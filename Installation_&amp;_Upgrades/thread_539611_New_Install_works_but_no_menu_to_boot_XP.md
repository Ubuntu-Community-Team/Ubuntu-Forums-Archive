---
title: "New Install works but no menu to boot XP"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by jeftere on 2007-08-31
Just installed 7.04 on my laptop.Grub will only boot into Ubuntu and does not give WinXP as an option.

---

### Post by jackocleebrown on 2007-08-31
Halo!

This should have been automatically done on install....  it is not too complicated to setup manually but it is a bit daunting if this is your first time using Ubuntu or Linux.

First things first, we need to work out which partition your XP installation is on.

Open the program called "Terminal" which is under the {applications}-{accesories} menu

Type in "sudo fdisk -l" and press enter it will ask you for your password and then will print lots of information about the disks on the system. Copy all this stuff and post it here.

Jack.

---

### Post by jeftere on 2007-08-31
Thanks for the fast reply!

Here is the output:
The one i want to boot is sda2




Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb1bfb1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   de  Dell Utility
/dev/sda2              14        5606    44925772+   7  HPFS/NTFS
/dev/sda3            6898        7295     3196935    7  HPFS/NTFS
/dev/sda4            5607        6897    10369957+   5  Extended
/dev/sda5   *        5607        6836     9879943+  83  Linux
/dev/sda6            6837        6897      489951   82  Linux swap / Solaris

Partition table entries are not in disk order
jb@jb-laptop:~$

---

### Post by jeftere on 2007-08-31
Thanks again for the quick reply Jack!

Problem solved by adding to the menu.lst.

title		Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by jackocleebrown on 2007-08-31
I'm impressed! You figured it out yourself!
Is this your first time using Ubuntu?

Glad to help,
Jack

---

### Post by jeftere on 2007-08-31
I have a co-worker who introduced me to Ubuntu and has it running on his laptop also.
We checked his menu.lst file and figured it out that way.
Although there is a great deal of guidance also in the comments in the file that is very handy.:)

I'm on day three of Ubuntu and the excitement grows. I installed on my home pc but didn't have this same problem....... Oh ya i guided to take the whole drive and trash the win install. Heh heh.

No more windoze at home!:guitar:

---

