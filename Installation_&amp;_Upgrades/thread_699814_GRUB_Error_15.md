---
title: "GRUB Error 15"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by tguellich on 2008-02-17
I am attempting to install Ubuntu on an IBM Thinkpad T40.  The hard drive was wiped with Gparted and two partitions were added and formatted in ext3.  When I boot, the disk starts then gives a GRUB Error 15.  Can anyone help me out with this?  Is there a FAQ somewhere with all the GRUB errors?  Thanks.

---

### Post by dstew on 2008-02-17
[Here]("http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors") is a list of grub errors, but I don't think that will help much. Does the error message have any explanation (like Error 15, file not found) or is it just the error number without any explanation?

---

### Post by tguellich on 2008-02-17
It is just the error without any explanation.  I went back in with Gparted and removed the ext3 and just left it unallocated, now I get Error 22.  But thanks for the list, I will dig in and see if I can figure anything out.

---

### Post by dstew on 2008-02-17
A grub error without any explanation is a stage1.5 error. That means that grub will need to be re-installed. You cannot fix this type of error by editing the /boot/grub/menu.lst file.

To re-install grub, see [this]("http://ubuntuforums.org/showthread.php?t=224351").

---

