---
title: "adding RAID 5 to dual boot"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by Pinocheckio on 2008-05-27
I made a ubuntu/windows xp pro dualboot without many problems, but when i added my RAID5 (3* 500GB), grub gave error 5. I can only boot to windows or ubuntu, disabling the array in BIOS and edit grub manually at post back from (hd4,0)--> (hd1,0) (ubuntu) and (hd3,0) --> (hd0,0) (windows)

I tried reinstalling ubuntu and at first he recognizes the 3 disks but when i begin formatting, he only can see 1, when i reboot i see the other 2 are offline... ( luckily i can rebuild the array)

So how can i make ubuntu see the whole array ( without having to reset my array)? It has not to be accessable from ubuntu (windows can see it without problems)or bootable, just to make grub satisfied.

thx

btw it's just software RAID, the intel ICH9R chipset

---

### Post by dstew on 2008-05-27
I believe what you have is called "FakeRaid", which is software-dependent hardware RAID. The BIOS can detect that the RAID exists, but cannot completely manage it.

If you use the dmraid program during a Live CD installation, you can get grub to recognize and boot from the RAID. I do not know how it works in Hardy, but with earlier distributions, since the Live CD installer program could not work with a FakeRaid, you had to install dmraid to the LiveCd system, and install the Ubuntu system "by hand". See the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto").

---

### Post by Pinocheckio on 2008-05-27
> **dstew said:**
> I believe what you have is called "FakeRaid", which is software-dependent hardware RAID. The BIOS can detect that the RAID exists, but cannot completely manage it.

If you use the dmraid program during a Live CD installation, you can get grub to recognize and boot from the RAID. I do not know how it works in Hardy, but with earlier distributions, since the Live CD installer program could not work with a FakeRaid, you had to install dmraid to the LiveCd system, and install the Ubuntu system "by hand". See the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto").

Booting from it is just what i don´t want, grub/ubuntu just have to know this array is there, that´s my problem.I find many howtos to install ubuntu on raid. i just want to add it, without rebuilding/formatting the array. i don´t know if it has to be on the grub/menu.lst, i don´t care really...
And if that´s completely impossible ( which i doubt) i will copy the files to my windows drive and rebuild it again I guess. But that is my last option

---

### Post by Pinocheckio on 2008-05-27
This is what dmraid says and yes (Data, the RAID5 array) seems broken, but that because i´m restoring it on windows.
At least it found something, don´t know what to do next though. :confused:

```
ubuntu@ubuntu:~$ sudo dmraid -ay
ERROR: isw device for volume "Data" broken on /dev/sdb in RAID set "isw_jeedjcdhh_Data"
ERROR: isw: wrong # of devices in RAID set "isw_jeedjcdhh_Data" [1/3] on /dev/sdb
ERROR: isw device for volume "Data" broken on /dev/sda in RAID set "isw_bcibfabhfg_Data"
ERROR: isw: wrong # of devices in RAID set "isw_bcibfabhfg_Data" [1/2] on /dev/sda
ERROR: device-mapper target type "raid45" not in kernel
ERROR: no mapping possible for RAID set isw_bcibfabhfg_Data
```

---

### Post by Pinocheckio on 2008-05-28
i just tried a lot of things , can anyone help set my menu.lst accordingly to:

```
jannes@Pinocheckio:~$ sudo fdisk -l
[sudo] password for jannes: 
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x4f35 of partition table 5 will be corrected by w(rite)
 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa36c0953
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       65270   524273242+   f  W95 Ext'd (LBA)
/dev/sda5   ?      147820      388020  1929405311   1f  Unknown
 
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16b216b3
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           1           0    0  Empty
Partition 1 does not end on cylinder boundary.
 
Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb5de1fe0
 
Disk /dev/sdc doesn't contain a valid partition table
 
Disk /dev/sdh: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91a191a1
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1       18240   146512768+   7  HPFS/NTFS
 
Disk /dev/sdi: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d320d33
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1        1216     9767488+  83  Linux
/dev/sdi2            1217        1459     1951897+  82  Linux swap / Solaris
/dev/sdi3            1460       10577    73240335   83  Linux
/dev/sdi4           10578       12401    14651280    b  W95 FAT32
```

sda/b/c is my raid array, but if they stay seperate disks to grub, its ok as long as i can boot ubuntu/windows

this is my current menu.lst:

```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd4,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6a703746-8584-4ae5-bb47-e6db953bea92 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd4,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6a703746-8584-4ae5-bb47-e6db953bea92 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd4,0)
kernel		/boot/memtest86+.bin
quiet

title		Other operating systems:
root

title		Microsoft Windows XP Professional
root		(hd3,0)
savedefault
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1


```

my dvd-player and writer are also connected with a SATA cable, don´t if that causes any problems.

I can only boot if i set sata controller to AHCI

---

