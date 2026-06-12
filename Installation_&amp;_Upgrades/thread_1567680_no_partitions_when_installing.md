---
title: "no partitions when installing"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by andrei4002 on 2010-09-04
hello, i'm trying to install ubuntu 10.04 x86-64 on my laptop

my current partitioning system looks like this:

1 primary ntfs partition 45 gb
1 extended with 2 ntfs partitions (100/150 gb) and 20 gb of free space)

the ubuntu installer sees this:

32k free space at the beginning
208 mb ( windows 7loader)
320 gb /dev/sda1
140 mb freespace

im booting from a usb drive, and i have ahci on in my bios

tried booting on ide/ahci-same results

the disk utility that comes with ubuntu sees the partitions correctly

tried installing on another laptop, partitions were seen correctly from install partitioner

i'm out of ideas.. pls help

---

### Post by srs5694 on 2010-09-04
Launch a text-mode shell and post the output of the following command:

```

sudo fdisk -lu

```

Please post the output between a "[noparse]```
[/noparse]" and a "[noparse]
```[/noparse]" string to improve legibility. Thanks.

---

### Post by Rubi1200 on 2010-09-04
Did you try defragmenting on the Windows side and using chkdsk before attempting the Ubuntu install?
It is also advisable to use the built-in disk  management tool in Windows 7 to shrink the drive.

---

### Post by andrei4002 on 2010-09-04
thanks for reply

here's some pictures of what things look like while running the live cd

[[IMG]http://img823.imageshack.us/img823/2536/screenshotnr.th.png[/IMG]](http://img823.imageshack.us/i/screenshotnr.png/)

[[IMG]http://img822.imageshack.us/img822/1623/screenshot1rv.th.png[/IMG]](http://img822.imageshack.us/i/screenshot1rv.png/)

[[IMG]http://img337.imageshack.us/img337/1979/screenshot2ts.th.png[/IMG]](http://img337.imageshack.us/i/screenshot2ts.png/)



and here's the output of fdisk -lu


```

ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfa1f8376

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    94381874    47190906    7  HPFS/NTFS
/dev/sda2        94381875   625137344   265377735    5  Extended
/dev/sda5        94381938   304110449   104864256    7  HPFS/NTFS
/dev/sda6       304110513   584846324   140367906    7  HPFS/NTFS

Disk /dev/sdc: 4002 MB, 4002910208 bytes
124 heads, 62 sectors/track, 1016 cylinders, total 7818184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3c7c4439

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     7807589     3903763+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 2)
Partition 1 has different physical/logical endings:
     phys=(485, 254, 63) logical=(1015, 68, 54)
Partition 1 does not end on cylinder boundary.
/dev/sdc2         7807590     7807652          31+  21  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(486, 0, 1) logical=(1015, 68, 55)
Partition 2 has different physical/logical endings:
     phys=(486, 0, 63) logical=(1015, 69, 55)
Partition 2 does not end on cylinder boundary.


```

---

### Post by srs5694 on 2010-09-04
I think the problem is that the disk appears to use a Master Boot Record (MBR) partitioning scheme, but there's leftover data from an earlier use of the disk with the GUID Partition Table (GPT) system. Windows favors MBR in such situations, but the Ubuntu installer may be using the GPT data. Was the disk ever used with GPT -- say, in a Macintosh? If you have reason to believe I'm wrong in this diagnosis, post back for more advice. I'm about to suggest a change that could be dangerous if my diagnosis is incorrect....

If I'm right, you'll need to erase the obsolete GPT data. You can do this with my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) utility. I recommend you use the latest version by booting the Ubuntu installer into its "live CD" mode, downloading the appropriate .deb file for your architecture from [its Sourceforge download page](https://sourceforge.net/projects/gptfdisk/files/) and double-clicking it. (Alternatively, and more easily, you can type "sudo apt-get install gdisk" to install it, but this will install a pretty old version with several known bugs.) To wipe the errant GPT data, follow these steps:


[list=1]
[*]Launch gdisk on the disk by typing "sudo gdisk /dev/sda". It will probably complain that it's found both MBR and GPT data and ask which it should use. Choose either; it doesn't matter which you'll use, given what you're about to do.
[*]Type "x" to enter the experts' menu.
[*]Type "z" to "zap" (destroy) the GPT data.
[*]Type "y" to confirm you want to destroy the GPT data.
[*]*Type "n" when asked if you want to blank out the MBR.* If you type "y" here, you'll destroy your MBR partition table, so be very very careful at this step!
[/list]


In theory, you should now be able to install Ubuntu. (You'll still have to shrink some partition(s) to make room, but the installer should be able to do that.) To be sure the system is using the new partition table, it won't hurt to reboot before you do this.

---

### Post by andrei4002 on 2010-09-05
yes, thank you, that was indeed the problem

---

### Post by srs5694 on 2010-09-05
Glad to have helped. FWIW, I've been seeing this problem reported more and more frequently recently. I've therefore added [this page](http://www.rodsbooks.com/gdisk/wipegpt.html) to my GPT fdisk documentation, describing the issue and the corrective procedure in more detail. I mention this in case somebody reading this thread wants more detail, or wants to provide a quick link to a fix to others in the future.

---

