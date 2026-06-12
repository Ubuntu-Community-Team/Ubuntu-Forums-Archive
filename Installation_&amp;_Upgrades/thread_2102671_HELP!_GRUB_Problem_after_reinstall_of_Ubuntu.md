---
title: "HELP! GRUB Problem after reinstall of Ubuntu"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by alu0506 on 2013-01-07
Hello,
I had a dual-boot installation of Windows 7 x64 and Ubuntu x32 and I wanted to install Ubuntu x64 in the place of Ubuntu x32. The first time I tried to install, I booted from the Ubuntu x64 Live CD and chose "Erase Ubuntu 12.10 and reinstall" and after I installed I rebooted and expected the usual GRUB menu but instead I saw a screen saying "Unsupported Filesystem" and GRUB Recovery. I booted the Live CD again and Installed, this time manually selecting the partition and installing. It still says the same thing when I try to boot the computer. I want to keep Windows and all the files intact.
Thank You!

---

### Post by adityamagadi on 2013-01-07
pls post the output of os-prober and try running sudo grub-update?

---

### Post by alu0506 on 2013-01-07
os-prober returns the following:

/dev/sda1:Windows Recovery Environment (loader):Windows:chain
/dev/sda2:Windows 7 (loader):Windows1:chain
/dev/sda6:Ubuntu 12.10 (12.10):Ubuntu:linux

grub -update and grub-update returns a command not found.

---

### Post by Bucky Ball on 2013-01-07
Welcome to the forums. If sudo update-grub doesn't work try Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If that doesn't work it can give us a full report of what is going on. Post a link to that.

---

### Post by alu0506 on 2013-01-07
Well, That seems to have done it! Thank You!

---

