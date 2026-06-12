---
title: "cant find harddrives"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by relaxedcrazyman on 2008-06-04
hello, i am brand new to ubuntu. i installed it with vista already installed. i cant find access to any of my harddrives except my external. it doesnt show the drive it was installed on either. any help would be much appreciated.

---

### Post by oldos2er on 2008-06-04
> **relaxedcrazyman said:**
> hello, i am brand new to ubuntu. i installed it with vista already installed. i cant find access to any of my harddrives except my external. it doesnt show the drive it was installed on either. any help would be much appreciated.

 In Ubuntu, go to Places, Computer, Filesystem. This will be your Ubuntu partition (assuming you placed /root, /boot, and /home in a single partition). If you don't see any other partitions e.g. "100 GB Media", we can help you mount them so they show up in Nautilus.

---

### Post by relaxedcrazyman on 2008-06-04
> **oldos2er said:**
> In Ubuntu, go to Places, Computer, Filesystem. This will be your Ubuntu partition (assuming you placed /root, /boot, and /home in a single partition). If you don't see any other partitions e.g. "100 GB Media", we can help you mount them so they show up in Nautilus.

There are no other partitions. i wanted it so that the files that i transfer over on cd or dvd can be saved on my other internal harddrive which have a lot more space available.

---

### Post by Pumalite on 2008-06-04
Get Gparted Live CD and post a screenshot:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.

---

### Post by relaxedcrazyman on 2008-06-04
> **Pumalite said:**
> Get Gparted Live CD and post a screenshot:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.

my friend had showed me this earlier, but could not make sense of it...
this is the drive ubuntu is installed on...
[IMG]http://farm4.static.flickr.com/3071/2551994155_9a854c7a7e_o.png[/IMG]


this is the drive i want to use for saving files and stuff. but i dont want to erase what is already on it

[IMG]http://farm4.static.flickr.com/3279/2552821732_122dccafa0_o.png[/IMG]

---

### Post by Pumalite on 2008-06-04
Your first picture shows only Windows. Your second drive appears empty. Ubuntu is nowhere to be seen.

---

### Post by relaxedcrazyman on 2008-06-04
> **Pumalite said:**
> Your first picture shows only Windows. Your second drive appears empty. Ubuntu is nowhere to be seen.

that is how new i am to all of this, what should i do to present information you can use.

---

### Post by Pumalite on 2008-06-05
Use the Gparted Live CD ande not the gparted that comes with Ubuntu. Post a new screenshot.

---

### Post by relaxedcrazyman on 2008-06-05
> **Pumalite said:**
> Use the Gparted Live CD ande not the gparted that comes with Ubuntu. Post a new screenshot.

When i booted from the disc i didnt know what to do, but this is what the screen said:

GNU GRUB version 0.97 (639k lower/3404388k upper memory)

then there was a command prompt, no idea what to enter...


EDIT: i downloaded a earlier version of it and it worked. i took a screenshot, but when i started up ubuntu again, i could not find the screenshot in the 'root' directory.

---

### Post by Pumalite on 2008-06-05
Try version Gparted-Live-0.3.7-2.iso
At the boot prompt; press 'Enter'

---

### Post by relaxedcrazyman on 2008-06-05
i just noticed that i have been getting this error from windows boot manager right after i select to run ubuntu:

Warning: Unrecognized partition table for drive 81. Please rebuild it using a Microsoft-compatable FDISK tool(err=4)


and while i was using the Gparted i must have done something, because when i try and run Ubuntu it starts then this comes up:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-inShell (ash)

and it is command prompt

---

### Post by Pumalite on 2008-06-05
Use rescuecd to check your drive and fix your partition table if you really need to:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by relaxedcrazyman on 2008-06-07
i have tried everything to get a new screen shot, but i just can not get it to work for me. is there any other way i can present the information that you need? and what information would that be?

---

### Post by Pumalite on 2008-06-07
Post:
sudo fdisk -lu

---

### Post by relaxedcrazyman on 2008-06-07
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff2db8be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   312578047   156288000    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ec6494e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  EFI GPT

Disk /dev/sdc: 2048 MB, 2048729600 bytes
64 heads, 63 sectors/track, 992 cylinders, total 4001425 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1             245     3999743     1999749+   7  HPFS/NTFS

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd8384a4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   490223474   245111706    7  HPFS/NTFS

---

### Post by Pumalite on 2008-06-07
This is your problem:
'WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ec6494e

Device Boot Start End Blocks Id System
/dev/sdb1 1 4294967295 2147483647+ ee EFI GPT

What kind of drive is this or how did it get that way?

---

### Post by relaxedcrazyman on 2008-06-07
it is an internal drive. i have no idea how it got any way. bought it installed it, no problems since. i really dont even know what that error is

---

### Post by Pumalite on 2008-06-07
I don't either. What do you have in that drive?

---

### Post by relaxedcrazyman on 2008-06-07
just a bunch of movies and tv shows. i think i remember when i first got it, that i had to make it a dynamic disk to get it to work, but i dont even know what that means.

---

### Post by Pumalite on 2008-06-07
If you have and external drive; save all that, and use gparted to format the drive ext3. Then restore your stuff.

---

### Post by relaxedcrazyman on 2008-06-07
that may take some time, i will probably have to buy another external harddrive, or perhaps another internal (dont have enough space to back it all up) it may be 2 weeks before that happens, if i am still having similar problems, should i post in this thread or create a new one?

---

### Post by Pumalite on 2008-06-07
You can continue this thread later if you want. If not I; there will be many here to help you.

---

