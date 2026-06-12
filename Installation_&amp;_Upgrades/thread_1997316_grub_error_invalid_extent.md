---
title: "grub error: invalid extent"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by thegameking on 2012-06-05
Okay, so i have a hp pavilion pc whose sata drives do not work. I also have a 2TB seagate external hard disk lying around. So I decided use whats left of the pc and the hard disk to install ubuntu 12.04LTS 64bit version on it. The error message I get is:

error: invalid extent
grub rescue>

I used the live usb and installed boot repair and got this:
[http://paste.ubuntu.com/1024434/]("http://paste.ubuntu.com/1024434/")

---

### Post by oldfred on 2012-06-05
Welcome to the forums.

There was (is?) a bug in grub where very large / partitions causes issues. It seems that it stops looking for files beyond a certain point. It also may be related to BIOS settings that need to be LBA or large not IDE.

```
=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 130.193119049 = 139.793797120  boot/grub/core.img                             1
1612.135658264 = [COLOR=Red]1731.017482240[/COLOR] boot/grub/grub.cfg                             1
   1.297851562 = [COLOR=Red]1.393557504 [/COLOR]   boot/initrd.img-3.2.0-23-generic               2
1612.134506226 = 1731.016245248 boot/vmlinuz-3.2.0-23-generic                  1
   1.297851562 = 1.393557504    initrd.img                                     2
1612.134506226 = 1731.016245248 vmlinuz                                        1


```I normally suggest smaller root partitions of 25GB and make rest of drive other partitions like /home or data  partitions or if your are not sure leave unallocated for now.
Some have tested just by shrinking root with gparted to a much smaller size and about half found that works (some have not said or just reinstalled). A few others have created a small /boot partition and that has worked. 
The issues is like the old IDE drives from 15 years ago that could only boot from the beginning of the drive. Some BIOS about 6 or 7 years or more old could only boot from the first 137GB, and maybe BIOS setting of IDE emulates that??

---

### Post by thegameking on 2012-06-05
Thank You so much. It works now. I took ur advice and jsut re installed the partitions with 250MB for boot, 25GB for root and the renaming as swap.

---

### Post by oldfred on 2012-06-05
I hope you did not make remaining swap.

 It should be /home or data. 

Swap only needs to be the size of RAM if wanting to  hibernate, otherwise 2GB is usually all you need unless you have less than 1GB of RAM.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

