---
title: "How to optimize file transfer in 14.04 lts - too slow copy SATA disk"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by HP001 on 2014-08-23
Hi all,
Another challenge I got after upgrade from 12.04 lts to 14.04 lts is disk performance.

I have ssd and western digital RE/enterprise 4T. 
Normally, file copy in 12.04 just took seconds; there was no concern. The speed is about 30-100Mbytes/s. The speed to/from usb3 external disks is about 45Mbytes/s

Now with the new 14.04 lts, the copy process takes hours.
I am appreciate alot if you can re-directly to threads that can tuned up the performance a bit.

Thank you.

---

### Post by TheFu on 2014-08-23
I'd perform some different tests with hdparm settings. There are many web articles on these settings.  Also, turning down the swappiness may be helpful - but doing so without understanding could turn out worse for system performance.

Before you start, use a real disk performance tool to gather the "before" data. Otherwise, you'll never know how much "better" the after is or is not.

"linux disk performance" search.

[http://www.robthomson.me.uk/2011/03/30/tuning-kvm-guests-you-need-to-do-it/](http://www.robthomson.me.uk/2011/03/30/tuning-kvm-guests-you-need-to-do-it/) is what I used to solve my issue.

Whenever disk performance becomes an issue, I always check cable connections first, then swap cables if that didn't help.  Sometime it really is the the dumbest thing. ;)

If there is virtualization - that is a different performance issue.
If there is RAID involved - that is a different issue too.

I'd re-tune every major kernel update or if things just seem slow. Disk scheduling seems to be something that has changed the last 4 yrs.

---

### Post by HP001 on 2014-08-23
Thank you TheFu, I'm going to look into it.

My current hdparm -Tt is:
 >Timing cached reads:   23946 MB in  1.99 seconds = 12031.80 MB/sec
>Timing buffered disk reads: 500 MB in  3.00 seconds = 166.65 MB/sec
which is not any close to what I experienced.
I'm not using RAID, and the just direct server access, not through virtualbox.

Is there a tuning section on ubuntu forum?

---

### Post by TheFu on 2014-08-24
Did you follow the provided link and do what it suggested?

---

### Post by HP001 on 2014-08-24
No, not yet.
I have one SSD for OS and all (read-only) files that are important to have speed like virtualbox VM.
My WD RE disk contains documents in shares folders that are accessible from different users and different VM.
Looks like the transfer speed is going up/down randomely. On the WD disk, it had been formated as ext4, and copying large files within the drive.

I am still looking for a 'complete' guide to optimizing ubuntu. 
I am trying to solve USB disk issues now, then video boot to black screen first. I'll let you know how.

---

### Post by TheFu on 2014-08-25
To my knowledge, that document does not exist.  Why not?

Every kernel changes how different parts of the kernel behave, how different schedulers can be optimized for different needs.  Imagine you were trying to maintain that level of documentation ... for free.  OTOH, all the source code is there for your review and people working on the kernel tend to think all the documentation necessary is already in the code.  kernel.org

Optimization for different sorts of hardware requires many different complementary settings. Only you care about optimizing under your specific hardware. There can be vast differences in what needs to be set for different chips.

The most likely tuning documentation will be for very specific, high-value, servers from the major vendors. This documentation will be provided with the support contract - perhaps by an on-site engineer from the vendor who sits inside your company. I've seen this from IBM, EMC, Dell, HP, Cisco engineers.  This is not something a home or small business user would be able to access normally. OTOH, the servers where I've seen the tuning documents were $25K+ each.

The most useful tuning that I've come across was in blog articles by engineers working on specific projects who happen to dive deep into tuning of 1 part of a system. Those articles are not generally for Ubuntu - rather, they are for Linux or Debian or RHEL and we have to perform our own testing around what their article states.

If you find an all-in-one document, please post it.

I'm trying to be realistic, not pessimistic, above. It is only what I've seen, so may not be 100% accurate.
A few search ideas: 
* ubuntu tuning sata
* ubuntu tuning hdd
* ubuntu tuning network
* ubuntu tuning nfs
* ubuntu tuning {insert your desired subsystem}

I'd try linux vs ubuntu and tune vs tuning too.  Hopefully, the author will say which kernel used.  2.6 versions may not reflect the best settings for a 3.2 or 3.11 or 3.13 kernel tree.

Don't forget that evey distro maker builds their own kernels with slightly different settings. Some will enable many security-related option which tend to slow down performance. Trade-offs.

Sorry for babbling so long here. Good luck finding what you seek.

---

### Post by brian_milnes on 2015-07-09
I'm currently getting 18MBs and my 2.7Tb file copy is gonna take till the weekend at this rate. <sigh>

And just so that you know, I got 137MB/s with the same drives on a Windows Server, so I know the drives CAN work at 7 times the speed.

So, what gives?

---

### Post by ubfan1 on 2015-07-09
I've been checking out slow USB3 copies of 50G files, seeing 10MB/sec. using cp or tar.  I did improve things with a tar blocking factor of two million (-b 200000 ) up to around 30MB/sec.  my hdparm test was 107 MB/sec.

---

### Post by TheFu on 2015-07-09
[http://www.urbandictionary.com/define.php?term=necroposting](http://www.urbandictionary.com/define.php?term=necroposting)
Best to start a new thread.

---

