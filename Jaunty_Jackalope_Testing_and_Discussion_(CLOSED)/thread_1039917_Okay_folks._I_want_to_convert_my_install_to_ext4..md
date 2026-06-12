---
title: "Okay folks. I want to convert my install to ext4."
date: 2009-01-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-01-15
But I don't want to dig through multiple topics and fudge my system by following conflicting advice.

Please, help me out.

:3

---

### Post by caryb on 2009-01-15
+1 there seems some ambiguity about converting the root partition? Some say yes & some say no!


Cary

---

### Post by cdtech on 2009-01-15
Taken from here:
[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

> **[SIZE="4"]Converting an ext3 filesystem to ext4:[/SIZE]**
To convert an existing ext3 filesystem to use ext4, use the command
       $ tune2fs -O extents,uninit_bg,dir_index /dev/DEV
**WARNING:** Once you run this command, the filesystem will no longer be mountable using the ext3 filesystem!
After running this command, you MUST run fsck:
       $ fsck -pf /dev/DEV
**NOTE:** by doing so, new files will be created in extents format, but this will not convert existing files. However, they can be transparently read by Ext4.
**WARNING:** It is NOT recommended to resize the inodes using resize2fs, as this is known to corrupt some filesystems.

---

### Post by caryb on 2009-01-15
I would use caution, just hosed my pc & my alpha 2 cd does not recognise my file system! Am not upset as I will rebuild as soon as the alpha 3 iso is ready.


Cary

---

### Post by daigorobr on 2009-01-15
I used [this]("http://ubuntuforums.org/showpost.php?p=6512542&postcount=24") and got it all working flawlessly.
My only adaptation was doing it for both my / and /home partitions.

---

### Post by LordVeovis on 2009-01-15
I would recomend to reinstall with ext4 over your current instal;l with alpha 3.  The older ext3 is not actually converted to ext4, it just makes all future writes be ext4 compatible.  So to truly get ext4, you have to make it a fresh install.

---

### Post by autocrosser on 2009-01-15
I would do a reinstall--I converted one of my testing installs & had problems with the patched grub--Colin is trying to duplicate the problem & repatch--I did a work-around by backing up my /boot, deleting it from my install & then reinstalling /boot--take a look at the other thread & read the bug report....  [http://ubuntuforums.org/showthread.php?t=1039840](http://ubuntuforums.org/showthread.php?t=1039840)

That being said---I have found a constant 3 sec improvement in boot to gdm in my system with EXT4--just want all the bugs killed so we can call it the default.....

---

### Post by Slug71 on 2009-01-15
Fresh install with Alpha 3.

---

### Post by Starks on 2009-01-15
I'm getting a read-only filesystem error.

---

### Post by jerrylamos on 2009-01-17
Is ext4 ready for prime time?  Check out

[http://ubuntuforums.org/showthread.php?t=1040199](http://ubuntuforums.org/showthread.php?t=1040199)

for multiple cases of irretrievable data loss....

Jerry

---

