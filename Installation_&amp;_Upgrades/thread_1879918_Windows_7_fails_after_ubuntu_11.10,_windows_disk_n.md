---
title: "Windows 7 fails after ubuntu 11.10, windows disk no help."
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by heaviside on 2011-11-12
Cleared partition space to FAT 32 in windows. Installed Ubuntu into this new space with no issues. 
Windows 7 now fails to boot. 

Windows error "The boot selection failed because a required device is inaccessible"

I have made a bootable usb of windows 7. It does not see my hard drive. It saw my hard drive in the past before installing Ubuntu (I re-installed windows previously).

Using boot repair I...
[INDENT] Re-installed grub. No help.
Restored mbr. No help.[/INDENT]

Tried sudo update-grub2 obtained:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda3
done
```

No help.

Ran sudo fdisk -l obtained the following:
```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x81c019ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
/dev/sda2            2048      409599      203776   42  SFS
/dev/sda3   *      409600  1011064831   505327616   42  SFS
/dev/sda4      1011066878  1250263039   119598081    5  Extended
/dev/sda5      1011066880  1246343167   117638144   83  Linux
/dev/sda6      1246345216  1250263039     1958912   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 2005 MB, 2005925888 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3917824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfb7ef801

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```

Any suggestions? I need windows 7 for work.

---

### Post by darkod on 2011-11-12
What does "cleared partition space to FAT32 in windows" mean? You need unallocated space to install, not any type of partition created from windows. When preparing to install linux, forget about creating partitions from windows (unless we are talking about shrinking the windows partition which is always best to be done from windows).

Anyway, do you know why are sda1, sda2 and sda3 SFS type? Win7 would usually be installed on ntfs.

From live mode you can follow the link in my signature and run the bootinfoscript. It will include more info. You can post the results here, if copying the text please do it in code tags as explained in that link, it's easier for reading.

---

### Post by oldfred on 2011-11-12
SFS is dynamic partitions. In Windows you tried to create more than the allowed 4 primary (basic in Windows) partitions and it converts to dynamic not one extended with many logical partitions. Linux does not work with dynamic partitions and some Windows repairs do not work with dynamic partitions.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work. Not sure how it works when you have both the dynamic & an extended partition. Be sure to have good backups.

Several users have used this, it has a liveCD download to use:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

---

### Post by heaviside on 2011-11-13
Thanks oldfred

Can't change it back to regular partitions as there are now linux partitions. That was probably where the problem came from. Plan on just doing a wipe of that area and re installing windows into a fresh partition.

There should be a warning about how you have to change dynamic partitions back to normal, but well that's life eh?

---

### Post by Mark Phelps on 2011-11-13
> **heaviside said:**
> There should be a warning about how you have to change dynamic partitions back to normal, but well that's life eh?

Why? YOU changed them into Dynamic Disks -- because you didn't know what you were doing.  

Windows will then work FINE with Dynamic Disks. It has no reason to generate any warnings.

How would Ubuntu know what you did when inside Windows?

---

### Post by heaviside on 2011-11-15
Ubuntu can see sfs style partitions (see  fdisk -l)

Something on the website on their directions to installing beside windows, or when installing would have been nice. I knew my partitions were dynamic (the computer came that way, thanks HP); however, did not know what that meant to grub.

I'm simply saying that since one can eaisly see the issue, a warning would be NICE. I didn't say it was necessary, nor did I blame the lack of warning for my problem. I had to do a clean windows install, and I think it would be nice for others to avoid such an operation.

---

### Post by oldfred on 2011-11-15
The SFS partitions are the underlying physical partitions, where the dynamic means some data may be written in logical partitions that cross the physical boundaries. Very similar to LVM in Linux. But Linux does not have the driver to match the proprietary dynamic file system logic. 

We have had some try Windows repairs on dynamic partitions and they have not worked. Do not know if that is always the case or not.

---

