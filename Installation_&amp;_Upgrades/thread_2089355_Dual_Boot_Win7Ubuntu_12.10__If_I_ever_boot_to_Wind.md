---
title: "Dual Boot Win7/Ubuntu 12.10:  If I ever boot to Windows, Ubuntu stops working"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by chetlin on 2012-11-29
Hi,

I recently got a laptop with Windows 7 pre-installed on it.  I used the tool to install Ubuntu and make it so I could boot to either operating system when I turn the laptop on.  If I choose Ubuntu everything works fine.  However, if I ever boot to Windows, then later try to boot to Ubuntu, the first time I get a bunch of garbage displayed, then any time after that (after turning the computer off and on) I always get the error: "attempt to read or write outside of disk 'loop0' " and then it will never actually boot to Ubuntu.  The only way I was ever able to fix this was to go into Windows and re-install Ubuntu, which starts me off with a "clean slate" (everything from Ubuntu is deleted).

This is, of course, not very practical for a dual-boot.  Does anyone know what's going on here who could help me try to fix this problem?

Thank you very much!

---

### Post by sudodus on 2012-11-29
Hi chetlin,

Welcome to the Ubuntu Forums :-)

The expression 'loop0' makes me think of a wubi install rather than dual boot.

Please run the following commands when in Ubuntu:

```
sudo fdisk -lu
```

```
df
```

and post the output of the commands in a reply!

Please put the output between code tags like this

[noparse]```
output
```[/noparse]

to get output like this
```
output
```

---

### Post by chetlin on 2012-11-29
Hi!

Yeah, that word "Wubi" does sound familiar.  Sorry, I don't know too much about this stuff, all I know is I'm more comfortable doing my school work on a Linux operating system and this seemed like the best way to do it.

Here is the outcome of those commands:

```

brian@ubuntu:~$ sudo fdisk -lu
[sudo] password for brian: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf7e19e97

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920    39022591    19470336    7  HPFS/NTFS/exFAT
/dev/sda3        39022592   976764927   468871168    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf7e19d5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    16775167     8386560   84  OS/2 hidden C: drive

brian@ubuntu:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/loop0      21563149  3339613  18223536  16% /
udev             2974208        4   2974204   1% /dev
tmpfs            1193364      908   1192456   1% /run
none                5120        0      5120   0% /run/lock
none             2983404      496   2982908   1% /run/shm
none              102400       44    102356   1% /run/user
/dev/sda3      468871164 45447760 423423404  10% /host

```

Thanks!

---

### Post by Bucky Ball on 2012-11-29
Welcome to the forums. 

Yep, it's a Wubi install if you've 'gone back into Windows and reinstalled Ubuntu.' This is not a dual-boot. That is when they are installed on separate partitions. Wubi is a 'try before you buy' scenario and not a permanent solution ... ;)

---

### Post by sudodus on 2012-11-29
> **chetlin said:**
> Hi!

Yeah, that word "Wubi" does sound familiar.
... ```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf7e19e97

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920    39022591    19470336    7  HPFS/NTFS/exFAT
/dev/sda3        39022592   976764927   468871168    7  HPFS/NTFS/exFAT
...
brian@ubuntu:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/loop0      21563149  3339613  18223536  16% /
...
/dev/sda3      468871164 45447760 423423404  10% /host

```

Thanks!
Yes, you have a wubi system installed in a file system inside a file in the Windows NTFS file system. This kind of system is good for testing, but not at all as stable as a real dual boot system.

A dual boot system is a system where Ubuntu has an own partition for its file system, side-by-side with the NTFS file system.

1. This means that you need to edit the partitions (and file systems) on the hard disk drive. This is risky, so I suggest to make a complete backup copy of the HDD, an image that is saved to an external HDD (typically a USB or eSATA drive). You can make such a copy with ***Clonezilla*** (also free linux software to be downloaded).

At least you should have a copy of the recovery partition(s) for Windows and copies of all your personal files (documents, pictures, video clips ...).

2. Then you can select dual boot instead of wubi. ***Boot the computer from the Ubuntu install CD/DVD/USB drive and select install alongside windows***. Part of the big NTFS partition will be deleted and made into a linux partition with the ext4 file system and a small swap partition.

Just follow the instructions in the graphical wizard.

---

### Post by oldfred on 2012-11-30
Is the sdb a SSD with Intel Smart Response? That complicates it and may be why wubi is having issues. SRT seems to use some sort of RAID to use SSD with Windows.

       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

   You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

