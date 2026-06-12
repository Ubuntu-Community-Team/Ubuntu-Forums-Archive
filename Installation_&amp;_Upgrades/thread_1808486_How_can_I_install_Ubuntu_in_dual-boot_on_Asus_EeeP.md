---
title: "How can I install Ubuntu in dual-boot on Asus EeePC 1015PX?"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by MaxReed on 2011-07-20
Hi everybody!
I bought a netbook Asus, an EeePC 1015PX with Win7 Starter. Now I want  to install in dual-boot Ubuntu. I created a new partition with Win7  reducing the space of the first partition (the one with Windows). In  this moment, for Windows, that space is marked as "not allocated". I  tried to install ubuntu by USB disk but he tells me that the space that I  have created is unusable.
On the HD there are five partition,one with Win, one for data, one for  recovery, one of only 16 Mb that I don't know what is it and what is its  function, and the partition created by me.

So, how can I install Ubuntu on my netbook, whereas Ubuntu does not want to use the free space that I created?

Thanks to all and sorry for my english!!

---

### Post by TBABill on 2011-07-20
When in the Ubuntu session and beginning in the install process you need to mark the box to setup partitions manually, then select the partition that is "unused space" and have the system format it and set it as ext4 (or whatever you want to use).

---

### Post by MaxReed on 2011-07-20
I tried to do it but he tells me that I can't create more than four primary partition

---

### Post by Quackers on 2011-07-20
Well the Ubuntu installer is trying to save you from a grave mistake.
The maximum number of primary partitions on any single mbr partitioned disc is 4. Sadly it has become the practice of several manufacturers to use all 4 by default. This is a ridiculous practice, imo. This means that unless a partition is deleted you can't install another operating system (which, I suspect, is the reason they do it).
If it is a HP machine some people in your position have deleted the HP TOOLS partition then shrunk their C: partition to make space to install Ubuntu into.
These jobs should be done in the Windows Disk Management utility and the C: partition should be defragmented first and the system should be rebooted when finished.
Once these jobs are done you can install Ubuntu using the "install alongside" option.

---

### Post by akand074 on 2011-07-20
Yes, as Quackers said. Max amount of Primary partitions you can have is 4. Luckily with Ubuntu you can create a Logical partition and then have as many of those as you want, but you still have to remove a primary partition first to do that. Anyways, if you can create recovery disks (external disc drive) or any other backup, do it. Then delete a partition you don't want/need and you can now install Ubuntu. Let the autoinstaller do it (manually you'll have to know to make swap and set Ubuntu's mount point to '/' but if you know what you're doing I'd recommend manually installing).

---

### Post by MaxReed on 2011-07-21
I can't delete one of the partition because, one is for recovery,one for boot boster, one contain my data and one is for windows. That of Windows is too big and I would like to reduce that but I see that I can't do it. There are any problem if I convert my disk in dynamic partition? 
at this point is better to install ubuntu with wubi inside Windows?

---

### Post by akand074 on 2011-07-21
> **MaxReed said:**
> I can't delete one of the partition because, one is for recovery,one for boot boster, one contain my data and one is for windows. That of Windows is too big and I would like to reduce that but I see that I can't do it. There are any problem if I convert my disk in dynamic partition? 
at this point is better to install ubuntu with wubi inside Windows?

I'd probably backup your data, wipe the partition and create two logical partitions (not primary), one for Ubuntu and one for your data. Or check if the recovery partition also recovers the boot booster or what not then you can delete both Windows and the boot booster, install Ubuntu on a logical partition and then recover.

I wouldn't recommend Wubi, it's really only for testing from within Windows. But it's a choice.

---

### Post by nk8215 on 2011-11-29
> **Quackers said:**
> Well the Ubuntu installer is trying to save you from a grave mistake.
The maximum number of primary partitions on any single mbr partitioned disc is 4. Sadly it has become the practice of several manufacturers to use all 4 by default. This is a ridiculous practice, imo. This means that unless a partition is deleted you can't install another operating system (which, I suspect, is the reason they do it).
(...)
Hello,
I wanted to avoid that by installing Ubuntu onto an external USB HDD, however, another problem appeared.
GRUB just won't load, rewarding my boot attempts with the well-known "reboot and select proper boot device" message. Later, I figured out that this could be somehow connected with EFI, my search for a walkthrough was unfortunately unsuccessful.
Could you give me an advice?
Thanks in advance and sorry for my English,
nk8215

---

