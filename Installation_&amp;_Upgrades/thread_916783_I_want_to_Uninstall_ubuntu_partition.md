---
title: "I want to Uninstall ubuntu partition"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by iampriteshdesai on 2008-09-11
I have installed Ubuntu 8.04 using the guided partition but now I want to uninstall it because I received Ubuntu Ultimate DVD. Now I am not so techy and don't know hot to partition and now I want to erase that partition. I have to be carefull since I have installed Ubuntu besides Windows on same drive. Plz help me. Is there any software which can help me wipe out Ubuntu from Windows I'll be glad.

---

### Post by caljohnsmith on 2008-09-11
If you just want to install the Ubuntu Ultimate over your current Ubuntu install, you should be able to do it during installation; just choose the current Ubuntu partition and have Ubuntu Ultimate format it to ext3 and use that partition as Ubuntu Ultimate's root mount point "/". Or if Ubuntu Ultimate doesn't allow you to do that, you can always manually format your Ubuntu partition to ext3 with gparted:
```
gksudo gparted
```
Keep in mind that as soon as you format your current Ubuntu partition, you will lose Grub on start up until you install Ubuntu Ultimate. If you need more help or details, please post the output of:
```
sudo fdisk -lu
```

P.S. I've heard some less-than-positive things about Ubuntu Ultimate. Are you sure you want to install it?

---

### Post by iampriteshdesai on 2008-09-11
Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeccaecca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    29431079    14715508+   7  HPFS/NTFS
/dev/sda2        29431080   156344579    63456750    f  W95 Ext'd (LBA)
/dev/sda5        72083718   156344579    42130431    7  HPFS/NTFS
/dev/sda6        50604876    71071559    10233342   83  Linux
/dev/sda7        71071623    72083654      506016   82  Linux swap / Solaris
/dev/sda8        29431206    49608719    10088757   83  Linux
/dev/sda9        49608783    50604749      497983+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5f4fd0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    78220484    39110211    7  HPFS/NTFS
iampriteshdesai@Pritesh:~$

---

