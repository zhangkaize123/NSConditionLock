# NSConditionLock
NSConditionLock使用条件
NSConditionLock: 
条件锁，一个线程获得了锁，其它线程等待。

[xxxx lock]; 
表示 xxx 期待获得锁，如果没有其他线程获得锁（不需要判断内部的condition) 那它能执行此行以下代码，如果已经有其他线程获得锁（可能是条件锁，或者无条件锁），则等待，直至其他线程解锁

[xxx lockWhenCondition:A条件]; 
表示如果没有其他线程获得该锁，但是该锁内部的condition不等于A条件，它依然不能获得锁，仍然等待。如果内部的condition等于A条件，并且没有其他线程获得该锁，则进入代码区，同时设置它获得该锁，其他任何线程都将等待它代码的完成，直至它解锁。

[xxx unlockWithCondition:A条件]; 
表示释放锁，同时把内部的condition设置为A条件 ----------------> 这个需要注意
