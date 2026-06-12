---
title: "Windows partition type changed during install"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by dbova on 2006-09-11
Ok.  I typed this big long message and walked away and my session timed out so this will be short(er).

I tried to install ubunto on my son's pc.  He already had XP installed so I wanted to setup dual boot.  During the install I chose the advanced option for partitioning.  I resized the windows partition (don't remember if it was fat32 or ntfs).  Made about 20GB space for ubuntu with a 512MB swap.  After I commited the changes and the partitioning program did it's thing the windows partition was changed to type ext3.  Also the new / partition where super small (8MB).

At that point I knew something was wrong so I aborted the install and tried to boot windows with no luck.  I searched online for my problem and saw a thread where he simply changed the type back to NTFS.  I tried to do that first using my Acronis Disk Suite boot cd but still not booting windows (tried FAT32 and NTFS).  I put the drive in my windows PC and partition magic shows the drive as bad (not reading any partitions) I tried to run chkdsk and it said the file type was raw.

Here is what fdisk shows (ran from ubuntu live cd):

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14592   117210208+   7  HPFS/NTFS
/dev/hda2           14593       14593        8032+  83  Linux
/dev/hda3           14594       14594           0+  83  Linux


ubuntu@ubuntu:~$ sudo fdisk /dev/hda1

The number of cylinders for this disk is set to 14591.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Expert command (m for help): p

Disk /dev/hda1: 255 heads, 63 sectors, 14591 cylinders

Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 1 00   0   0    0   0   0    0          0          0 00
 2 00   0   0    0   0   0    0          0          0 00
 3 00   0   0    0   0   0    0          0          0 00
 4 00   0   0    0   0   0    0          0          0 00

Please help.  I would rather not re-install XP and all the programs.  It seems maybe it's a combination of getting the right partition type and fixing the partition table maybe??

Thanks...

---

### Post by dbova on 2006-09-11
Any ideas?

---

### Post by Jonie on 2006-09-11
If your partitions are not messed up physically, you can use Testdisk to restore them. GParted LiveCD is for example small live distro that includes it.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Or you can just start Ubuntu from CD and sudo apt-get install testdisk. Then launch it from terminal.

---

### Post by dbova on 2006-09-11
:D WOOHOOO... Thanks Jonie.  testdisk did the trick.  After using testdisk to analyze - search - then replace the NTFS boot sector with the backup boot sector the NTFS partition is restored.  Thank you very much for your advice.

---

