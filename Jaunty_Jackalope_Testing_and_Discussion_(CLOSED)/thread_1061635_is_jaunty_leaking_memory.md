---
title: "is jaunty leaking memory?"
date: 2009-02-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by avb on 2009-02-06
guys, does somebody see this? My desktop using about 150mb on start, but in a day of work, it start to use around 250 with a basic desktop without any extra stuff loaded. Does somebody see this except me?

---

### Post by diebels on 2009-02-06
Disk cache?

---

### Post by OrangeCrate on 2009-02-06
> **avb said:**
> guys, does somebody see this? My desktop using about 150mb on start, but in a day of work, it start to use around 250 with a basic desktop without any extra stuff loaded. Does somebody see this except me?

+1 for disk cache...

**Linux Memory Management or 'Why is there no free RAM?'**

> Traditional Unix tools like 'top' often report a surprisingly small amount of free memory after a system has been running for a while. For instance, after about 3 hours of uptime, the machine I'm writing this on reports under 60 MB of free memory, even though I have 512 MB of RAM on the system. Where does it all go?

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

---

### Post by ronacc on 2009-02-06
@ AVB check your individual processes , on a freshly booted AMD64 desktop with compiz ,5 screenlets ,and gnome-do/dockey loaded and wireless connected I am showing 91 MB mem used . I'll add an edit in a couple of hours with mem used after that time .

---

### Post by W2IBC on 2009-02-06
> **diebels said:**
> Disk cache?

++1

when i boot up i start with 180MB (I booted at 11pm est) now at 8:40AM est i have 490MB ram. 

which is about normal for me.

---

### Post by Nullack on 2009-02-06
Im sure there is memory leaks in the code but I havent noticed anything particular about this dev cycle with it.

---

### Post by karlmp on 2009-02-06
use conky

```
sudo aptitude install conky
```

---

### Post by jp_coll2003 on 2009-02-06
Hi there. I am now using Jaunty and for the first time since using Ubuntu, I am now missing 100 mb. I have always had the full two gig when looking for at the system monitor, but now only have 1.9 gig in total. Is it just me ?????????

---

### Post by andrewabc on 2009-02-06
> **jp_coll2003 said:**
> Hi there. I am now using Jaunty and for the first time since using Ubuntu, I am now missing 100 mb. I have always had the full two gig when looking for at the system monitor, but now only have 1.9 gig in total. Is it just me ?????????

Probably the way ram is counted. conky is only reporting I have 2.94gb of ram even though I have 3gb.

It is possible you have shared video ram which is where the 100mb is missing (video card has 100mb allotted to it).

---

### Post by jp_coll2003 on 2009-02-07
No, I have an independent video card, and as I have said, I have never had this missing memory problem before.

---

### Post by diebels on 2009-02-07
You could try mem=2G,
see [http://lxr.linux.no/linux+v2.6.28/Documentation/kernel-parameters.txt#L1224](http://lxr.linux.no/linux+v2.6.28/Documentation/kernel-parameters.txt#L1224)

---

### Post by felix.rommel on 2009-02-08
> **jp_coll2003 said:**
> Hi there. I am now using Jaunty and for the first time since using Ubuntu, I am now missing 100 mb. I have always had the full two gig when looking for at the system monitor, but now only have 1.9 gig in total. Is it just me ?????????

Maybe in the last version system monitor used Giga Byte (GB) instead of Gibi Byte (GiB)!?

GB = 10^9 = 1000000000 Bytes
GiB based on 1024 basis = 1073741824 Bytes

KiB, MiB, GiB, ... are the new standardized units.

Appart from that I wanted to post the same question to this forum about a memory leak. Here after about 18 hours, Plasma uses about 540 MiB! And memory consumption is growing. I have an Intel card which grabs main memory. But the memory which the graphic card uses should be shown in Xorg memory consumption!?

I have no desktop effects enabled in KWin. So the memory which the graphic card uses can't be very high. I also have not that many Plasma objects running and as I said, the Plasma memory consumption grows by the time.

Does anybody else have this high memory usage of Plasma after a few hours?

---

### Post by W2IBC on 2009-02-08
idk im not see'in it. im using KDE and after uptime 24hrs my mem usages is still about 410MiB which is better then 8.10 w/ KDE after 24 would be 650MiB

---

### Post by karlmp on 2009-02-08
Gigabyte (GB) to Gibibyte (GiB) and Megabyte (MB) to Mibibyte (MiB) Converter:

[http://wintelguy.com/gb2gib.html](http://wintelguy.com/gb2gib.html)

---

### Post by taavikko on 2009-02-08
Haven't noticed anything particular...

FF is likely to hog some memory (~200Mb) in my system...
Rhythmbox also, ~11k songs and crossfading (~70Mb)

> uptime;free -m
 22:00:18 up 6 days,  4:18,  3 users,  load average: 0.16, 0.45, 0.61
             total       used       free     shared    buffers     cached
Mem:          1508       1214        293          0         24        877
-/+ buffers/cache:        312       1195
Swap:          964         34        929

ps -A |wc -l
119

Anyhow, runs faster than any Ms product ever will (on this machine)
> model name	: Intel(R) Pentium(R) M processor 1.86GHz


---

### Post by jp_coll2003 on 2009-02-12
> **felix.rommel said:**
> Maybe in the last version system monitor used Giga Byte (GB) instead of Gibi Byte (GiB)!?

GB = 10^9 = 1000000000 Bytes
GiB based on 1024 basis = 1073741824 Bytes

KiB, MiB, GiB, ... are the new standardized units.

Appart from that I wanted to post the same question to this forum about a memory leak. Here after about 18 hours, Plasma uses about 540 MiB! And memory consumption is growing. I have an Intel card which grabs main memory. But the memory which the graphic card uses should be shown in Xorg memory consumption!?

I have no desktop effects enabled in KWin. So the memory which the graphic card uses can't be very high. I also have not that many Plasma objects running and as I said, the Plasma memory consumption grows by the time.

Does anybody else have this high memory usage of Plasma after a few hours?

Many thanks for this post. Checked it out and yes it came up with 1.86 blah blah blah . Rounded up it would  come to 1.9 gb

---

### Post by W2IBC on 2009-02-12
> **felix.rommel said:**
> Maybe in the last version system monitor used Giga Byte (GB) instead of Gibi Byte (GiB)!?

GB = 10^9 = 1000000000 Bytes
GiB based on 1024 basis = 1073741824 Bytes

KiB, MiB, GiB, ... are the new standardized units.

Appart from that I wanted to post the same question to this forum about a memory leak. Here after about 18 hours, Plasma uses about 540 MiB! And memory consumption is growing. I have an Intel card which grabs main memory. But the memory which the graphic card uses should be shown in Xorg memory consumption!?

I have no desktop effects enabled in KWin. So the memory which the graphic card uses can't be very high. I also have not that many Plasma objects running and as I said, the Plasma memory consumption grows by the time.

Does anybody else have this high memory usage of Plasma after a few hours?

I'm using KDE system has been up 48hrs+ and my mem usage is only 380MiB
Plasma for me is only using 11MiB 

do you have alot of "widgets" running on yours?

---

### Post by felix.rommel on 2009-02-13
> **KD8HHO said:**
> I'm using KDE system has been up 48hrs+ and my mem usage is only 380MiB
Plasma for me is only using 11MiB 

do you have alot of "widgets" running on yours?

All in all I have about 16 Plasmoids running (Panel, systray, ...) included. After about 8 hours Plasma uses a lot less memory. Maybe some update fixed the memory problem. I will keep an eye on memory consumption until Jaunty will be released.

---

### Post by inportb on 2009-02-13
Wait -- what's wrong with using RAM? I mean, if your system only needs 512MB, why the heck do you need to waste money on 2GB? I hope you're not sad because your RAM is actually serving a purpose now rather than doing nothing. Let your RAM fill with cache, because that's its purpose.

---

### Post by Kow on 2009-02-14
As a previous user stated, an operating system should try and utilize as much of the resources available to it otherwise it's just a waste to spend money on more than a GB of memory. The Linux kernel's memory management is not stupid and will quickly reallocate the resources when you run a game, for instance. Finally to answer the question in the thread title: No, since jaunty is nothing more than a word for a collection of packages. Since you are a tester (why else would you be using jaunty?) you should be able to figure out on your own if a particular program is leaking memory. Then, you should be able to encapsulate it within.. let's say valgrind or gdb, and post a bug report with the useful information to developers. A memory "leak" is when the program that allocated the memory forgets that it exists and never frees it. Of course the memory will be automatically freed when the program is terminated.

---

### Post by aamukahvi on 2009-02-14
-

---

### Post by 4tro on 2009-03-05
to get back at the original post, I have noticed a leaking of memory as well.

during a days work my memory will fill up, mainly by xorg using loads of memory and slowing down to a halt when at 92% total memory usage.

Killing xorg fixes this issue temporarily, starting again with normal memory usage.

---

### Post by knarf on 2009-03-05
Install xrestop and have a look at what it is that makes Xorg grow...

---

### Post by 4tro on 2009-03-05
I'm having a look, for now compiz and emerald are on top, but I'll look when I'm at 92% memory usage...

---

