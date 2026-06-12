---
title: "Cannot open Windows XP from Grub boot-up screen"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by explorer716 on 2007-08-27
I have two hard drives. One drive for Windows XP and the other for Ubuntu.  On the Grub boot-up screen I can scroll down and highlight Windows XP OS and hit enter.  Instead of starting Windows I get this message, "NTLDR is missing  Press Ctrl +Alt+DEl to restart." 

When I press Ctrl+Alt+Del  I go back to the Grub Start-Up page.  From here I can go into Ubuntu, but not to Windows XP.

What have I done and how can I correct this problem?

Thank you

---

### Post by Pumalite on 2007-08-27
From Terminal post:
sudo fdisk -l(small L)
cat /boot/grub/menu.lst

---

