---
title: "Grub does not install after adding partition"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by .kARoshi on 2006-06-28
I recently edited my second hard drive partition to have space for a little 5 gb partition.
My setup was initially as follow:
sda:
sda1: ntfs - windows xp
sda2: extended
sda5: ntfs - data

sdb:
sdb1: fat32 - data
sdb2: extended
sdb5: ext3 - ubuntu dapper

I had grub installed on sda's MBR. and booted everything with no prob.
I added a small 5gb partition before sdb5, therefore making the linux partition sdb6. Of course grub refused to work and i decided to reinstall it using an ubuntu live cd.  I issued the following commands:

```

grub *entering the grub shell*
grub> root (hd1,5)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd1,5)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

```

Thus installing it in the first mbr. The problem is that if i boot from the first drive the bios tells me that the disk is not bootable and to insert a bootable media, leading me to think that grub's install was not successful. 
Please, i have no clue on what to do next. Thanks in advance.

---

