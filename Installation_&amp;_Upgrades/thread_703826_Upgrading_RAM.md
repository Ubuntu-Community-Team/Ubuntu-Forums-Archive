---
title: "Upgrading RAM"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by jsnelli2 on 2008-02-21
I have read posts that Ubuntu never really needs more than 1 GB of RAM, which is what I currently have installed in my laptop (1.6 ghz centrino).  I was thinking about buying a couple sticks of 1 GB to move up to 2 GB.  Would I notice a major difference in speed?  Or would it be negligible?  I was wondering if it would have much of an effect on Compiz or anything like that?  I've noticed that sometimes my computer is rather slow and jumpy with videos at times.

Thanks

---

### Post by Rocket2DMn on 2008-02-21
It probably won't have any effect.  You can view your memory usage by running
```
free -m
```
If you're not using anywhere close to 1GB, esp. with lots of stuff running, you don't need more RAM.  Spend the money on something else :)

---

### Post by jsnelli2 on 2008-02-21
total       used       free     shared    buffers     cached
Mem:          1011        942         68          0        189        351
-/+ buffers/cache:        401        609
Swap:         2957         32       2924

That's the output. So I've only got 68 mb free?

---

### Post by Rocket2DMn on 2008-02-21
That seems like a lot, what are you running that is taking so much memory?
You can also check under the Resources tab of 
```
gnome-system-monitor
```

---

### Post by xeth_delta on 2008-02-21
> **jsnelli2 said:**
> total       used       free     shared    buffers     cached
Mem:          1011        942         68          0        189        351
-/+ buffers/cache:        401        609
Swap:         2957         32       2924

That's the output. So I've only got 68 mb free?

If I am not mistaken, from the used memory 401MB are used for cache/buffers, so that memory can be freed when programs need it.
If you use multiple  programs that will take more than th 1GB your laptop has, you will see an increase of speed, due to swap avoidance, otherwise, I wouldn't be so sure.

---

### Post by Pumalite on 2008-02-21
Ubuntu will take as much memory as you give it. Memory is to be used. Increase to 2 GB is the best way to spend your money in your laptop.

---

### Post by jsnelli2 on 2008-02-21
When I copied that I had Rhythmbox, Evolution, and Firefox (w/ 2 tabs) opened.  That's it.  Music not playing.  Compiz disabled.

So the memory that is used for cache/buffers is pretty much like its not being used since it will be freed when programs need it?

---

### Post by jsnelli2 on 2008-02-21
Gnome-system-monitor states 407 mb used

---

### Post by Rocket2DMn on 2008-02-21
> **jsnelli2 said:**
> Gnome-system-monitor states 407 mb used

I think you're OK on RAM, you will REALLY notice it if you ever don't have enough.

---

### Post by jsnelli2 on 2008-02-21
Ok thanks for all the responses!

---

### Post by xeth_delta on 2008-02-22
> **jsnelli2 said:**
> When I copied that I had Rhythmbox, Evolution, and Firefox (w/ 2 tabs) opened.  That's it.  Music not playing.  Compiz disabled.

So the memory that is used for cache/buffers is pretty much like its not being used since it will be freed when programs need it?

It is being used by the system in order to be more responsive, but as I said, that memory will be freed if needed by programs.
I agree with Pumalite, memory is a good way to spend money on your computer.

---

### Post by jsnelli2 on 2008-02-23
So with my current usage you think there will be a noticeable difference?

---

### Post by Pumalite on 2008-02-23
There is always a difference when you increase your RAM, especially if you process large files.

---

### Post by kvdbreem on 2008-02-23
I agree.  I recently upgraded from 1G to 3 G on my Dell Dimension 8400.  Running Compiz, VMWare for work.  At first it didn't look like the system was taking more than a gig, but it certainly wasn't thrashing quite as much.  Then I started up a bunch of games and other programs and sure enough the system started digging into the two new gigs of mem, and I was up to around 1.6G.  

My only question is why some swapspace was being used.  Was it just because the scheduler had a few pages of memory that it didn't think were used often enough by programs it had running and so it stuffed them away to the swapspace instead?

I noticed that my load average went very high when I tried running two virtual machines at the same time, one Windoze XP and the other Ubuntu, set to use 1G and 512M of memory respectively.

---

### Post by jsnelli2 on 2008-02-25
Well that is good to hear.  My computer is quite a bit laggier than it used to be.  I had to shut Compiz off, because it was so jumpy when playing videos.  It stills lags a little now, although I'm not sure why.  I think it may be the video drivers that I am running.  Before reformatting I had the video set up very nicely.  If only I could get it back to the way it was....

There is nothing else besides video drivers that would lag down video playback is there?

---

### Post by xeth_delta on 2008-02-25
> **jsnelli2 said:**
> Well that is good to hear.  My computer is quite a bit laggier than it used to be.  I had to shut Compiz off, because it was so jumpy when playing videos.  It stills lags a little now, although I'm not sure why.  I think it may be the video drivers that I am running.  Before reformatting I had the video set up very nicely.  If only I could get it back to the way it was....

There is nothing else besides video drivers that would lag down video playback is there?

Open a terminal and run "top". Then play a video and check the information top offers. Is there anything using too much processing power? What video card do you have and what video drivers are you using?

---

### Post by jsnelli2 on 2008-02-27
Streaming a divx file firefox is using 80 perecnt of system resources.  I have an ATI Radeon 300x.  I had ATI's 8.452.1-1 drivers installed and Compiz was running smoothly, but common tasks like scrolling in firefox would make xgl take nearly 100 percent of system resources and lag the system down unbearably.  So I reverted back to MESA drivers.

---

### Post by jsnelli2 on 2008-02-27
I forgot to mention...I read that the system resources jumping to 100 percent was some sort of a bug.

---

