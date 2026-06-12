---
title: "Jaunty realtime kernel dual-core support"
date: 2009-03-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by seanlano on 2009-03-08
I am using Intrepid (Ubuntu regular), but recently attempted a semi-migration to Studio. I installed some of the ubuntustudio-* packages, as well as the latest linux realtime kernel, and all works fairly well. 

However, the problem is that the realtime kernel does not support dual-core processors. I have also read this is a universal problem for many people on other sites/blogs/forums about Ubuntu Studio. 


I was wondering, is there going to be support for dual-core processors in the realtime kernel that will be in the Jaunty repos? 

Thanks.

---

### Post by Cresho on 2009-03-08
You can install it in synaptic but I ran into the same problem.

[http://ubuntuforums.org/showthread.php?p=6861736#post6861736](http://ubuntuforums.org/showthread.php?p=6861736#post6861736)

This is'nt something that is just going to get passed on by.  I can run my games fine in hardy heron.  The jaunty jackelope is in alpha stages and is being worked on and hope its finalized in the release date.

---

### Post by seanlano on 2009-03-08
yeah, i've got it working too, but with only a single 1.66Ghz core, which introduces a lot of lag and latency with audio applications. 

Hopefully the realtime kernel is fixed for Jaunty.

---

### Post by Stochastic on 2009-03-09
There has been some discussion about the Jaunty Realtime Kernel on the UbuntuStudio users mailing list.  Here are some threads:

[https://lists.ubuntu.com/archives/ubuntu-studio-users/2009-March/004217.html](https://lists.ubuntu.com/archives/ubuntu-studio-users/2009-March/004217.html)

[https://lists.ubuntu.com/archives/ubuntu-studio-users/2009-March/004244.html](https://lists.ubuntu.com/archives/ubuntu-studio-users/2009-March/004244.html)

I'll give it a test pretty soon, and post back with results.  So far, the vanilla jaunty kernel has been pretty stable for my audio needs (the odd xrun here and there).

Intrepid's RT kernel is full of known bugs but due to the lack of development time (there was a kernel switch late in the Intrepid development cycle).

---

### Post by gnomeuser on 2009-03-09
There is luckily now a renewed effort upstream to work on RT, and the next bits of work might go in soon. So hopefully soon we will have the rt capabilities in the "proper" kernel.

[http://lwn.net/Articles/319544/](http://lwn.net/Articles/319544/)

---

### Post by Starks on 2009-03-09
Can someone explain to me in simple terms what the realtime kernel is?

---

### Post by kayosiii on 2009-03-09
The RT kernel is a modified version of the linux kernel that trades some performance for the ability to make sure that a high priority task can be completed before a deadline. This is useful to guarantee that you won't loose any information when recording audio due to some other process in the kernel taking too much time to do what it needs to.

Recently (around 2.6.25) a feature that the realtime kernel relies very heavily on was removed from the kernel. So there hasn't really been a good rt kernel since then.

---

### Post by cariboo on 2009-03-09
Here's a link for you.

[RtWiki]("http://rt.wiki.kernel.org/index.php/Main_Page")

Jim

---

### Post by gnomeuser on 2009-03-10
> **Starks said:**
> Can someone explain to me in simple terms what the realtime kernel is?

The wikipedia entry is quite good:
[http://en.wikipedia.org/wiki/Real-time_computing](http://en.wikipedia.org/wiki/Real-time_computing)

---

### Post by seanlano on 2009-03-17
so, is there dual-core support in Jaunty or not? I'm downloading the 64-bit alpha-6 live cd now, so in a few days I can find out when I install it, but is it supposed to be included?

---

