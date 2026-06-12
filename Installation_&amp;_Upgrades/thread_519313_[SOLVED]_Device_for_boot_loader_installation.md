---
title: "[SOLVED] Device for boot loader installation"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by sfgeorge on 2007-08-06
Howdy,

I'm on step 7/7 of the LiveCD GUI installer and almost ready rock. :)

The only last thing I want to do is preserve my MBR and the existing grub setup I have on another partition.

I'm looking to install ubuntu over my existing hda3 partiton, which currently has Gentoo on it.  The grub I want to save is on hda2.

I'm on the Advanced Options screen of page 7 of the installer.  For my setup, am I correct in thinking I should specify set my boot loader installation to (hd0,2)?

Here are my disks:

```
IDE1 master (hda)  -  160.0 GB ST3160023A
   #1 primary  115.3 GB   K ntfs       /media/hda1  (Windoze)
   #2 primary   21.0 GB B K reiserfs   /media/hda2  (Knoppix)
   #3 primary   21.0 GB   K reiserfs   /media/hda3  (Gentoo)
   #4 primary    2.7 GB   F swap       swap

IDE2 slave (hdd)  -  200.0 GB ST3200827A
   #2 primary    5.1 GB   K fat32      /media/hdd2
   #1 primary  195.0 GB B K ntfs       /media/hdd1
```

Thanks!

Stephen

---

### Post by sfgeorge on 2007-08-07
I have a habit of asking lengthy questions, perhaps that's the problem. :)

I'm just wondering how I should reference partition 3 of hda in the Advanced Options screen.  Based on documentation and other posts, I believe that it should be (hd0,2), but I just need to make sure.

Thank you!

Stephen

p.s., I have no idea whether this info is needed in context, but here it is...

While running the LiveCD, here's the output of the following commands...

**cat /etc/fstab**
```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda4 swap swap defaults 0 0
```

**sudo fdisk -l**
```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       14023   112639716    7  HPFS/NTFS
/dev/hda2   *       14024       16573    20482875   83  Linux
/dev/hda3           16574       19123    20482875   83  Linux
/dev/hda4           19124       19457     2682855   82  Linux swap / Solaris

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *         616       24321   190418445    7  HPFS/NTFS
/dev/hdd2               1         615     4939956    b  W95 FAT32

Partition table entries are not in disk order
```

**mount**
```
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
```

---

### Post by sfgeorge on 2007-08-07
After more reading, it looks like I've found the real command I needed in order to verify that hda=hd0...  based on info in this thread, I ran these commands:
```
sudo grub
```
while still in grub, I ran this:
```
find /boot/grub/stage1
```
...which gave me all of the information I needed in order to determine that hda = hd0.

The problem now is that, even though I know that (hd0,2) is where I am installing the ubuntu root, I get a grub error near the end of the ubuntu LiveCD install (see attached screenie).  For thread-searching purposes, the error I got was:

> **unable to install GRUB on (hd0,2)**

Executing 'grub-install (hd0,2)' failed.

This is a fatal error.

Stephen

---

### Post by sfgeorge on 2007-08-07
...At least I know I'm not crazy (though this thread proves that I talk to myself).  But what I really mean is I found a how-to that suggested doing things exactly as I did it.  Too bad I still have this funky grub error.

But [this page explains exactly what I'm trying to do]("http://kubuntuforums.net/forums/index.php?topic=3081671.0"), preserving Windows, keeping Knoppix as my GRUBer on (hd0,1), and adding ubuntu on (hd0,2):
> - - -   Installing a Linux OS after another Linux OS is already installed (Windows may or may not be in your system):    You have a Linux1 OS already installed and working fine. Its GRUB is installed to the MBR (hd0), it is your “main” Linux that controls the boot menu, and you want to install another Linux OS, call it Linux2.  (Note that this case applies whether you have one or two hard drives.)  How you handle this depends on the following question:

Question:  During the install of Linux2, where should you install GRUB:   to the MBR (hd0)?  or, to the root partition where Linux2 will be installed to?

[B]Case 1:   If you want Linux1 to continue to control the boot menu, then do NOT let the Linux2 installer put  GRUB in the MBR.  Instead, when given the choice, have the installer put GRUB in the root partition where you are installing Linux2.  You must also edit the menu.lst of Linux1 to include a boot entry for Linux2  (and so, you must access the /boot/grub/menu.lst in the Linux2 partition, using Konqueror or using Konsole, copy the boot entry for Linux2, and paste it into the /boot/grub/menu.lst of Linux1.)
- -  If you make a mistake here, after installation, you need to re-install GRUB from Linux1 to the MBR.  To do all this, see both: “Install or Re-install GRUB” and “The menu.lst” below.[/B]

Case 2:   If you want Linux2 to control the boot menu, then tell the Linux2 installer to put GRUB in the MBR (hd0).  In this case, the GRUB installed in (hd0) from Linux2 will handle Linux1, Linux2, and Windows if you have Windows.  (If your system won’t boot properly, you may also have to edit the /boot/grub/menu.lst of Linux2, and if so see “The menu.lst” below.  For many Debian distros, this should not be necessary, though.)
- -  If you make a mistake and don't install GRUB to the MBR, then after installation, you need to install GRUB from Linux2 to the MBR, so see “Install or Re-install GRUB” below...

I've seen other's with the grub-install failed error that I mentioned, but most are not able to run "find /boot/grub/stage1" within Grub, but I can.  Still scratching my head on why I'm stuck at 94% of the install with the "Executing 'grub-install (hd0,2)' failed." error.  Any help is appreciated.

Thanks,

Stephen

---

### Post by sfgeorge on 2007-08-08
I changed up the partitions on my primary drive, partly in order to make a separate /home partition for ubuntu.  My planned / (root) ubuntu partition will now be /hda5, so I specified (hd0,4) in the Advanced Options section of step 7/7 on the LiveCD.  Unforunately, still getting a similar error to before at 94%...
> Executing 'grub-install (hd0,4)' failed.

Here's my current drive layout.  Any ideas why I am still getting a grub-install error at 94%?

```
|           |           |           |                                                     |
| /dev/hda1 | /dev/hda2 | /dev/hda4 | /dev/hda3                                           |
|    ntfs   |  reiserfs |   swap    ||¯¯¯¯¯¯¯¯¯¯¯¯|¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯|¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯||
|  Windoze  |  Knoppix  |           || /dev/hda5  |    /dev/hda6   |      /dev/hda7      ||
|           |           |           ||  reiserfs  |    reiserfs    |       fat32         ||
|           |           |           || ubuntu "/" | ubuntu "/home" | win/linux workspace ||
```

Thanks,

Stephen

---

### Post by sfgeorge on 2007-08-08
...YES!  After several tries, I finally had success today with my install.  Now I running *real* ubuntu, not just the LiveCD. :guitar:

I´ve been trying to install grub to my ubuntu root (/dev/hda5) without overwriting the MBR.  The difference between my failure to do that last night, and my success today had something to do with 2 changes I made today; one of the 2 changes (or both) was/were necessary in order to have success.

First, today I used the *alternate cd* for 32-bit ubuntu 7.04 Desktop, whereas yesterday I was using the *LiveCD* of the equivelant version.  Second, for my custom grub location, today I specified* /dev/hda5* whereas yesterday I specified *(hd0,4)* - whether that made a difference, I don´t know (the two should be equivalent).

But additionally, and most importantly - I had read on the forums of others who had grub-install failed errors who said ¨second time´s a charm¨ - that if at first you do not succeed,  do the *exact same* install again (without rebooting).  I can confirm that this was the case for me.  The alternate cd could not install grub to /dev/hda5 the first time... I simply re-ran that step in the alternate cd with the *exact same parameter* for the grub location... and it worked the 2nd time.  8-[  (I did try it twice last night, using the LiveCD, and it did not work).

Woohoo, now I can really get down to business!    \\:D/

Stephen

---

