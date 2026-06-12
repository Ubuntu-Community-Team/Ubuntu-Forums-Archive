---
title: "Restoring old XP partition to Ubuntu..."
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by Baldrick_NZ on 2010-09-29
My system had an installation of XP and Ubuntu 10.04 as dual-boot. For quite sometime I configured startup manager to automatically log in to Ubuntu, which avoided me having to choose which OS I wanted to boot to.

Anyway, I decided that XP was taking up valuable hard drive space, so I deleted it it using gparted via the LiveCD. That worked great. XP is no longer there, but instead I have a huge amount of 'unallocated' space, which makes sense to me to join that up with my existing Ubuntu partition. 

And there's the rub. How do I take an unallocated portion of a hard drive and merge that into an existing partition?

Or, would it make more sense to make the unallocated space into separate partition ext4, which my existing Ubuntu install will also see as a separate drive?

Any help would be much appreciated...

---

### Post by skumnull on 2010-09-29
Have you tried resizing the partition?

---

### Post by Baldrick_NZ on 2010-09-29
> **skumnull said:**
> Have you tried resizing the partition?
Thanks for your reply.

Under Gparted? No. I didn't realise you could.
Does this need to be done with the aid of the LiveCD, or can it be done while the computer is running in it's normal state?

Am I supposed to have Gparted in Applications/System/Admin after installing Ubuntu? Or is that done away with during the installation process? 

Cheers.

---

### Post by Goolie on 2010-09-30
```
sudo apt-get install gparted 
```

```
 sudo gparted 
```

It should come up, and from there you should see your partitions.

From here you can handle that unallocated space.  Right-Click --> Resize.

---

### Post by plucky on 2010-09-30
> Does this need to be done with the aid of the LiveCD, or can it be done while the computer is running in it's normal state?


You cannot resize your Ubuntu partition while you are running Ubuntu.Use the Live CD to do the job.

Just remember you can only move the front of a partition into the allocated space and then grow the partition from the rear.As this moves all your data as well,it could take a long time depending on how much data has to be moved.

**To be safe have a backup of your data**

Good Luck

---

### Post by Rubi1200 on 2010-09-30
> **plucky said:**
> You cannot resize your Ubuntu partition while you are running Ubuntu.Use the Live CD to do the job.

Just remember you can only move the front of a partition into the allocated space and then grow the partition from the rear.As this moves all your data as well,it could take a long time depending on how much data has to be moved.

**To be safe have a backup of your data**

Good Luck
+1

Just to add a couple of things; you must also unmount the swap partition (right-click > Swapoff) and make sure you do a backup!

If you are unsure of anything, ask first before things go wrong.

Use GParted on the LiveCD and post the results of ```
sudo fdisk -l
``` if you need another opinion.

Good luck!

---

### Post by Baldrick_NZ on 2010-09-30
OK, so I'm in now using the LiveCD, and have bought up Gparted.

As you'll see from the pic attached, sda5 is my Ubuntu partition, and sda1 is where Windows was. I've formatted it to ext4 hoping that would benefit my resize.

When I right click and choose 'Move/Resize" there appears to be no option to "Move", just to Resize. And when I try that, I can only get it to resize smaller.

I also tried while sda1 was unallocated, which didn't help either.
All I really want to do is reclaim the partition that Windows had and merge it into my current Ubuntu partition.

Here's the result of sudo fdisk -l:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00024175

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       34102   273924283+  83  Linux
/dev/sda4           34103       60802   214457345    5  Extended
/dev/sda5   *       34103       60050   208418816   83  Linux
/dev/sda6           60050       60802     6037504   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

I have also done a full back-up - though hoping I don't need it! lol

Any help would be much appreciated!

---

### Post by Baldrick_NZ on 2010-09-30
Oop, forgot to add pic.. Attached here.

---

### Post by Mark Phelps on 2010-09-30
You will have to do the following:
1) Remove the first partition
2) Resize the EXTENDED partition to the left to fill the unallocated space
3) Resize the sda5 partition to the left.

That should work.

However, since the XP partition was first, your GRUB entries for Ubuntu will be wrong now -- as they will be pointing to the wrong partition.  You will have to rebuild the GRUB menu in order to boot into Ubuntu again.

---

### Post by Baldrick_NZ on 2010-10-01
> **Mark Phelps said:**
> You will have to do the following:
1) Remove the first partition
2) Resize the EXTENDED partition to the left to fill the unallocated space
3) Resize the sda5 partition to the left.

That should work.

However, since the XP partition was first, your GRUB entries for Ubuntu will be wrong now -- as they will be pointing to the wrong partition.  You will have to rebuild the GRUB menu in order to boot into Ubuntu again.

Thanks for that Mark. I'll give that a go when I get back home. Incidently, since deleting XP and reformatting that partition, I've had no problem starting Ubuntu. Seems the grub is intact still?

Cheers.

---

### Post by plucky on 2010-10-01
You have to also turn swap off before it will allow you to change the extended partition.Right click on the swap partition and select swapoff.

Good Luck

---

