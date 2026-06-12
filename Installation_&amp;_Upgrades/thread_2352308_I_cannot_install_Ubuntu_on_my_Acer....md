---
title: "I cannot install Ubuntu on my Acer..."
date: 2017-02-11
forum: Installation &amp; Upgrades
---

### Post by naseralomari1998 on 2017-02-11
Hi guys,
I have a laptop with the following specifications: 
- Acer Aspire v15 v3-572g-786A
- Intel Core i7-6500U 2.5GHz
- NVidia GeForce 940M 2GB Dedicated VRAM
- 8GB DDR3 Memory
- 1000GB HDD
Windows 10 was already installed on it with UEFI Bios.
---------------------------------------------------------------
I came to install Ubuntu and all the steps worked fine, I made sure fast-start-up was off and other options too. I also, changed the boot order, so it boots from the USB.
And the installation worked fine until the message of 'Restart now' when I pressed that. The grub menu doesn't show up. And in my bios there is no option where I can set the default operating systems. I checked my partitions and all of them were working allocated correctly. 
What am I doing wrong?
I want to dual boot both operating systems. Is it possible?
P.S. I put install along side Windows and I also tried the option Something else.
Thank you

---

### Post by westie457 on 2017-02-11
Hi Acer computers are unique because they need some further changes in the UEFI/BIOS screens. 
Reboot into the bios go to the security page. Here you must set a password to unlock the settings to select a file as 'trusted', hit F10 to save the settings and exit. You should now be seeing the Grub menu. Never forget that password otherwise you will not be able to access the bios. The password can be reset to be blank.

---

