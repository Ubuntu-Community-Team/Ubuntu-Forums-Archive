---
title: "Vista/Ubuntu Dual Boot Install Trouble"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by HPHarty on 2008-11-16
I have been trying to install a Vista Ubuntu dual boot on my ThinkPad T61.  So far I have managed to create four partitions and install Vista correctly on one of them and the Lenovo Recovery partition on another.  Here is what I have currently:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x82fcf9f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    12914687     6456320   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    12927600    94832639    40952520    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3        94832640   135792719    20480040   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4       135792720   312575759    88391520    b  W95 FAT32
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 2055 MB, 2055021056 bytes
16 heads, 63 sectors/track, 3981 cylinders, total 4013713 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     4013712     2006825    b  W95 FAT32
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

Partition 3 is intended for Ubuntu and Partition 4 is intended to be a shared volume for documents, music, video, ect...

I was hoping that when I started up the ubuntu installer (I created a bootable flash drive in place of a Live CD) it would just recognize these partitions and I could be on my way.  However that is not the case.  The only options the partitioner provided me with were "Use entire disk" and "Manual".  Since I am a complete novice at this, I'm wondering how to proceed from here.  

Keep in mind restoring the Lenovo Recovery and Vista partitions is about a 5 hour process that I absolutely do not want to repeat.  However, the contents of Partition 4 are safely backed up on an external drive, so that one may be expendable.  I also have a GParted Live CD if it is needed.  Thanks for your help Ubuntu people.

---

### Post by taurus on 2008-11-16
Just pick the manual option and then tell the installer to mount whichever partition you want to use for Ubuntu as / and format it as ext3 filesystem.  Then, mount the other one that you want to share between Ubuntu and windows to somewhere.  Also, it's a good idea to have a swap partition when you install Ubuntu.

---

