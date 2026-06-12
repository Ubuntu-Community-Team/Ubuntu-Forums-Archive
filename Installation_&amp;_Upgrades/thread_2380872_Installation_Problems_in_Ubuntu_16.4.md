---
title: "Installation Problems in Ubuntu 16.4"
date: 2017-12-23
forum: Installation &amp; Upgrades
---

### Post by pradeep22 on 2017-12-23
I want to install Ubuntu 16.04 32 bit on a Intel 2nd gen HCL Notebook Computer. While selecting "Install Ubuntu" option, it takes a me to some errors(nouveau failed to ....ide channel 2).  After that a login screen comes. 
It really hooks up my mind. 
Mechine has two graphics cards
1 Intel 
2 Nvidia 560M(Optimus Technology) .

---

### Post by oldfred on 2017-12-23
Why 32 bit? Most work better with 64 bit  unless you have very little RAM (less than 2GB) and then Lubuntu or other lightweight flavors are suggested.
That looks like a 64 bit system, or is a tablet or very small system with 32 bit UEFI but still 64 bit system?

Are you able to turn off nVidia in UEFI/BIOS and install using Intel, then once installed boot and add nVidia drivers?
Are you using nomodeset boot parameter?
       
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

    While 32 bit 16.04 will  be supported for its life.
 Proposed end of Ubuntu 32 bit images 
[https://ubuntuforums.org/showthread.php?t=2312451](https://ubuntuforums.org/showthread.php?t=2312451)

---

### Post by pradeep22 on 2017-12-23
Ok let me first download Ubuntu 16.04 (64 bit). Then I will be back...by the way thanks.

---

