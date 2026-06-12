---
title: "Windows error after installation"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by karpinskipawel1 on 2013-03-09
Hello I installed ubuntu on my PC with Windows 7 . I choose during the installation to devide my disc 50% for Ubuntu and 50% for Windows.
After installation I can't start windows. 
I will be appreciate for help this is my work computer and I need to fix it ASAP

---

### Post by black veils on 2013-03-09
boot the installer and choose try, load the desktop.

search terminal application, paste:

sudo parted -l

to list what is on your disk, then paste the output in a reply, using code tags (the hash symbol button)

---

### Post by Mark Phelps on 2013-03-10
Sounds like you used the Slider in the installer to shrink the Win7 OS partition -- BAD idea!  That has historically run the risk of corrupting the Win7 boot loader -- as you have now discovered.

While Win7 was working, you could have used the Backup feature to create a Win7 Repair CD for free; but now, it will cost you to do that.  IF you go to the site below, you will find a link for the ISO image for that CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Buy the image, download and burn the ISO to CD, boot from that -- and run Startup Repair three times.

---

### Post by mirearts KING SUNNY on 2013-03-10
What happened, is your Windows bootloader got corrupted or erased by the  Ubuntu setup. Boot Ubuntu and use GPARTED to see your partition setups.  If you know your Windows partition, set the flag to "bootable" 

2. Never select auto installation modes, always other or manual. Mount partitions manuaaly fs:ext4, mount point /

---

