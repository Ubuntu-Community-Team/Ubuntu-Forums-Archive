---
title: "Dual Boot (Karmic/XP), 2 HDDs, 1 HDD Not Found"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by WildcatRay on 2010-02-08
I have set up my system to dual boot Karmic and WinXP. Ubuntu 9.10 is on the master drive (IDE ATA) with WinXP on the slave. Grub2 is set up as per instructions, but I have WinXP set as my default OS.

Now for my problem. On one occasion, I turned off the computer from Ubuntu by the proper procedure. The next morning, the bios failed to detect the WinXP HDD. I was able to remedy this by moving the cable from the Ubuntu HDD to the WinXP HDD--I have the HDDs jumped to Cable Select--and booting into WinXP.

Before I shut down the computer the previous night, I had been accessing the WinXP disk copying information and files from it to my Ubuntu HDD and did not unmount the WinXP disk before shutting down the computer. Later, I returned the cable to it's original positioning--Ubuntu Master/WinXP Slave--and the computer booted with no issue. Since it has done so for several days after, I thought my not unmounting the WinXP disk may have been the reason for the bios not detecting the WinXP HDD.

Forward to yesterday. I rebooted from Ubuntu to WinXP only to have the bios not detect the WinXP HDD, again. This time I had not been accessing the WinXP HDD, so evidently, unmounting may not be as important as I first thought. Switching the cable again allowed me to boot into WinXP.

Though I have since switched the cable back, I have yet to boot into Ubuntu and back to WinXP. I am wondering if what I am seeing may be a known issue or if it may be a sign of another possible problem.

Your thoughts and suggestions?

P.S. The bios battery was replaced just a few months ago, so it is still pretty fresh.

---

### Post by ajgreeny on 2010-02-08
This sounds more like a hardware issue than a software one to me, and to answer your question about not unmounting winxp before shutting down, I can assure you that it will make no difference at all, as ubuntu will unmount the partitions that are mounted before shutting down automatically, in exactly the same way as if those partitions had been mounted automatically by fstab at boot.

Perhaps worth checking the disk(s) with their manufacturers diagnostic applications which may well be on the Ultimate Boot CD or using the Disk Utility on ubuntu 9.10, though I don't know if that will work on an ntfs partition/disk.
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by darkod on 2010-02-08
Personally I never trusted those cable select thingies. As a first step you might consider using master/slave by jumper. Look on your hdd labels, there should be one saying where to insert a jumper for master/slave.
Then decide which hdd you want as master or slave, and select by jumpers accordingly.
Depending on your BIOS you might need to enter the Main page or what ever it would be called, and re-detect the hdds.
Once they are fixed with jumpers as master/slave they should keep that setting permanently.

---

### Post by WildcatRay on 2010-02-08
> **ajgreeny said:**
> This sounds more like a hardware issue than a software one to me, and to answer your question about not unmounting winxp before shutting down, I can assure you that it will make no difference at all, as ubuntu will unmount the partitions that are mounted before shutting down automatically, in exactly the same way as if those partitions had been mounted automatically by fstab at boot.

Perhaps worth checking the disk(s) with their manufacturers diagnostic applications which may well be on the Ultimate Boot CD or using the Disk Utility on ubuntu 9.10, though I don't know if that will work on an ntfs partition/disk.
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

I did a quick check using DiskCheckup. All parameters show "OK". If I get a chance, I will try ultimatebootcd.

---

### Post by WildcatRay on 2010-02-08
> **darkod said:**
> Personally I never trusted those cable select thingies. As a first step you might consider using master/slave by jumper. Look on your hdd labels, there should be one saying where to insert a jumper for master/slave.
Then decide which hdd you want as master or slave, and select by jumpers accordingly.
Depending on your BIOS you might need to enter the Main page or what ever it would be called, and re-detect the hdds.
Once they are fixed with jumpers as master/slave they should keep that setting permanently.

That's a good thought and can be done more quickly than getting the ultimatebootcd, burning and running it. :p

---

