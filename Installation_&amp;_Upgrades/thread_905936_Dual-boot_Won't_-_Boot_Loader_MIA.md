---
title: "Dual-boot Won't - Boot Loader MIA"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by mxcrowe on 2008-08-30
I just put together a new system for my daughter (EVGA e7050/610i; e2200; 2x1GB OCZ RAM; 2 80G IDE hard drives) and installed Windows XP first.  Then I installed Ubuntu 8.04.1 with the hopes of dual-booting the machine.  XP lives on the C: drive (Disk 0).  I split the second drive (D:, Disk 1) into 2 partitions during the Ubuntu install, so that there is a ~40GB NTFS partition, plus space for Linux.  Ubuntu made a 36gb partition plus a 1.6GB swap partition.  All this shows up in the disk management console from XP.
The install of Ubuntu went fine, but when I boot the system, it provides me with no boot menu and XP loads automatically.  Can anyone tell me how to modify things so that I can choose to boot to Ubuntu or XP?

---

### Post by Pumalite on 2008-08-30
If you are installing in different drives; search: Dualboot Two Hard Drives in this Forum.
If not; post:
sudo fdisk -lu
(Boot your Live CD)

---

### Post by cdtech on 2008-08-30
Boot into the Live CD.

When you get to the desktop open a terminal and enter:
```
sudo grub
```
This will give you a "grub" prompt, type:
```
$ grub > find /boot/grub/stage1
```
This will return the location of the stage1 file. Whatever was returned from the find command use it in the next command:
```
$ grub > root (**hd?,?**)
```
Again use the value from the find command i.e. if find returned (**hd0,1**) then you would enter root (**hd0,1**)
Next enter the command to install GRUB to the MBR (of the primary drive):
```
$ grub > setup (**hd0**)
```
This installs GRUB to the MBR of the primary drive (hd0).
Exit grub:
```
$ grub > quit
```

---

### Post by mxcrowe on 2008-08-30
Thanks guys.  I followed all the above advice.  First I went thru the grub exercise using Live CD, then after reviewing other posts, went into BIOS and switched the HD boot order.  That gives me the boot menu and both O/S's show up.  Thanks for the help!!

---

