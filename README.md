# ArrayQueue
namespace ArrayQueue
{
    internal class ArrayQueue
    {
       int[] qArray;
         int qFront;
         int qRear;
         int qMax;
        int qCount;
        public int[] QArray { get => qArray;set=>qArray = value; }
        public int QFront { get => qFront; set => qFront = value; }
        public int QRear {  get => qRear; set => qRear = value; }
        public int QMax { get => qMax; set => qMax = value; }
        public int QCount { get => QCount; set => QCount = value; }
        public ArrayQueue(int max=0) {
        
        qArray=new int[max];
            qFront=0;
            qRear=-1;
            qMax=max;
            qCount=0;
                } 
        public bool IsEmpty =>qCount==0;
        public bool IsFull=>qCount==qMax;
        public bool Enqueue() {
            if (IsFull) return false;
            qRear++;
            if (qRear % qMax == 0) qRear = 0;
            qCount++;
            return true;
              
        }
        public bool Dequeue(out int outItem) { 
            outItem = 0;
        if(IsEmpty) return false;
            outItem = qArray[qFront];
            qFront++;
            if(qFront % qMax == 0) qFront = 0;
            qCount--;
            return true;
        }
        public bool Top(out int outItem)
        {
            outItem = 0;
            if(IsEmpty) return false;
            outItem = qArray[qFront];
            return true;
        }
        public void Input(ArrayQueue arrayqueue)
        {

            while (true)
            {
                Console.WriteLine("Nhap Gia Tri cua queue,neu la so am thi dung");
                int x = int.Parse(Console.ReadLine());
                if (x < 0)
                    break;
                if (arrayqueue.Enqueue()) break;
            }
        }
        public void Output(ArrayQueue arrayQueue)
        {
            while (!arrayQueue.IsEmpty)
            {
                int x;
                arrayQueue.Dequeue(out x);
                Console.WriteLine($"{x,4}");
            }
        }

    }
}
