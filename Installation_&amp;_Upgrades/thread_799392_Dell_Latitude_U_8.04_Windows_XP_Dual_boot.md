---
title: "Dell Latitude U 8.04 Windows XP Dual boot"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by quikone8 on 2008-05-19
Thanks in advance for considering this question.

I have Ubuntu Server running on a Dell 2800 series successfully as a mail server.

My problem; I am trying to successfully install 8.04 D on a Dell Latitude D820.  It is installed but every time I try to boot the system it goes to XP with no choice for the OS.

I have checked and can find the boot folder but cannot find any hint of where grub was installed.  I have checked all partitions, but nothing so far.  I assume it should have been installed in the Windows partition.  I would like a grub choice for the OS, but am willing to create a boot 
CD or USB device.

Boot file attached.

---

### Post by iaculallad on 2008-05-19
Post the content of your /etc/grub/menu.lst and /etc/grub/device.map, this could help resolve your problem.

---

