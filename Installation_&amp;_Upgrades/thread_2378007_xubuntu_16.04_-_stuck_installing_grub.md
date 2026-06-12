---
title: "xubuntu 16.04 - stuck installing grub"
date: 2017-11-18
forum: Installation &amp; Upgrades
---

### Post by pithaya on 2017-11-18
Hi,
I have bought a new laptop Acer that came with Windows 10. I have been wanting to install Xubuntu 16.04 (whiping Windows from my computer) but I just can't install it. I did a bootable USB, I can use Xubuntu through the Try option, but when I try to install it, it get stuck at installing grub.

I surfed a little bit online and tried the solutions out there : changing the partitions, trying to reinstall grub, but nothing seems to work. 

Can anyone help me? I just don't want to use Windows hahahaha

---

### Post by oldfred on 2017-11-19
Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
More details on installing in UEFI mode in link in my signature.

But Acer has a unique requirement of setting an UEFI password & enabling "trust" on the Ubuntu/grub .efi boot files in ESP from within UEFI. 
Make sure you have newest UEFI from Acer.


 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by photonxp on 2017-11-21
Any more infomation such as steps installation and screen output/phenomenon?

---

### Post by oldfred on 2017-11-21
Issue in this thread is just Acer and its trust setting requirement which actually is not a grub issue, if grub in general post a new thread.

Users that have set trust and actually have done it posted in the links above.
And one of the links shows a screen shot of a typical Acer system.

---

