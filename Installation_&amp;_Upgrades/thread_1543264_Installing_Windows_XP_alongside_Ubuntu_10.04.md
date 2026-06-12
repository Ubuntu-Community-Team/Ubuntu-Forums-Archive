---
title: "Installing Windows XP alongside Ubuntu 10.04"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by magicdanw on 2010-07-31
It is a sad day indeed, but I need to run a developer's tool that only runs on Windows, and it interfaces with a USB device that doesn't do well through any VMs I've tried.  I've resorted to installing XP.

Now, I'm wondering if there will be any problems I'll face installing XP after Ubuntu 10.04 has already been installed?  I suspect so, but it's been a while since I dual booted, and I've never worked with Grub2, so any and all suggestions are welcome!

---

### Post by oldfred on 2010-07-31
You need to have a primary partition that is NTFS with the boot flag for windows.

After windows installs it will overwrite grub and you will need to reinstall grub to the MBR. After booting into Ubuntu run sudo update-grub and it should find the windows install.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by magicdanw on 2010-07-31
Thanks! :D

---

