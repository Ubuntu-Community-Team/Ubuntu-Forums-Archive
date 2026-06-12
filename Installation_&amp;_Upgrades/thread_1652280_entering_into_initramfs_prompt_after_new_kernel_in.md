---
title: "entering into initramfs prompt after new kernel installation"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by chaitanyajun12 on 2010-12-24
i tired installing a new kernel to my ubuntu 10.04 system. I have got only ubuntu installed on this system.

I compiled it and even updated the grub.

following these steps shown below.

1. make defconfig  (selecting a default configuration)
2. make 
3. make modules_install
4. make install
5. update-grub 

Is this the correct process ?
but after booting up the new kernel, its showing errors. I dont remember them correctly. 

right after this i thought not having initrd.img created might be the problem. I created the initrd,img.2.6.36.2
using
update-initramfs -k 2.6.29.3 -c 

This created the problem, after booting its not even opening grub and directly entering into initramfs prompt. What is the problem ?

how to boot the system from the initramfs prompt. I am stuck here. 

Help would really be appreciated.

With kind regards,
Chaitanya.

---

