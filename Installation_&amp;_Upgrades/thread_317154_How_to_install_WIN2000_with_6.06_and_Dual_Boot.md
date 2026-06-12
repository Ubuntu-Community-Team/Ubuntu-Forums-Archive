---
title: "How to install WIN2000 with 6.06 and Dual Boot"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by m_vrik on 2006-12-11
I have Dapper installed on my Compaq N600c laptop, 20 gig HD.  I resized the HD and created an ntfs partition of 5 gig and want to install WIN2000 on it and be able to dual boot this box.  Problem is I don't know how to go about installing the Windows OS and change Lilo so that I can dual boot.  Help is appreciated.

---

### Post by andreas64 on 2006-12-14
Hi,

Win2000 must be installed into the first partition of your harddisk. So the most painless way is to install Windows first and Ubuntu after your Windows-installation. In that case, grub will detect Windows and you will have the startup-choice, wich operating system to boot 

Andreas

---

### Post by m_vrik on 2006-12-14
Andreas64'
Thanks, I'll try that.  I modified my /boot/grub/menu.lst to show Windows on hda3 where my ntft partition is located, but before I did that I had installed lilo.config and now when I press 'esc' on boot-up and select Windows, I get a Lilo splash screen which soon starts to boot Ubuntu 6.06.  I can't figure out how to get rid of the Lilo application so I was thinking of wiping my laptop HD and starting over.  Any thoughts?

---

### Post by K.Mandla on 2006-12-15
If you have open, unpartitioned space, you can install Windows to that area, then rebuild Grub to allow both operating systems to boot. It might save you reinstalling Windows, but it also takes an extra step or two. There's a howto somewhere around here about rebuilding Grub. ... :-k

---

