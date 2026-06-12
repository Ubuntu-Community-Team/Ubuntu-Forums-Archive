---
title: "Problems with Grub?"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by illy123 on 2010-01-01
I recently installed Ubuntu and thus am now dual booting it with W7 (which was installed first). These are the options I get with Grub:

Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)

I'm not sure if there is something wrong with this; why is there an option for Linux 16 and then for 14? At the moment I'm booting into Ubuntu using Linux 16.

I'm a sticker for looks and would prefer reducing it down just to: 

Windows 7
Ubuntu

Thanks a lot.

---

### Post by raymondh on 2010-01-01
> **illy123 said:**
> I recently installed Ubuntu and thus am now dual booting it with W7 (which was installed first). These are the options I get with Grub:

Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)

I'm not sure if there is something wrong with this; why is there an option for Linux 16 and then for 14? At the moment I'm booting into Ubuntu using Linux 16.

I'm a sticker for looks and would prefer reducing it down just to: 

Windows 7
Ubuntu

Thanks a lot.

Those are kernels.  It is suggested/recommended to have at least 2 kernel versions just in case your current one borks.

Some reading on how to re-configure grub2

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305](http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by illy123 on 2010-01-01
> **raymondh said:**
> Those are kernels.  It is suggested/recommended to have at least 2 kernel versions just in case your current one borks.

I see.

Thanks a lot :)

---

### Post by ywh842005 on 2010-01-01
[]("https://help.ubuntu.com/community/Grub2#Custom Menu Entries")> 
I'm a sticker for looks and would prefer reducing it down just to: 

Windows 7
Ubuntu


if you want to reduce the menuentry, this website may give you what you want
[https://help.ubuntu.com/community/Grub2#Custom](https://help.ubuntu.com/community/Grub2#Custom) Menu Entries

---

### Post by ywh842005 on 2010-01-01
This one is more clear
[https://wiki.ubuntu.com/Grub2#Removing](https://wiki.ubuntu.com/Grub2#Removing) Entries from Grub 2

---

