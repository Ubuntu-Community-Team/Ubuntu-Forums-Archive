---
title: "PXE network install fails writing to local HDD"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by ukoda on 2008-04-26
I have set up a copy of 8.04 on my server so I can network boot, via PXE, run and install much the same as with the standard desktop CD.  Most of it works.  I can get PCs boot in to the standard Ubuntu desktop that appears like you see from the CD and it works well as a workstation.  However when I run the Ubiquity installer from the desktop icon and it goes fine till the point where it is copying to the local hard drive.  It creates the files systems and someone of the directories then just disappears.  The last few lines of the log show:

Apr 26 09:59:28 ubuntu ubiquity[14232]: switched to page stepReady
Apr 26 09:59:46 ubuntu ubiquity[14232]: Step_before = stepReady
Apr 26 09:59:46 ubuntu ubiquity[14232]: progress_loop()
Apr 26 10:00:06 ubuntu kernel: [ 6283.181521] Adding 1413680k swap on /dev/sda5.  Priority:-2 extents:1 across:1413680k
Apr 26 10:00:07 ubuntu partman: mke2fs 1.40.8 (13-Mar-2008)
Apr 26 10:00:31 ubuntu kernel: [ 6307.643711] kjournald starting.  Commit interval 5 seconds
Apr 26 10:00:31 ubuntu kernel: [ 6307.650350] EXT3 FS on sda1, internal journal
Apr 26 10:00:31 ubuntu kernel: [ 6307.650372] EXT3-fs: mounted filesystem with ordered data mode.
Apr 26 10:00:39 ubuntu ubiquity: /usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
Apr 26 10:00:39 ubuntu ubiquity:   warnings.warn("apt API not stable yet", FutureWarning)
Apr 26 10:00:39 ubuntu ubiquity: /usr/lib/ubiquity/localechooser/post-base-installer: 49: cannot create /target/etc/default/locale: Directory nonexistent
Apr 26 10:00:39 ubuntu ubiquity: umount: /target/cdrom: not mounted
Apr 26 10:00:39 ubuntu ubiquity: grep: 
Apr 26 10:00:39 ubuntu ubiquity: /target/etc/apt/sources.list
Apr 26 10:00:39 ubuntu ubiquity: : No such file or directory

I'm not too familiar with the what the install process does behind the scenes so I'm not too sure what to look at next.  I welcome suggestions.  For completeness this the fstab I'm currently using:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
192.168.1.2:/tmp       /target       nfs   noauto,user
proc            /proc           proc    defaults        0       0
/dev/nfs        /               nfs     defaults        1       1
none            /tmp            tmpfs   defaults        0       0
none            /var/run        tmpfs   defaults        0       0
none            /var/lock       tmpfs   defaults        0       0
none            /var/tmp        tmpfs   defaults        0       0

The /target entry is so I can mount something there when needed as the installer sometimes balks that it can't unmount /target even when it's got nothing mounted there.  At the time it falls over it has /dev/sda1 on /target.

---

