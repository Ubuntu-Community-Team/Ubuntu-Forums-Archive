---
title: "Lucid Lynx Beta 2 Memory Consumption."
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ubiquitousblake on 2010-04-12
Hi all! I'm just now running 10.04 Beta 2 (32 bit) on an old machine I've had around my house and I've become quite scared at its memory use! Right from start-up, the machine is using roughly 300 MB of RAM! Now this is still FAR less than Windows, but my 9.10 machine uses around 170-190 MB of RAM from start-up! Mind, I'm running compiz, the latest proprietary drivers for my NVIDIA graphics card and my wireless card. Surely there is a way to streamline this version to its previous level of consumption of resources without sacrificing an arm or a leg. 

On the 10.04 machine, I'm running nothing other than the default start-up items. Also, I have no drivers, other than what is installed by default, installed on this machine- so no graphics acceleration; no desktop effects. 

I really love Ubuntu and what it represents. It has held my devotion for quite some time now. However, my OCD is really nagging me on this one. It's not that the RAM use is anything atrocious, it's just a large spike from where I had previously become comfortable within this system environment. Any suggestions? Also, if you wouldn't mind answering me what your RAM usage averages about to (if you're running the 32 or the 64 bit version =P). 

I really appreciate your time in reading this, and hopefully responding!

---

### Post by psyke83 on 2010-04-13
> **ubiquitousblake said:**
> Hi all! I'm just now running 10.04 Beta 2 (32 bit) on an old machine I've had around my house and I've become quite scared at its memory use! Right from start-up, the machine is using roughly 300 MB of RAM! Now this is still FAR less than Windows, but my 9.10 machine uses around 170-190 MB of RAM from start-up! Mind, I'm running compiz, the latest proprietary drivers for my NVIDIA graphics card and my wireless card. Surely there is a way to streamline this version to its previous level of consumption of resources without sacrificing an arm or a leg. 

On the 10.04 machine, I'm running nothing other than the default start-up items. Also, I have no drivers, other than what is installed by default, installed on this machine- so no graphics acceleration; no desktop effects. 

I really love Ubuntu and what it represents. It has held my devotion for quite some time now. However, my OCD is really nagging me on this one. It's not that the RAM use is anything atrocious, it's just a large spike from where I had previously become comfortable within this system environment. Any suggestions? Also, if you wouldn't mind answering me what your RAM usage averages about to (if you're running the 32 or the 64 bit version =P). 

I really appreciate your time in reading this, and hopefully responding!

How are you measuring memory usage? Keep in mind that most utilities/applications also count the buffer/cache usage, so you may be misinterpreting the information. Under ideal circumstances, your memory should always be 100% in use (if the cached data is not useful, the process of de-allocating it from memory is, for all intents and purposes, instantaneous, so there is no disadvantage).

---

### Post by Lollerke on 2010-04-13
+1, Sometimes right after the boot up the System Monitor shows 400MB usage,but the normal is ~200MB.

"How are you measuring memory usage?"

It's not important,because I think everybody used the same program in other Ubuntu versions to measure this. (I use the System Monitor).

---

### Post by psyke83 on 2010-04-13
> **Lollerke said:**
> +1, Sometimes right after the boot up the System Monitor shows 400MB usage,but the normal is ~200MB.

"How are you measuring memory usage?"

It's not important,because I think everybody used the same program in other Ubuntu versions to measure this. (I use the System Monitor).

I use "free" and "top"...

Maybe in your case, your system really is using 400mb of RAM. I think it's quite possible that the act of launching System Monitor itself can increase your actual memory usage from 200mb to 400mb. I also enjoy using System Monitor to monitor my CPU usage, whilst simultaneously looking at all  of the fancy (and CPU-intensive) cairo-drawn widgets on its interface... ;)

---

### Post by Longinus00 on 2010-04-13
There's a bug in ureadahead where it won't free memory used for the tracing buffer which leads to very high memory consumption. Check to see if that's what's affecting you.

[http://ubuntuforums.org/showpost.php?p=9012493&postcount=55](http://ubuntuforums.org/showpost.php?p=9012493&postcount=55)
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

---

### Post by Lollerke on 2010-04-13
"I think it's quite possible that the act of launching System Monitor itself can increase your actual memory usage from 200mb to 400mb."

I don't think so. In Karmic I used System Monitor too and the memory usage was always ~200MB.

---

### Post by psyke83 on 2010-04-13
> **Lollerke said:**
> "I think it's quite possible that the act of launching System Monitor itself can increase your actual memory usage from 200mb to 400mb."

I don't think so. In Karmic I used System Monitor too and the memory usage was always ~200MB.

I was only kidding. I'm not fan of System Monitor :). 

Anyway, as mentioned already, you could be seeing the [ureadahead bug #501715]("https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715").

---

### Post by forcecore on 2010-04-13
> **Lollerke said:**
> "I think it's quite possible that the act of launching System Monitor itself can increase your actual memory usage from 200mb to 400mb."

I don't think so. In Karmic I used System Monitor too and the memory usage was always ~200MB.

it was joke right? even windows task manager takes only 2-4 mb.

---

### Post by ubiquitousblake on 2010-04-13
Thanks for the replies! 

I haven't checked the bug report yet, but I plan to look immediately. I use system monitor, but even that uses little RAM. My Karmic machine is really conservative. Something that really turned me to Linux. Yet, again, I haven't checked out this bug report! I really appreciate everyone's time who replied or even just read this post! I'll get back after I read through the ureadahead report. :P

---

### Post by ranch hand on 2010-04-13
I get a spike a little bit after the desktop is working but it only lasts about 25 seconds.  Haven't really looked into it.

Just wrote it off as a side effect of being in development.

May well be that I better be checking that bug too.

---

### Post by grandtoubab on 2010-04-13
hello,
what about 
Applications -> system tool -> htop

---

