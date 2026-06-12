---
title: "Neiter XP or Ubuntu boots after Install"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by Malax on 2008-10-12
Back again.  I gave up on trying to install both os's to the same drive, and decided I would use one drive for Windows XP and one for Xubuntu.

I ran the guided partition using my entire drive, leaving my windows installation alone.  I have 3 hard drives, 1 40gb ide, 1 80gb ide, and one 500gb sata. 

All were detected fine during the setup, but when I tried to boot I got grub error 17 and the boot stopped.

I then searched for some solutions, switched my jumper settings around with the xp drive as master and ubuntu as slave, and now I'm getting error 22.

I can't boot ubuntu at all, even from the super grub disc, and now windows will only boot until about the windows xp splash screen before it hangs forever.  I also got that far from the super grub disk.

Any help would be greatly appreciated.  I'm a complete novice with all of this.

---

### Post by Pumalite on 2008-10-12
If you see Grub; hit 'e' then 'e' again. Try different combinations:
(hd0,1), (hd1,0).  Press 'Enter', then 'b' for boot. When you find the right one; you can make the change permanent in menu.lst.

---

### Post by Patb on 2008-10-12
Malax, make sure the partition names and uuids are correct for the partition you are trying to boot. Note that grub numbering starts at 0 whereas linux starts at "a" or 1. Thus Grub's (hd0,1) refers to /dev/sda2 and (hd1,0) refers to /dev/sdb1 and 
so on. To list relevant information, from a live CD:
```
sudo fdisk -l
sudo blkid
```
Cheers, Pat.

---

### Post by caljohnsmith on 2008-10-12
> **Malax said:**
> All were detected fine during the setup, but when I tried to boot I got grub error 17 and the boot stopped.

I then searched for some solutions, switched my jumper settings around with the xp drive as master and ubuntu as slave, and now I'm getting error 22.

So do you get those Grub errors before you see a Grub menu or after you select an OS and try to boot it?

---

### Post by Malax on 2008-10-13
Before I ever see a grub menu.  I've never seen the option to boot a particular os outside of the grub disc.

Actually, I believe I have the correct jumper settings now (xp master, ubuntu slave), because it wasn't booting before when I did that, so at least it looks like I'm getting SOMEwhere.  Still getting error 17 though.

Pat, this is the printout of the commands you listed.  Sorry, but half of this is greek to me.

> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2eaf2eaf

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9354    75135973+  83  Linux
/dev/hda2            9355        9729     3012187+   5  Extended
/dev/hda5            9355        9729     3012156   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo blkid
/dev/hda1: UUID="718bb14b-b227-4385-bb5b-0525b130998d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: UUID="d9e3c3d5-3aea-438e-9d58-f9d6f207a644" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ 



---

### Post by Sef on 2008-10-13
This is Grub error 17:

> 17 : Cannot mount selected partitionThis error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.What does your XP partitions?   Windows needs to be on the first primary partition.

---

### Post by Malax on 2008-10-13
> **Sef said:**
> This is Grub error 17:

What does your XP partitions?   Windows needs to be on the first primary partition.

Windows has its own drive with only one partition on it.  However, I noticed just now that when I went into Gparted, it's only picking up the 1 drive with linux on it, nothing else, not even my sata for data storage.

This is the first time this has happened, but like  I mentioned, my jumper settings are different now.

---

### Post by confused57 on 2008-10-13
For now, I would recommend that you set up your drives exactly as they were when you installed Ubuntu...boot up Super Grub Disk:
1.) Super Grub Disk (No Help)
2.) English SGD
3.) Windows
4.) Fix Boot of Windows


This should restore your ability to boot your Windows drive.

Then you might want to read this tutorial for setting up a dual boot with separate drives:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by Patb on 2008-10-13
Malax, try to read the Greek, even if only a bit at a time (:)).  Your output shows that fdisk can only see one hard drive, "Disk /dev/hda: 80.0 GB". But you said you had three. Perhaps switching the jumper settings has resulted in your BIOS not recognising some of your drives. If your BIOS doesn't recognise them, your OS won't. 

That is just by way of explanation. The advice from Confused57 seems the best course from here. Let us know how you go. 

Cheers, Pat.

---

### Post by adrian15 on 2008-10-13
> **Malax said:**
> 
I ran the guided partition using my entire drive, leaving my windows installation alone.  I have 3 hard drives, 1 40gb ide, 1 80gb ide, and one 500gb sata. 

All were detected fine during the setup, but when I tried to boot I got grub error 17 and the boot stopped.
Any help would be greatly appreciated.  I'm a complete novice with all of this.

Can you please copy-paste here your [hard disk partitions layout from SGD point of view](http://www.supergrubdisk.org/wiki/Support_Rules#Run_partition_layout_option)?

Also... Did you ever try the **Boot Linux Directly** options ?

adrian15

---

### Post by Malax on 2008-10-13
> **Patb said:**
> Malax, try to read the Greek, even if only a bit at a time (:)).  Your output shows that fdisk can only see one hard drive, "Disk /dev/hda: 80.0 GB". But you said you had three. Perhaps switching the jumper settings has resulted in your BIOS not recognising some of your drives. If your BIOS doesn't recognise them, your OS won't. 

That is just by way of explanation. The advice from Confused57 seems the best course from here. Let us know how you go. 

Cheers, Pat.

Yeah, I understood that. I'm going to put the jumpers back the way they were and see if i can fix my windows boot.  Keep you posted.  Thanks everyone.

---

### Post by WWSmith36 on 2008-10-13
Once you get fix the jumpers and all three of your drives are recognized by bios, we should be able to help you.  The first thing we will want to look at is your output from

sudo fdisk -lu

with all three drives

The grub 17 error: Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

This typically occurs when trying to boot windows in cases where there are mixed drives (IDE, ,SCSI, SATA) and there is disagreement between BIOS, GRUB, or the kernel regarding which disk is the first disk.  This situation can resolved by using the grub CLI and then modifying the menu.lst file.  Sometime this error occurs simply because root command used rather than rootnoverify on a NTFS filesystem.

The grub 22 error: No such partition
This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

This error occurred because after you switched the jumpers two of your drives window and sata drivers were not being seen at all, so grub was pointing to a partition that didn´t exist in the current configuration.

---

