---
title: "Installation on an old laptop"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by mutew on 2008-09-15
I have this old Acer laptop which I would like to install Ubuntu on but to my dismay the DVD Writer no longer works and there is no USB/net boot option. Ubuntu was earlier installed on one of the partitions but that was formatted leaving a defunct MBR with a non-working GRUB installed so that I cannot even boot into Windows.

The only way out seems to imvolve removing the laptop hard-drive and connect it over USB to my PC so that I can install Ubuntu on a free partition on the laptop HDD. Does anybody have any idea regarding this process? Tutorials on the net mostly dealt with net / USB pen-drive installation.

---

### Post by AnPar on 2010-09-21
It should be actually feasible to restore grub, but I just cannot imagine how exactly. Relevant entries are in /etc/grub.conf or /boot/grub/menu.lst.
However you could attach an external CD ROM drive via USB, if your BIOS supports it.
You could start your PC, laptop hard drive attached, with a LiveCD. During the installation process you are asked where to install it. On that spot you could choose your external hard drive. This is only a suggestion. Not at all sure if it is the proper way to do it, but I know that it randomly works.
A proper way might be a network boot installation: [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
Hope this helps!

---

