---
title: "Ubuntu CPU usage for processes"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by redlinethecar on 2009-12-11
Hello all and first let me say thank you very much, this forum has answered so many questions about ubuntu and linux in general and has given me great understanding in it.  Linux has definelty let me take control of my computer (unlike other OS's won't mention any names).  Anyway I wanted to post in ubuntu 64 bit because thats what im running but it appears I can't post new threads there for some reason so my apologies for posting in a wrong section if I am.  I am trying to find software that will let me control how a process (a script) uses my CPU's.  There is software called CPULIMIT that manages the usage but it appears to only work with one processor and only limit not extend.  For example, if I would like a process to use 100% of CPU0 and 50% of CPU1.  Or, is this an automatic value that has been written in software and cannot be changed.  Thank you for all your help and support.

---

### Post by doas777 on 2009-12-11
well, for the most part processors process as fast as they can for any given task. when you see a task running for minutes and cpu usage is only 50%, then likely the rest of the time is waiting for IO operations to complete. 

upper layer programms (and langagues) have little control over what the CPU is actually doing, only the way they address it, for instance via multi-threading or parallel processing.

usually if an app only wants to consume limited CPU resources, the easiest way to do it is to pause teh thread for a proportion of the time. if you want 50%, pause your thread every other second for  second (you can probably slice it finer than that).

---

### Post by redlinethecar on 2009-12-11
Thanks a lot for the input.  Makes since, just hate waiting lol

---

### Post by doas777 on 2009-12-11
after rereading your post, perhaps we should touch on threads, synchronicity, and asynchronisity.

a CPU can only do one thing at one time. when a cpu has multiple processes running, it very quickly switches between tasks, so it seems like it's doing more than one thing at a time, but really it isn't. this is called synchronous processing, because we have to wait our turn, and I can't begin until you end. Any time a process is using the CPU, it is running a "thread". a thread is the smallest unit of execution a program can do. the general rule is that only one thread can execute on one cpu core at a time. the other threads all have to wait their turn. this means that any program that uses a single execution thread, can only run on one CPU/core.

many modern programs are written asynchronously, using more than one thread. these programs can use multiple CPUs/cores, each running a different thread. many programmers for instance perform IO on one thread, and processing on another. this way, the processing thread does not have to wait on the hard disks to provide data for the IO thread (unless the process consumes the IO).

parallel processing involves breaking a task up over multiple processes, which themselves may have many threads.

as it stands today, there are still many tasks that can only utilize one processor core because of their threading model, so you will be limited in the means you have to improve their performance. with single thread apps, all you can do is get a processor with a higher frequency.

---

### Post by redlinethecar on 2009-12-15
Thanks a lot, Im always amazed to see how much knowledge i don't have, LOL.  Thanks youv'e helped a lot.  I ended up finding a not to well known software that does the same process i needed but actually uses both cores at 100%.  The problem was, the install was a serious pain!!  But everything is up and going thanks a lot.

---

