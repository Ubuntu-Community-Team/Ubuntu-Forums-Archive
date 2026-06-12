---
title: "Help me to Install,please !"
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by lolly325 on 2012-02-23
I'm a bit confused with Ubuntu installation.
In [www.ubuntu.com](www.ubuntu.com), there are 3 installation option, first "Replace Windows 7 with Ubuntu", second "Install Ubuntu alongside Windows 7", and last "Something Else"

I have do it rightly, make an bootable usb with pendrivelin, and I'll try to boot the usb.
And I chose the "Install Ubuntu" button, but this is weird !
"Install Ubuntu alongside Windows/XP/Vista/7" doesn't appear !?
"Replace Windows Vista" are on there with "Something Else" :(

This are my installation option :
1. I have an E: drive unused on my PC
2. I want to make a dual boot Windows Vista with Ubuntu 11.10

Thanks a lot for the answer.......

---

### Post by darkod on 2012-02-23
1. If the E: partition (it's a partition but usually windows calls then drives which should be distinct from disk drive) is ntfs, linux doesn't install on ntfs.

Delete the E: partition and leave the space as unallocated. Ubuntu will create its own partitions (or you can create them manually).

2. If Vista is not detected, the option "along side" will not be offered which seems to be what is happening to you. You will need to investigate why Vista is not detected.

Maybe you have raid meta data remains on the disk if you have used it in raid before, maybe it's Dynamic disk and not Basic, etc.

Boot the ubuntu cd in live mode (Try Ubuntu), and in terminal execute:
sudo fdisk -l (small L)

Post the results.

---

### Post by lolly325 on 2012-02-23
> **darkod said:**
> 1. If the E: partition (it's a partition but usually windows calls then drives which should be distinct from disk drive) is ntfs, linux doesn't install on ntfs.

Delete the E: partition and leave the space as unallocated. Ubuntu will create its own partitions (or you can create them manually).

2. If Vista is not detected, the option "along side" will not be offered which seems to be what is happening to you. You will need to investigate why Vista is not detected.

Maybe you have raid meta data remains on the disk if you have used it in raid before, maybe it's Dynamic disk and not Basic, etc.

Boot the ubuntu cd in live mode (Try Ubuntu), and in terminal execute:
sudo fdisk -l (small L)

Post the results.

Do I need to use windows hd manager to shrink the E: partition ?
Please, help me out.....

---

### Post by darkod on 2012-02-23
Yes, if you only want to shrink it, use Disk Management tool in Vista.

If you wish to use all of that space for ubuntu, simply delete it in Disk Management and leave the space as unallocated.

But if you are only shrinking it, you need to count in DM how many primary partitions you have right now. If you have 4 primary, you will not be able to simply install without needing other partitioning steps. Because 4 primary partitions is the limit of a disk.

---

### Post by lolly325 on 2012-02-24
> **darkod said:**
> Yes, if you only want to shrink it, use Disk Management tool in Vista.

If you wish to use all of that space for ubuntu, simply delete it in Disk Management and leave the space as unallocated.

But if you are only shrinking it, you need to count in DM how many primary partitions you have right now. If you have 4 primary, you will not be able to simply install without needing other partitioning steps. Because 4 primary partitions is the limit of a disk.

After, I'll do that, and install oneiric with usb on E: with "Install Alongside Windows Vista" choice, I'm still can boot to vista right ?

---

### Post by darkod on 2012-02-24
Yes, you will be able to boot vista or ubuntu from the grub2 boot menu.

And note that you will not be installing it on E:. After you shrink E: you will install ubuntu into the unallocated space that the shrink creates.

---

### Post by lolly325 on 2012-02-24
> **darkod said:**
> Yes, you will be able to boot vista or ubuntu from the grub2 boot menu.

And note that you will not be installing it on E:. After you shrink E: you will install ubuntu into the unallocated space that the shrink creates.

Okay...
muchas gracias, senor ;)
I will try it tommorow.....

---

