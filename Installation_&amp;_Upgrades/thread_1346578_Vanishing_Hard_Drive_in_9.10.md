---
title: "Vanishing Hard Drive in 9.10"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by unklejoe on 2009-12-05
First off, I'm openly new to Ubuntu 9.1. After a massive software failure in Vista, I made the switch a week ago and love it. I do however have one (slightly large) issue. 

My laptop has a 120gb hard drive. I followed the installation process as I had read on some tutorials and everything went fine. However, I seem to have lost 107gb of my hard drive!

My / has 380mb free, and there is nothing showing up with the remaining 107gb. Which makes it hard to download and install any software or music. 

So, how badly did I screw up the installation? Or am I just missing a folder with my 107gb in it?

Oh, and if you can help, please remember I'm new to Ubuntu and Linux in general. 

Many thanks for any help. Greg

---

### Post by darkod on 2009-12-05
Open terminal (Applications-Accessories) and run:
sudo fdisk -l (small L)

That will show you all your partitions on the drive. See if it's what you expect it to be. Another option is that if it's NTFS partition you might not be mounting it. Check fdisk first, it will give you some info. Post it here if you need help.

---

### Post by unklejoe on 2009-12-05
Thanks for the fast reply. I rand sudo fdisk in the terminal and it came up with

[Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors]

I still have no idea where my hard drive space went! I have a feeling I messed up the installation and it wasn't partitioned.

---

### Post by darkod on 2009-12-05
This just gave you the options of fdisk. You should run
sudo fdisk -l

and that is small L at the end.

---

### Post by unklejoe on 2009-12-05
Ahh got ya. Ran it againand got this...

[Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1888ad39

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806    0  Empty
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14131     1092388+  82  Linux swap / Solaris
/dev/sda6           14132       14566     3494106   83  Linux
/dev/sda7           14567       14593      216846   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21af5b41

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS]

The 500gb hard drive is my external hard drive and is just for Data.

---

### Post by darkod on 2009-12-05
Did you have Vista and Ubuntu together as dual boot? Your first partition /dev/sda1 is right there but for file system it says empty. There is your space but it seems you were never using it for ubuntu. If vista failed and you formatted it, or similar, it will not automatically expand that space into ubuntu.

---

### Post by unklejoe on 2009-12-05
I gave Vista a full format and then installed Ubuntu on the full blank drive. 

So I did screw up the installation?  So how do I expand the space? I don;t mind re-formatting as I have nothing installed except a few drivers.

---

### Post by arashiko28 on 2009-12-05
What I see there is that you have 2 swap partitions, one Linux partition, one extended and one empty.

Did you whiped out windows?

My guess is that you made a slight mistake during installation.
Swap should be at least the same size as your RAM
if you're having separate partitions, the filesystem /, should be at least 4 GB, 8-10GB recommended. (I gave it 20).
And /home, to your choice.

I am doing an installation later, I'll take some step by step pics, if you haven't solved your problem, it will help you. I have them right now, but they're in spanish.

---

### Post by darkod on 2009-12-05
Hmmm confusing a little bit. Or you selected different option then you thought. If you selected ubuntu to use the whole drive it should have installed it on the whole drive.
Yes, reinstalling at this point seems best. Make sure you instruct ubuntu to use the whole drive, not just the free space. The leftover partition from vista is not considered free unpartitioned space. Maybe that happened last time.

---

### Post by unklejoe on 2009-12-05
I'm guessing my empty one is my 107gb. But I have no idea how to either access it. 

During installation, I just followed the 6 steps. On the partition step, I just used the "erase and install" feature which is what the tutorial told me to do. That's where I think I went wrong.

---

### Post by darkod on 2009-12-05
Actually that sound like the correct option. I don't remember how exactly it was called now, but it was something like that. Also look closely is your drive gonna be shown as 120GB. Maybe the vista partition got messed up and it can't be recognized as part of the drive. So even selecting the "use whole drive" option would limit it to the 13GB, not whole 120GB. This is just my assumption.
I found this screenshot, attached.

---

### Post by raymondh on 2009-12-05
You can resize of re-install.  Should you decide to resize, kindly post a screenshot of a gparted output to help the forum visualize.  I see your fdsik - l output but am curious about sda1.  Also, kindly unmount and detach the sdb.

To get a screenshot ....

1.  Access gparted (system > administration)
2.  Once gparted outputs (window pop-up), you can either
-  press PrtScr key which will prompt you where to save the screenshot or,
-  access "take a screenshot" from applications > accessories
3.  In your next post, attach the .png file by clicking the attach icon (beside the smiley face), broswing for the .png file (which would've been saved by default in your desktop), and uploading.

Regards,

---

### Post by unklejoe on 2009-12-05
I took the easy way out and did a fresh install this time selecting a different setting. Now works perfectly and I have my hard drive back! /thanks a lot for all your help. Now time to re-install all those drivers!

---

### Post by darkod on 2009-12-05
Excellent. You got it sorted anyway. :)

---

