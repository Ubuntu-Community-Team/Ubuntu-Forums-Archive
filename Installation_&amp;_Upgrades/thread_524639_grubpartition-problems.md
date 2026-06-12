---
title: "grub/partition-problems"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by i386DX on 2007-08-13
I have a dual-boot system (windows 2000 <-> Ubuntu) Today I reinstalled Windows (formatted the partition and installed Windows 2003).

Windows-setup had overwritten the MBR so I tried to reinstall grub like I always do:
grub
find /boot/grub/stage1
root (hd0,6)
setup (hd0)

but now I get an error 22: No such partition

```

Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0)  (hd0)1+17 p (hd0,6)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: no such partition

```

In Gparted  /dev/hda is empty (unallocated) and does not find any partitions, however they exists. 
The XUbuntu livecd sees them and I can open them.

---

### Post by merlinus on 2007-08-13
Post results of:

```

sudo fdisk -l

```

-merlin

---

### Post by i386DX on 2007-08-13
```

i386dx@i386DX:~$ sudo fdisk -l
Password:

Schijf /dev/hda: 163.9 GB, 163928604672 bytes
255 koppen, 63 sectoren/spoor, 19929 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/hda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/hda2            5223       19929   118133977+   f  W95 Uitgeb. (LBA)
/dev/hda3           10444       19929    76196263+   b  W95 FAT32
/dev/hda5            5223        5302      642537   82  Linux wisselgeheugen
/dev/hda6            5303       10443    41295051   83  Linux

Schijf /dev/hdb: 122.9 GB, 122942324736 bytes
255 koppen, 63 sectoren/spoor, 14946 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/hdb1   *           1       14946   120053713+   7  HPFS/NTFS


```

I played a bit around in fdisk (with the bootable flag) and when I executed the find-command in grub it said hd0,5 in stead of hd0,6. I was able to reinstall grub using hd0,5. 
Now grub is loaded on boot, and I can choose Windows.
When I choose Ubuntu I get the error 22. However when i edit the bootoptions in grub for Ubuntu and I change root (hd0,6) to root  (hd0,5) it works perfectly.
Solved for me, but strange the 6 became a 5 just by formatting an partition that already exists

---

### Post by merlinus on 2007-08-13
Numbering for these things begins at zero, not 1, so (hd0,5) is correct.

ubuntu is on partition six of hard disk one.

-merlin

---

