---
title: "Major Major Boot Error"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by 31337 on 2006-09-30
After installing ubuntu I got this message.
__________________________________________________

GRUB Loading stage1.5
GRUB loading, please wait.....
Error 17
_
__________________________________________________

Can someone help with this please. It does not do anything but just show this screen and go no-where. It will be greatly appreciated.

---

### Post by crazymonkey on 2006-09-30
> **31337 said:**
> After installing ubuntu I got this message.
__________________________________________________

GRUB Loading stage1.5
GRUB loading, please wait.....
Error 17
_
__________________________________________________

Can someone help with this please. It does not do anything but just show this screen and go no-where. It will be greatly appreciated.

> Error 17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

How did you install? Did you use the Desktop cd or the alternate using LVM? Do you have a Windows partition? Do you use sata/SCSI disks?

---

### Post by louieb on 2006-09-30
This is a common problem. Do a google search for
> grub error 17 
(See my signature) You will find the answer to your problem a hundred times.

---

