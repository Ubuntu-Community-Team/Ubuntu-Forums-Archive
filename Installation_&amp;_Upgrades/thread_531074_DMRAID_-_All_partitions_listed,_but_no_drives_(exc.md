---
title: "DMRAID - All partitions listed, but no drives (except / ) mounted... Almost there!"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by neuralnet on 2007-08-21
Hi, 

I've been following these guides;

[FakeRaidHowto - Wiki]("https://help.ubuntu.com/community/FakeRaidHowto")
[Successful and "easy" install DUALBOOT FeistyFawn/XP with nvdia raid0 stripeset]("http://ubuntuforums.org/showthread.php?t=464758")
[Re: Doesn't boot XP or FF 7-04 raid0 - completely stuck]("http://ubuntuforums.org/showpost.php?p=2782560&postcount=6")

in my attempt to install Ubuntu Feisty on to an existing RAID 1 array (2x300Gb Maxtor Drives, VIA onboard SATA controller, Gigabyte Mobo) with Windoze installed, I've mainly followed instructions of the second link above and ALMOST have the setup I need. The problem is that ALL the partitions on both drives of the array showed up in 'Computer', i.e. 14.8 GB Volume, 14.8 GB Volume (2), 19.5 GB Volume, 19.5 GB Volume (2), etc etc however - none are mounted. If I double click on them, they are mounted independently as /media/disk and not as an array. 

My fstab looked like this;

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/via_dacbccejae2 /               ext3    defaults,errors=remount-ro  0      1
/dev/mapper/via_dacbccejae3 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

So I've added;

```
/dev/mapper/via_dacbccejae1 /media/winroot	ntfs    defaults,rw,user,errors=remount-ro 0       1
/dev/mapper/via_dacbccejae4 /media/storage	ntfs	defaults,rw,user,errors=remount-ro 0       1
```

and whilst 'winroot' and 'storage' show up in file browser, when I double click I get told;

```
Unable to mount the selected volume.
mount: /dev/mapper/via_dacbccejae4 already mounted or /media/storage busy
mount: according to mtab, /dev/mapper/via_dacbccejae4 is already mounted on /media/storage
```

Hmmm, not quite right! I'm a bit a Linux newbie but I'm learning fast :) Assistance gratefully received !

Thanks.

---

### Post by neuralnet on 2007-08-21
As I said above, If I double click the drive icon in 'computer' I get the error;

```
Unable to mount the selected volume.
mount: /dev/mapper/via_dacbccejae4 already mounted or /media/storage busy
mount: according to mtab, /dev/mapper/via_dacbccejae4 is already mounted on /media/storage

```

if I navigate to /media/winroot or /media/storage & click the icon I get told;

```
The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "winroot".

```

Where am I going wrong ?

---

### Post by neuralnet on 2007-08-21
OK... I now have both NTFS partitions mounted.. after some googling my fstab now looks like this;

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/via_dacbccejae2 /               ext3    defaults,errors=remount-ro 0       1
/dev/mapper/via_dacbccejae3 none            swap    sw              0       0
/dev/mapper/via_dacbccejae1 /media/winroot	ntfs    noauto,users,ro,umask=0,	1	0
/dev/mapper/via_dacbccejae4 /media/storage	ntfs	noauto,users,ro,umask=0,	1	0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

and I am very happy :D 

The only thing I need do now is hide the unmounted partitions in the file browser.. Anyone ?

---

### Post by neuralnet on 2007-08-21
Forgot to add to the last post that I had to set the mount points (/media/storage) to read-write, from the default read only;

```

chmod a+rw /media/<mount point>

e.g.
chmod a+rw /media/winroot
chmod a+rw /media/storage
```

I managed to hide all the /dev/sda1 /dev/sda2 etc etc devices using this damned handy script

[Re: How to do you hide unmounted volumes? (Feisty Fawn)]("http://ubuntuforums.org/showpost.php?p=2605508&postcount=34")

and I'm a very happy geek.

---

