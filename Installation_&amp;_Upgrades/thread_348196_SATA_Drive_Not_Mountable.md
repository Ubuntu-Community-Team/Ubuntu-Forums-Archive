---
title: "SATA Drive Not Mountable"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by talking_walnut on 2007-01-28
Hi,

I recently moved my computer to a new case and reinstalled Ubuntu on it (to remove Windows completely). With my old setup my SATA drive was automatically picked up and mounted for me. Now however it isn't. It is still detected by Ubuntu and shows up under Places->Computers but if I double click on the icon I get ```

Unable to mount the selected volume.
error: device /dev/sda1 is not removable

error: could not execute pmount


```

Anybody any idea why this is happening? Here's the basic structure of my hard discs:
1x 20GB IDE drive containg OS, /home and swap on seperate partitions
1x 200GB SATA drive for files (SATA I I think)

My bios is detecting the drive during startup and displaying the correct size and other information.

Also, I didn't have the drive connected at the time of installing Ubuntu if that makes a difference

---

### Post by chalex on 2007-01-28
What does 'sudo fdisk -l' show?

What does your /etc/fstab look like?

---

### Post by talking_walnut on 2007-01-28
sudo fdisk -l gives me 
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    c  W95 FAT32 (LBA)

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            2332        2434      827347+  82  Linux swap / Solaris
/dev/hda2               1         262     2104483+  83  Linux
/dev/hda3             263        2331    16619242+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40000536576 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4863    39062016    c  W95 FAT32 (LBA)

```

And my fstab looks like this 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

So fdisk is detecting it but its not in /etc/fstab. Could this be the only problem? Can anyone give me the correct parameters to add if it is? It's been a while since I had to edit my fstab and its been a long day :)

---

### Post by taurus on 2007-01-28
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by talking_walnut on 2007-01-28
Ya. Got it. I should really have known better but it's been a while since I used Linux. Thanks for your help guys

---

