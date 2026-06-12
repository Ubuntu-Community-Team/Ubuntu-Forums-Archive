---
title: "Dual boot setup | ubuntu16 over centos7"
date: 2017-01-14
forum: Installation &amp; Upgrades
---

### Post by praduman1417 on 2017-01-14
hi guys

i am trying to install ubuntu machine with centos  installed on diff. partition....so that i can make dual boot and from grub i can boot one of them.

but after installing ubuntu ...the grub still showing centos grub entries...( no ubuntu entry )

how can  i get ubuntu grub entry??

===========================

FYI 
installing on same hard disk ( /dev/sda)
centos boot (/dev/sda3) and (/dev/sdb4)

ubuntu on ( /dev/sda1)
=================================

---

### Post by praduman1417 on 2017-01-14
right now i am able to boot to centos machine

---

### Post by oldfred on 2017-01-14
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info
[/URL]
 [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

[URL="https://help.ubuntu.com/community/Boot-Info"]
[/URL]

---

### Post by praduman1417 on 2017-01-14
Hey guys its resolved

i just rerun the command on centos
 grub2-mkconfig -o /boot/grub2/grub.cnf

running this automatically made entry for ubuntu grub line 
after that i am able to boot in both the machines

---

