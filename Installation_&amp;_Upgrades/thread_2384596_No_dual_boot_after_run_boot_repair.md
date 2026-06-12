---
title: "No dual boot after run boot repair"
date: 2018-02-09
forum: Installation &amp; Upgrades
---

### Post by r4u1 on 2018-02-09
Today install Ubuntu 17.10 but my pc only start in windows 10, I try whit boot repair for fix it but the problem persist.

Leve the boot info scrip

[https://paste.ubuntu.com/26544855/](https://paste.ubuntu.com/26544855/)

Thanks oldfred i solved mi problem whit the dual boot whit this post 

[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)

---

### Post by oldfred on 2018-02-09
What brand/model system?
I see Acer mentioned? 
If Acer ( all models as far as we know) you have to set UEFI passwork and enable "trust" on the Ubuntu/grub .efi boot files.
Some older models need UEFI updates. Older threads mention downgrading UEFI and newer ones then say newest UEFI from Acer works.

Multiple threads with essentially same instructions, but some explain better or differently so look at several.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by r4u1 on 2018-02-09
Ok I chek all post and change the tread to solve when i found the solution and post it and is a Acer Aspire F 5 Bios last update 2017 but i check if have another update today

---

