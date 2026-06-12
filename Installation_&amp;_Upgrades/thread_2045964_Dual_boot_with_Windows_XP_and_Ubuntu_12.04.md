---
title: "Dual boot with Windows XP and Ubuntu 12.04"
date: 2012-08-22
forum: Installation &amp; Upgrades
---

### Post by mummasboy on 2012-08-22
Hi, I have installed Ubuntu 12.04 along side my Windows XP. But I am unable to boot from Windows XP, only Ubuntu is working. Every time I choose the option Windows XP from the first boot window; a blank screen appears and I get returned to boot window showing the options. My partition specs are as,-

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6c5b6c5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS/exFAT
/dev/sda2        81915496   312560639   115322572    f  W95 Ext'd (LBA)
/dev/sda5        81915498   140393327    29238915    7  HPFS/NTFS/exFAT
/dev/sda6       163830933   245746304    40957686    7  HPFS/NTFS/exFAT
/dev/sda7       245746368   312560639    33407136    7  HPFS/NTFS/exFAT
/dev/sda8       140394496   161753087    10679296   83  Linux
/dev/sda9       161755136   163829759     1037312   82  Linux swap / Solaris

Partition table entries are not in disk order.
Please tell me what is wrong.
Thanks.

---

### Post by oldfred on 2012-08-23
If grub has the menu entry that is good as then most of XP's boot files are there and it can mount & read partition.

Post this to see if there are any XP issues we can see, but usually it then is just a Windows issue that may need chkdsk and/or fixBoot from a Windows installCD's repair console.

Post link from BootInfo:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by mummasboy on 2012-08-24
> **oldfred said:**
> If grub has the menu entry that is good as then most of XP's boot files are there and it can mount & read partition.

Post this to see if there are any XP issues we can see, but usually it then is just a Windows issue that may need chkdsk and/or fixBoot from a Windows installCD's repair console.

Post link from BootInfo:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Thank you for the info. I will look out for it.

---

