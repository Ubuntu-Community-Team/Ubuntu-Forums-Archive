---
title: "Installed Ubuntu 7.10 , Now it freezes when booting"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by christophicer on 2008-02-23
I've been going for 3 days now, trying to get Ubuntu working. Installed the alternate cd because the live just wouldnt boot, it would freeze everytime so I tried the alternate, installed fine and everything went good. Rebooted and there she goes it stalls in the exact same spot as the live cd did, about 1/10th of the way, cant figure out where to go, all i see is and error-code-+0x72/0x80 and i don't know what to do thats all i understand, popped the cd back in and it went to replace the grub file, tried all the supported easy fixes, hd0, hd0,1 and floppy but none do anything different, really wanna get rid of windows, been having problems for too long but i cant get any version of linux to work, tried, Ubuntu, Xubuntu, Fedora, Mandriva, LinuxOS and Linux Mint, it all seems to do the exact same thing, so BIOS error or...


Acerpower Sv
1Gb Ram
2.6 Intel P4
256 Radeon 9250 pci grapic

---

### Post by gwoodruff on 2008-02-23
If you hit esc when message appears during grub boot can an you select the repair option and boot to terminal prompt? If so it could be display problem. If so try sudo dpkg-reconfigure xserver-xorg and set display driver to vesa or vga. Hope it helps. Ubuntu has a learning curve but is well worth the effort just for free support and software.

---

### Post by Pumalite on 2008-02-23
Are you dual booting? Vista?

---

