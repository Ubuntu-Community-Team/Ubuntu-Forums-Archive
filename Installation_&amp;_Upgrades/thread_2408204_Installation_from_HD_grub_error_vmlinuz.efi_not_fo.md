---
title: "Installation from HD grub error vmlinuz.efi not found, load kernel first"
date: 2018-12-15
forum: Installation &amp; Upgrades
---

### Post by essflow on 2018-12-15
Hello,
Unfortunately my upgrade from 16.04 to 18.04 via terminal did not work (hangs, black screen, kernel panic) and now even older versions and their offered recovery modes all end up with a black screen.

However, 
before I was trying to "just make" the dist-upgrade, I did put a 2nd mSATA ssd into the T430 ThinkPad and was trying to make the 18.04 running as an alternative. Because I don't have a CD-device, I did follow some steps explained for how to download and prepare the distro for an installation from HD instead from CD or USB. 
When I start the grub is offering me the option:
Ubuntu 18.04.1 LTS Installer 
and if I select it:
Error : ~" /casper/vmlinuz.efi not found" 
~"you need to start the Kernel at first" 

--- in/for grub :
By entering the cli with [c] 
and then :
grub> ls (hd1, msdos1)/casper/vmlinuz
returns :
vmlinuz
---
Has somebody an idea, how I can proceed further? 

Thanks in advance, 
Florian

---

### Post by ubfan1 on 2018-12-15
Names like vmlinuz.efi change for no reason I know, so if you look at the installer media, you will see the name should be /casper/vmlinuz  no efi.  Check the initrd entry/file name too, it may be initrd.lz now.  Edit those in the grub.cfg until you can rerun sudo update-grub

---

### Post by essflow on 2018-12-15
The answer was easy: all I needed to do was to delete the: ".efi" part manually in the grub order. I think, I entered with m instead c and simply deleted and f10, but I if I remember right. Did grap the installer and I could manage to get it to work without a cd-drive.

---

### Post by essflow on 2018-12-15
> **ubfan1 said:**
> Names like vmlinuz.efi change for no reason I know, so if you look at the installer media, you will see the name should be /casper/vmlinuz  no efi.  Check the initrd entry/file name too, it may be initrd.lz now.  Edit those in the grub.cfg until you can rerun sudo update-grub

Thanks, it seems to be an older issue. 
Before you have given the answer, I could find it within a post related to Ubuntu 12.x
...
Thank you!

---

