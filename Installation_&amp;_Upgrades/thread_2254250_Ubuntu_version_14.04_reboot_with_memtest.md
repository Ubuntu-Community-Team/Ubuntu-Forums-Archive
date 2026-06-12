---
title: "Ubuntu version 14.04 reboot with memtest"
date: 2014-11-25
forum: Installation &amp; Upgrades
---

### Post by bachar-82 on 2014-11-25
With Ubuntu version 14.04 how to reboot with memtest ?
sudo apt-get install memtest86+ does not work, I am unable to set the path to grub, 
I tried to install in local directory the .iso image, editing path to grub via loop(hd0,1) in custom_40 file was an impossible mission too

Any idea or help wit grub.d file or other stuff ? 

Thks,

---

### Post by deadflowr on 2014-11-25
Is Ubuntu installed?
If so, memtest would already be installed and ready to boot into when get to the grub screen.
No need to loop an iso file to access memtest.

Is memtest not showing at the grub menu at boot?

---

