---
title: "Live CD created an unsafe  filesystem"
date: 2012-12-31
forum: Installation &amp; Upgrades
---

### Post by mringer on 2012-12-31
Lubuntu 12.04, installed from the live CD. Updated 2012-12-23.

But then:
```

sudo tune2fs -l /dev/sda2   #  root file system 
```
produced this output (cut) ```

Filesystem created:       Sat Dec 22 20:23:27 2012
Last mount time:          Mon Dec 31 09:29:56 2012
Last write time:          Sat Dec 22 20:40:57 2012
Mount count:              33
Maximum mount count:      -1
Last checked:             Sat Dec 22 20:23:27 2012
Check interval:           0 (<none>)  
```

This means that the filesystem will not be fsck'ed until an error
is detected. The man page ( tune2fs(8) ) strongly recommends against
these settings. I think that probably lots of people have
been installing live CDs and not getting any warning.

---

### Post by sudodus on 2012-12-31
How did you install Ubuntu?

What is the content of the file [FONT="Courier New"][SIZE="3"]/etc/fstab[/SIZE][/FONT] ? And what are your partitions?

Please post the output of the following commands:

```
sudo fdisk -lu
```
```
cat /etc/fstab
```

---

### Post by mringer on 2013-01-01
> **sudodus said:**
> How did you install Ubuntu?

As I said: I installed it off the live CD. It offered some options,
but I cannot remember which I selected.


> Please post the output of the following commands:


```

sudo fdisk -lu
[sudo] password for manager: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40017914    20008926    7  HPFS/NTFS/exFAT
/dev/sda2        40017915    59552954     9767520   83  Linux
/dev/sda3        59552955    75184199     7815622+  82  Linux swap / Solaris
/dev/sda4        75184200   234436544    79626172+  83  Linux

```

```

 cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=30c969c8-8299-4020-8ecc-bc228a671810 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=46d18e5f-1549-43b9-bd7b-560c091eb105 /home           ext3    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=367914b5-71fa-4e83-ad91-94647511ab22 none            swap    sw              0       0

```

---

### Post by sudodus on 2013-01-01
You are right!

The settings in /etc/fstab are correct for the partitions to be checked, but these settings shown by tune2fs are bad, if you want checking.

I just checked with three systems at home. One system was installed as Ubuntu 8.04 and upgraded via Ubuntu 10.04 and 12.04. This system has

```
Mount count:              10
Maximum mount count:      20
```

and it does check the partitions once in a while.

Another system was installed as Lubuntu 12.04 to a USB drive to be a portable system. Later on I also cloned it to the internal HDD of an old Thinkpad. This system has

```
Mount count:              92
Maximum mount count:      -1
```

and when I start thinking about it, it has not checked the partitions. The entry for the root file system in /etc/fstab indicates that there should be checking.

A third system was also installed as Lubuntu 12.04 but into a hard disk drive, when there was already another linux system there. This system has the following count settings

```
Mount count:              118
Maximum mount count:      -1
```

So obviously there is no file checking in that system either.

I think you have found a bug. Would you like to report it in launchpad?

---

### Post by mringer on 2013-01-07
> **sudodus said:**
>   [cut]
I think you have found a bug. Would you like to report it in launchpad?

Eventually I did so, but they did not agree that there is a bug.

---

### Post by sudodus on 2013-01-08
> **mringer said:**
> Eventually I did so, but they did not agree that there is a bug.
I see. Anyway I have changed it manually, so that I get checking in the Lubuntu systems now.

Thank you for sharing :KS

---

