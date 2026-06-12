---
title: "GRUB Won't Find Kernel"
date: 2013-04-22
forum: Installation &amp; Upgrades
---

### Post by fowlslegs on 2013-04-22
I just upgraded from Xubuntu 12.10 to Ubuntu 13.04 using `sudo do-release-upgrade -d`. I accidentally turned my computer off during the upgrade process when I meant to restart xscreensaver and some other x program which the terminal-based installation prompt said I needed to halt. Anyway it seemed I had resolved everything after remounting my sda1(root) partition and entering `dpkg --configure -a` from kernel 3.8.8's recovery mode,  which I selected from the grub2 menu during bootup. I installed all  raring updates and fixed my /etc/apt/sources.list. Everything seemed to  be working fine. `uname -r` returned 3.8.8.x...-generic, `sudo  update-grub`, however only found memtest. I made a mental note of this  and meant to reinstall the kernel and figure out why grub wasn't seeing  it even though it was obviously in use. However, I forgot and rebooted  after updating. I am now immediately taken to memtest. (Oh yeah I set  the grub timer to 0 and holding shift does nothing). What can I do?  Kernel 3.8.8.x...-generic is definitely on my computer somewhere.

---

### Post by fowlslegs on 2013-04-22
Fixed with boot-repair CD.

---

### Post by Toz on 2013-04-22
Thread closed. Please do not create duplicate threads for the same issue, it dilutes the community effort.

---

