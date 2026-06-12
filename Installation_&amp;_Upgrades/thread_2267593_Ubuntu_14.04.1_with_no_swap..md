---
title: "Ubuntu 14.04.1 with no swap."
date: 2015-03-02
forum: Installation &amp; Upgrades
---

### Post by stchman on 2015-03-02
Hello all.

I have two machines running Ubuntu 14.04.1 and have disabled swap on both.

Machine #1: Core i7 3770, 32GB RAM, 256GB SSD.
Machine #2: AMD FX-6300, 8GB RAM, 250GB SSD.

Machine #1 is a dual boot of Windows 7 Ultimate and Ubuntu 14.04.1 and machine #2 is Windows 7 Home Premium and Ubuntu 14.04.1.

On both machines after install I turned off swap and then removed the swap partition using GParted.  I have done this kind of thing since Ubuntu 12.04 as with no swap, there is no chance of the OS doing any writing to the SSD unintentionally.  Since both machines have plenty of RAM and I don't hibernate, I found no need for swap.

Any thoughts?

---

### Post by kerry_s on 2015-03-02
should work just fine, with that much ram.

---

### Post by stchman on 2015-03-02
> **kerry_s said:**
> should work just fine, with that much ram.

Agreed, when I go to the System Monitor in Ubuntu, I am using about 1GB of RAM on each machine which is well short of the available RAM.

---

### Post by kerry_s on 2015-03-02
yeah, i only got 2gb & i've never gone over 1 gig. i watch a lot of videos & movies, even now i got netflix running all day & ram is 783mb, no swap(4gb) is being used, i don't tweak my swap so it's all system managed.

---

### Post by pfeiffep on 2015-03-02
Should be fine if you don't do video editing or huge data base work or ....

---

### Post by sammiev on 2015-03-02
Even with using VM I never get over 1.5 GB and that is running everything hard and to the max without a swap. I do have my VM set to use 4 GB on my SSD.

---

### Post by tgalati4 on 2015-03-02
A small swap partition (like a couple of hundred megabytes) is helpful to keep the kernel from dumping processes when you do run out of memory.  Although with 32 GB, that would be rare, unless you are running a bunch of virtual machines.  Even the raspberrypi running off of an SD card has a 100 MB swap file.  It's doubtful that you will wear out an SSD with a small swap file that is only written to once in a while.

If you want to save power, then you might consider hibernate since reading the swap/hibernate file from SSD is reasonably quick and keeping 32 GB of RAM powered all the time (during sleep) will run up your power bill.  Use a Kill-a-Watt meter to measure the power difference between sleep and hibernate.  If you are burning 20 watts during sleep, then you might consider a swap file large enough to hold the RAM for hibernate.

---

### Post by justin-avril on 2015-03-03
> **tgalati4 said:**
> A small swap partition (like a couple of hundred megabytes) is helpful to keep the kernel from dumping processes when you do run out of memory.  Although with 32 GB, that would be rare, unless you are running a bunch of virtual machines.  Even the raspberrypi running off of an SD card has a 100 MB swap file.  It's doubtful that you will wear out an SSD with a small swap file that is only written to once in a while.

If you want to save power, then you might consider hibernate since reading the swap/hibernate file from SSD is reasonably quick and keeping 32 GB of RAM powered all the time (during sleep) will run up your power bill.  Use a Kill-a-Watt meter to measure the power difference between sleep and hibernate.  If you are burning 20 watts during sleep, then you might consider a swap file large enough to hold the RAM for hibernate.

Power-saving is a good reason to keep the swap partition.

---

### Post by mattharris4 on 2015-03-03
> **kerry_s said:**
> yeah, i only got 2gb & i've never gone over 1 gig. i watch a lot of videos & movies, even now i got netflix running all day & ram is 783mb, no swap(4gb) is being used, i don't tweak my swap so it's all system managed.

That is very light use IMO.  Maybe there is more difference between Ubuntu (Unity GUI) and Edubuntu (I run it with GNOME, there are several options) but with nothing but the system monitor running I use a gig of RAM, with normal web surfing or running videos I run about 1.5GB and with the hoggiest sites and six to eight tabs of that hoggiest site running I sometimes reach 2.5GB.  I am running 3.5GB (actually it detects 3.2GB as it is a 32-bit computer), I actually added memory as it originally had 2GB RAM and every time I hit the cap and went into swap my computer slowed to a crawl.  It never reached 2GB RAM used until a large update a few months ago and the hoggiest site I use was redesigned.   Running Netflix (or anything for that matter) and only using 783MB of RAM using Ubuntu (I assume the current LTS version 14.04.2) makes me wonder what is going on with my computer.  That actually sounds like the numbers I was getting with latest LTS Kubuntu and Xubuntu on my trial runs of them (with the RAM hog site I got numbers around 1.3-1.5GB of RAM used).  Of course if you are still running Ubuntu version 12.04 that might explain the difference.

---

### Post by poorguy on 2015-03-10
hey guys, ok i am confused here. i read that you should always include a swap partition no matter how much ram you had. i have always added the swap partition and have never used it. the next thing is if i am reading your post right how can writting to the swap on a hdd create additional wear.

the poorguy

---

### Post by efflandt on 2015-03-11
SSD has limited write cycles (maybe a lot, but still limited at some point), so using SSD for swap is not recommended, and a good idea to use tmpfs for /tmp. But I have not used swap at all for many years even on a regular hard drive mainly due to limited partition availability when installed on a Windows drive. For example my Win7 desktop was using 3 partitions (utility, recovery, OS) and some Windows programs storing some data in what they "thought" was an unused part of the mbr initially stepped on larger grub2 in the mbr killing it. Also a Win7 service pack update would not work unless Win7 owned the mbr to do something during reboot. So I leave the Windows mbr and set up 1 primary partition with grub installed to that partition instead of the mbr, and was not sure if grub could boot if installed on extended instead of primary partition. I leave the boot flag on sda2 and normally boot from grub on sdb from a small backup system on SSD, but in a pinch I could switch the boot flag to sda4 and boot sda instead of sdb. For some reason my system seems to take about as long to wake up from suspend as it does to cold boot, so I do not suspend or hibernate. Even after playing Steam games I do not use 8 GB:```
efflandt@XPS-8100-1404:~$ free
             total       used       free     shared    buffers     cached
Mem:       8102108    6247860    1854248      20252      91160    5332752
-/+ buffers/cache:     823948    7278160
Swap:            0          0          0
```But even on a non-gaming tablet PC with 2 GB RAM I have no swap because it has Win7 Pro on 32 GB SSD and runs either Ubuntu or Lubuntu 12.04 from SD with common /home partition.

When I tried putting grub on sda4 of my Win7 laptop (over a year ago with 13.10 when I did not want to tamper with the mbr) and tried setting its boot flag to sda4 something peculiar in its BIOS or mbr kept resetting the boot flag on sda2 and it would only boot Win7. So I had to install grub on a USB memory stick and boot sda4 from there. I recently installed 64-bit 14.04.1 to 512 GB mSATA SSD card (sdb) and now boot from that. It has 8 GB RAM and no swap, but since I don't need 13.10 anymore I could switch sda4 to an extended partition for data and swap.

---

### Post by C.S.Cameron on 2015-03-11
I use a bootable flash drive to control my home entertainment center, (ie TV).
I use a large swap so that I can hibernate in the middle of movies.

---

