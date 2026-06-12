---
title: "Help! Clean install, no grub, manual restore won't work"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by npwhite on 2008-08-18
Had a perfectly stable dual boot XP/Hardy going for about a week. I had to re-install Windows. When trying to add grub back to the MBR, I encountered some errors (unfortunately I didn't log them), so I opted to do a clean Ubuntu install as well. 

Now after the clean install, the system still boots straight to Windows, even if I manually switch the boot order in the BIOS. 

In grub:
* "find /boot/grub/stage1" turns up "Error 15: File not found"

root (hd0,0)           
root (hd0,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/grub/stage2 /grub/menu.lst"... succeeded

and it still doesn't work. Any help is much, much appreciated!!

fdisk info below...



Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00051088

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          24      192748+  83  Linux
/dev/sda2              25        3063    24410767+  83  Linux
/dev/sda3            3064       91201   707968485   83  Linux

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c188c18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-08-18
First of all, when you say it boots straight into Windows, do you see the Grub message on startup saying "press ESC for menu" or something like that? Or does it truly boot straight into Windows? 

Please boot a Live CD, open a terminal, do the following and post the results:
```
sudo mount /dev/sda1 /mnt
cat /mnt/grub/menu.lst
```
That should print your menu.lst based on the info you gave. Also for completeness do the following:
```
sudo grub
grub> geometry (hd0)
grub> geometry (hd1)
grub> find /grub/stage1
```
And again, post the results.

---

