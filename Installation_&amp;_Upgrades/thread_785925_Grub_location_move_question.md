---
title: "Grub location move question"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by Ryandor on 2008-05-07
I am currently booted to Xubuntu 8.04 Live CD, performing an install. I have four drives formated NTFS that I would prefer not to modify as I'd rather not have to restore from backups. It's all data (movies, music, documents). I'd just like to have them mounted as shares from the get-go.

The four NTFS drives show up as hde, hdf, hdg, hdh; these are on a Highpoint IDE card (HPT302; not RAID capable). These I have set as /vol1, /vol2, /vol3, /vol4 in setup.

I have two other IDE drives I am performing the actual install on. These are attached to the motherboard IDE channels.
sda, sdb
I've set these as sda1 as /, sda2 as /swap, sdb1 as /home and sdb2 as /var

My fdisk -l is listed below, but the installer has not finallized it yet.

I'm on the last step (7) of the install and noticed in the Advanced Options that the Boot Loader (I assume Grub) is defaulting to (hd0).

My questions:
Is this one of the ntfs drives, and why would it put it there?
Can I change it to sda with no ill effects (or would sda1 be better), or does it even matter?

I am under the assumption that I can't actually boot from those drives attached to the IDE PCI Card, and need to change it to the sda drive. The IDE card is a HPT302, which is lacking any type of bootable features as far as I know. I just want to make sure the system will boot once the install is complete. I've stepped on a few Grubs before and would prefer not to get a Error 21.

Thank you for any insight.

-Ryandor


```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hde: 102.9 GB, 102935347200 bytes
255 heads, 63 sectors/track, 12514 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf42af42a

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1       12514   100518673+   7  HPFS/NTFS

Disk /dev/hdf: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa1944633

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1       24792   199141708+   7  HPFS/NTFS

Disk /dev/hdg: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05b837a1

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               1       19452   156248158+   7  HPFS/NTFS

Disk /dev/hdh: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/hdh1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb70cb70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2482    19936633+   7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122941242880 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc1862277

Disk /dev/sdb doesn't contain a valid partition table


```

---

### Post by unutbu on 2008-05-07
(hd0) is /dev/sda, so you should be okay.

---

### Post by Ryandor on 2008-05-07
Thank you for the quick reply.
I've hit "finsh" and it's installing now. I'll post back once rebooted.
-Ryandor

---

### Post by Ryandor on 2008-05-08
Just a followup.
It appears I have other issues with this computer in general, as I it was unable to finishing partitioning the sda drive. Looks like a failed drive. Rebooting and watching the console gives a ton of I/O errors on sda.  So much for that this time around.

Thanks for the answer anyway, and will consider it when I do get working hardware.

-Ryandor

---

