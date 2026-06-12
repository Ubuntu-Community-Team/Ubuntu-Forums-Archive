---
title: "Solid State Disk Karmic Support"
date: 2009-09-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2009-09-09
Wondering if SSD will be supported by default with karmic. Once SSD come with TRIM firmware, can I simply pop in SSD into computer, boot from livecd/usb, install karmic to SSD, and karmic will know the best alignment, and TRIM will automatically work? No custom configs needed for basic SSD trim/alignment support?

I'm pretty sure the kernel supports SSD (trim). Just wondering what work has to be done to get an SSD working with TRIM etc once TRIM firmware is released.

Indilinx should have TRIM firmware support by end of month.

With win7 release in October most SSD should have TRIM firmware, so I hope ubuntu (linux) makes the most of this new technology, and I don't have to wait for full SSD support in 10.04 (without having to manual config everything).

Anyone currently testing karmic with an SSD? How does it feel/speed and stability?
I'll be buying a SSD once the prices stabilize, they really jacked up the prices in past month or so.

EDIT:
Yah I know it is solid state **drive**, stupid forum not allowing me to edit topic title.

---

### Post by antiram on 2009-09-09
kernel has no completed trim support, but you can use wiper.sh from new hdparm
[http://sourceforge.net/projects/hdparm/](http://sourceforge.net/projects/hdparm/)
[http://www.ocztechnologyforum.com/forum/showthread.php?t=60882](http://www.ocztechnologyforum.com/forum/showthread.php?t=60882)

works with my supertalent ultradrive and 1711 firmware (which has bugs related to win7)

the cfq scheduler should have some optimizations for ssds, but on jaunty .28 kernel deadline looks faster for me with
echo deadline > /sys/block/sda/queue/scheduler
echo 1 > /sys/block/sda/queue/iosched/fifo_batch

the current trim patches need a rewrite
[http://thread.gmane.org/gmane.linux.ide/42526](http://thread.gmane.org/gmane.linux.ide/42526)

---

### Post by MacUntu on 2009-09-09
And what about aligning partitions like explained here [http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226](http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226)

---

### Post by bear24rw on 2009-09-09
> **antiram said:**
> kernel has no completed trim support, but you can use wiper.sh from new hdparm
[http://sourceforge.net/projects/hdparm/](http://sourceforge.net/projects/hdparm/)
[http://www.ocztechnologyforum.com/forum/showthread.php?t=60882](http://www.ocztechnologyforum.com/forum/showthread.php?t=60882)

works with my supertalent ultradrive and 1711 firmware (which has bugs related to win7)

the cfq scheduler should have some optimizations for ssds, but on jaunty .28 kernel deadline looks faster for me with
echo deadline > /sys/block/sda/queue/scheduler
echo 1 > /sys/block/sda/queue/iosched/fifo_batch

the current trim patches need a rewrite
[http://thread.gmane.org/gmane.linux.ide/42526](http://thread.gmane.org/gmane.linux.ide/42526)

is deadline better then noop?

---

### Post by antiram on 2009-09-09
dont know what the karmic installer does, but you can use gparted and uncheck the checkbox for "aligned to cylinder boundaries" and make a 1MB alignment (which is also a 512k, 256k, 128k, 64k alignment), or use fdisk with "fdisk -u" to use sectors as unit. 1024k = 2048 sectors

the feeling with deadline is better for me, because it prefers reads and this results in faster program starts

---

### Post by andrewabc on 2009-09-09
So, from what I gather from posts in this thread, is that default install will not fully support (without configs) trim/alignment?

Is it easy to simply install the hdparm, and all you have to do whenever you think of it (or scheduler should auto run program), would act like a TRIM command for entire drive (like most wiper tools)?

And alignment you have to manually do before running ubuntu installer? It won't auto detect best alignment for the SSD?

EDIT:
I don't know much about technical stuff in linux, but I've been following SSD news and ocz forums for several months now, waiting to buy an SSD and want to make sure ubuntu 9.10 works well with it before buying anything as prices should drop.

---

### Post by josephellengar on 2009-09-27
So is that the final say?  That Koala will not support trim out of the box?  How would one go about enabling it?  And what is this alignment thing that everybody is discussing?

---

### Post by josephellengar on 2009-09-27
That is, if I have a ssd in my system, will I have to do anything to get it to trim?

---

### Post by artir on 2009-09-27
deadline is the new default scheduler/elevator for karmic, Was changed a few days ago

---

### Post by andrewabc on 2009-09-27
> **artir said:**
> deadline is the new default scheduler/elevator for karmic, Was changed a few days ago

I don't understand what that means. There is no "deadline' packages in karmic.

So will there be TRIM by default (once TRIM firmware is put on SSD)?
Do I have to align? What is default alignment (and is it worth aligning to 1024)?

I just purchased 60gb vertex, and would like some good answers. Quite frankly I don't understand most of what was said in this thread, and I've been testing ubuntu since 2006, and have been following SSD stuff since April.

Vista/win7 aligns itself, so will Ubuntu? TRIM will work by default with SSD trim frimware on win7, will ubuntu?

---

### Post by josephellengar on 2009-09-27
> **andrewabc said:**
> I don't understand what that means. There is no "deadline' packages in karmic.

So will there be TRIM by default (once TRIM firmware is put on SSD)?
Do I have to align? What is default alignment (and is it worth aligning to 1024)?

I just purchased 60gb vertex, and would like some good answers. Quite frankly I don't understand most of what was said in this thread, and I've been testing ubuntu since 2006, and have been following SSD stuff since April.

Vista/win7 aligns itself, so will Ubuntu? TRIM will work by default with SSD trim frimware on win7, will ubuntu?

Yeah those are the questions that I want answered too, before I splurge on the gen2 80gb intel drive that's in my amazon cart right now.  Of course it's still faster, even when not aligned or trimmed, but still ...

Oh, and I don't exactly get what alignment means in this context, if somebody could explain.

---

### Post by andrewabc on 2009-09-27
Alignment is complicated. I don't even know that well.

Basically a SSD will write to a certain block size, and you'd want the alignment to be the same size (or in same multiples), so that it does it faster or more efficiently (less writes).

I think hard drives have different block sizes than SSD, and thus would benefit from having different alignment than what is used on hard drives when installing OS.

That is why you always hear people having to align winxp with SSD, as winxp is so old and doesn't care about SSD. So You'd have the OS format and align differently than the SSD should be aligned to.

---

### Post by josephellengar on 2009-09-27
> **andrewabc said:**
> Alignment is complicated. I don't even know that well.

Basically a SSD will write to a certain block size, and you'd want the alignment to be the same size (or in same multiples), so that it does it faster or more efficiently (less writes).

I think SSD have different block sizes than SSD, adn thus would benefit from having different alignment than what is used on hard drives when installing OS.

That is why you always hear people having to align winxp with SSD, as winxp is so old and doesn't care about SSD.

Yeah, I read a few blogs and got that and it doesn't seem to matter much in terms of speed on the new intel drives, but what about trim()?  Are we getting automatic support on karmic or should I not bother buying an SSD?

---

### Post by Ruhani04 on 2009-09-28
Trim is probably not going to be available for a while.
In my opinion we have no agreed standard for different OS. Vertex firmware 1.3 supports their own in house Trim which, however, is not supported by any other OS. They are right now working with M$ to support Trim for Windows 7. 
I haven't heard or seen anywhere that Trim will be supported in the near future to work right "out of the box." 
The technology is too new and too many parties are involved to come up with a quick solution.
Hopefully things will be different in a few months.
I have been using a Vertex SSD for several months now and I must say I am very happy with the performance without Trim if you got the right setup.

---

### Post by nhasian on 2009-09-28
It is my understanding that ATA-TRIM will **not** be available with the windows7 launch, and the function will be added some time later.  

> **andrewabc said:**
> TRIM will work by default with SSD trim frimware on win7, will ubuntu?

---

### Post by MacUntu on 2009-09-28
> **nhasian said:**
> It is my understanding that ATA-TRIM will **not** be available with the windows7 launch, and the function will be added some time later.

[http://www.ocztechnologyforum.com/forum/showthread.php?t=56351](http://www.ocztechnologyforum.com/forum/showthread.php?t=56351)

---

### Post by pressureman on 2009-09-28
> **andrewabc said:**
> Basically a SSD will write to a certain block size, and you'd want the alignment to be the same size (or in same multiples), so that it does it faster or more efficiently (less writes).

I think hard drives have different block sizes than SSD, and thus would benefit from having different alignment than what is used on hard drives when installing OS.

That is why you always hear people having to align winxp with SSD, as winxp is so old and doesn't care about SSD. So You'd have the OS format and align differently than the SSD should be aligned to.

Windows Vista and 7 use megabyte-aligned partitions by default, rather than the old cylinder-aligned partitions used in the past. With existing hard drives that use 512-byte sectors, a megabyte (1048576 bytes) is exactly 2048 sectors. Newer hard drives (and SSDs) will start to use 4KB sectors, which also evenly divide into 1MB (4096 x 256). This is one of the main reasons behind the move to megabyte-aligned partitions - so that they will be future-proof when all hard drives use 4KB sectors.

SSDs typically have a 512KB erase-block size, so this also means that partitions will align neatly on an erase-block boundary.

---

### Post by andrewabc on 2009-09-30
I found this
[https://wiki.ubuntu.com/KernelTeam/Specs/KarmicSSD](https://wiki.ubuntu.com/KernelTeam/Specs/KarmicSSD)
Hasn't been updated since August 11. So looks like they don't care.

Anyone know of SSD benchmark utilities for ubuntu? Windows has lots, but I don't plan on installing windows to SSD.
I want to know read/write speeds. Something like crystaldisk would be fine.

---

### Post by MacUntu on 2009-09-30
Maybe not as easy as those one-button-apps for Windows: [http://www.iometer.org/doc/downloads.html](http://www.iometer.org/doc/downloads.html)

---

### Post by andrewabc on 2009-09-30
Any easy to install .deb? I downloaded iometer-2008-06-22-rc2.src.tgz of iometer and "install readme" says can only be installed onto windows...
I don't want to learn to compile etc. I've spent a dozen hours compiling just to try to get my scanner to work.

---

### Post by Ruhani04 on 2009-09-30
Here is a link from the OCZ forum for Linux support with some benchmarking with hdparm:
[http://www.ocztechnologyforum.com/forum/showthread.php?t=54379](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379)

Hope that helps. It worked for me.;)

---

