---
title: "Win 8 is booting directly after installing Ubuntu"
date: 2014-08-31
forum: Installation &amp; Upgrades
---

### Post by priyesh2 on 2014-08-31
Recently, 1 hr ago i installed Ubuntu 13.10 using USB. Installer doesn't detected my win 8, so i choose Something else and installed Ubuntu and at end at shows Installation Finished.

But now my windows 8 is booting directly without showing option to choose Ubuntu.
When i m trying to install it again, it shows Installer has detected Ubuntu 13.10.:KS

See attachment

My laptop : HP pavilion 15 n204tx

---

### Post by sbnwl on 2014-08-31
Nearly all the new laptops having Windows 8 preinstalled are UEFI enabled. When you are in Windows 8, delete the Ubuntu 13.10 partition (~43GB) and the swap space(~9GB). This time make Ubuntu 14.04.1 live usb, and boot into it. Now try to install Ubuntu 14.04.1 using the UEFI option.

You can follow this tutorial:
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

Warning: BEFORE YOU TRY THE INSTRUCTIONS IN ABOVE, FIRST BACK UP ALL YOUR IMPORTANT DATA FROM WINDOWS 8.

---

### Post by priyesh2 on 2014-09-01
My laptop came with pre-installed  Ubuntu, and its in LEGACY mode.


1 doubt, while installing Ubuntu, in screen where i selected partition for installation

      what should be the ** Device for boot loader installation** : /dev/sda ATA HGST HTTS545050A7 (500.1 GB)  **OR** /dev/sda5

---

