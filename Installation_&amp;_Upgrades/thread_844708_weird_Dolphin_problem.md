---
title: "weird Dolphin problem"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by Tom_ZeCat on 2008-06-29
Dolphin is my favorite file manager because I like how it easily does a dual panel and lets you customize it.  However, since my reinstall of Ubuntu 8.04, I can't get Dolphin to work right with external drives.  I have a 120 GB external Maxtor drive, which I formatted as an ext3 drive.  I was using it on another Linux workstation and then brought it back to this one to get some data back.  

The first thing I tried was to boot to an Acronis boot CD (which is itself a type of Linux) in order to back up my new install of the OS to the external hard drive.  I got an error from Acronis saying that it couldn't read the disk -- I don't know if it meant the internal or the external hard drive.  So then I tried to do it with the Norton Ghost boot disk, but couldn't get it to properly load.  I've back-burnered creating the OS image for now.  I've asked about it on the Acronis board, so it's not the subject of this post.  

Is is about Dolphin.  When I first booted back up into Ubuntu, the external drive was not showing up on the Desktop, nor did it show up in Ubuntu's default file manager. When I tried to pull it up in Dolphin, it said: > Malformed URL System:/media
So I powered down the PC and unplugged the external drive's USB cable, then powered back up.  Then I powered down again, plugged it back in, and powered back up.  At this point, it was seen again on the Desktop and in the default file manager.  Not so in Dolphin.  Dolphin gives me the same error message when I click on Storage Media.  

So I went into the Synaptec Package Manager and did a complete uninstall of Dolphin, then reinstalled it.  It didn't change a thing -- same problem.  In fact, I don't think it actually did a complete uninstall because upon reinstall, Dolphin already had all my custom settings such as the dual pane.  

According to the default file manager, the drive is not at "System:/media."  It's at "/media/disk."  In fact, if I type that into Dolphin, it goes there correctly.  

Dolphin is my favorite file manager.  How do I get it recognizing my external drive?

**Edit:**
Oops, never mind.  I figured it out.  I was able to right click on Storage Media and choose Edit.  Then I put in "/media/" and all was better.

---

### Post by nobody13 on 2008-08-07
I have the same problem but with my raid drive. I can navigate to /media raid/ and access it fine (so it's not really a problem so much as a small annoyance) but it doesn't show up under system:/media/. It shows my 2 raid 1 drives as sda1 & sdb1 (they're not mountable). If I go to /media it's there. My usb stick appears differently also. So were is system:/media actually looking at?

Here's what's in them:
system:/media/
```

system:/media/sdg1
system:/media/sdc1
system:/media/sdd1
system:/media/sdd5
system:/media/sdb1
system:/media/sda1
system:/media/sdc3
system:/media/fd0
system:/media/scd2

```

/media/
```

file:///media/cdrom
file:///media/cdrom0
file:///media/cdrom1
file:///media/disk
file:///media/floppy
file:///media/floppy0
file:///media/hdb1
file:///media/hdb5
file:///media/raid
file:///media/U3 System

dave@dave-desktop:/media$ ls -1l
total 42
lrwxrwxrwx  1 root root        6 2007-11-25 16:24 cdrom -> cdrom0
drwxr-xr-x  2 root root       48 2007-11-25 16:24 cdrom0
drwxr-xr-x  2 root root       48 2007-11-25 16:24 cdrom1
drwxr-xr-x 12 dave root    16384 1969-12-31 19:00 disk
lrwxrwxrwx  1 root root        7 2007-11-25 16:24 floppy -> floppy0
drwxr-xr-x  2 root root       48 2007-11-25 16:24 floppy0
drwxrwx---  1 root plugdev 12288 2008-08-06 16:48 hdb1
drwxrwx---  1 root plugdev  8192 2008-08-06 16:44 hdb5
drwxrwx---  6 root plugdev  4096 2008-08-07 15:39 raid
dr-xr-xr-x  1 dave root     2048 2007-10-28 08:52 U3 System


```

Am I using the wrong mount point or need to list it differently?

fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=0d06c78e-49e3-4eee-8300-d72c5d285ad3 /               reiserfs defaults        0       1
# /dev/hda1
UUID=67b3286b-a738-4b49-b19a-fc81686591e4 /boot           ext2    defaults        0       2
# /dev/hdb1
UUID=94249FD2249FB628 /media/hdb1     ntfs    defaults,umask=007,gid=46 0       0
# /dev/hdb5
UUID=FA74775B74771A19 /media/hdb5     ntfs    defaults,umask=007,gid=46 0       0
# /dev/hda2
UUID=a9c5eb81-5637-4fc4-a9b7-ecc44ed6e00f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
#raid
/dev/mapper/sil_aiaiafdeaidj1	/media/raid	ext3	defaults	0	0
```

---

