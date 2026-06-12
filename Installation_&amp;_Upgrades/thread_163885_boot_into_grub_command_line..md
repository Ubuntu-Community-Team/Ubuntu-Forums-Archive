---
title: "boot into grub command line."
date: 2006-04-21
forum: Installation &amp; Upgrades
---

### Post by xtra on 2006-04-21
Hi, I am new to ubuntu. I just did the installation on my MSI mcp51 board. 

After I changed the grub from MBR to the hda2 /boot partition,
(grub-install /dev/hda2)
 I no longer can boot into ubuntu in menu.  I have to do it manually by typing grub commands.  
grub>

How do I go back to menu boot grub. I do have the menu.lst under /boot/grub

---

### Post by aysiu on 2006-04-22
Do you have a live CD? If so, you can try [this](http://ubuntuforums.org/showthread.php?t=24113).

---

### Post by xtra on 2006-04-22
thanks aysiu

Problem solved. I just have to dd the boot sector again. so I guess that the boot sector in my /boot partition contains the information for grub to boot with menu.lst.

---

