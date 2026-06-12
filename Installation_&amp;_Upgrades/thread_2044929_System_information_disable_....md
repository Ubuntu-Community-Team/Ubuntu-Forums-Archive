---
title: "System information disable ..."
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by vs20 on 2012-08-20
Hello,
I currently install OS in VMware and i have the following error:
System information disable due to load higher than 2.0
My laptop is Core-i5 with 4GB Ram.
Please help me

---

### Post by Doug S on 2012-08-21
Hi, and welcome to Ubuntu forums.
 
It doesn't matter if the system information thing decides not to run.
However, if you want to force it to run have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2000524").
 
Hope this helps.

---

### Post by sandyd on 2012-08-21
Just a small explanation on why this is happening-

I bet thats a dual core core-i5 right?

You see, the system load represents the processor load.

I.E.
1 = 1cpu
2 = 2cpu

In this case, when the System Load rises above 2, it means that processes are being queued, sort of like in a car jam.

As a result, Landscape does not run, because it will just add to the queue :)

---

