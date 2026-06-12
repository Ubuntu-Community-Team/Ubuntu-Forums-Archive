---
title: "Problems with an Acer Swift 3 SF314-41"
date: 2019-09-24
forum: Installation &amp; Upgrades
---

### Post by fparri on 2019-09-24
Hello,

I've just bought an Acer Swift 3 SF314-41-R2XF ([https://www.acer.com/ac/it/IT/content/model/NX.HFDET.005](https://www.acer.com/ac/it/IT/content/model/NX.HFDET.005)) running on a AMD Ryzen 5 3500U cpu and an AMD Radeon Vega 8 and, unfortunately, I have problems running Linux on it.
Most of the distributions I've tried until now either freeze during boot, or freeze a few seconds after getting to the desktop screen.

Anyone can help me trying to fix this?

---

### Post by cabpa on 2020-09-08
> **fparri said:**
> Hello,

I've just bought an Acer Swift 3 SF314-41-R2XF ([https://www.acer.com/ac/it/IT/content/model/NX.HFDET.005](https://www.acer.com/ac/it/IT/content/model/NX.HFDET.005)) running on a AMD Ryzen 5 3500U cpu and an AMD Radeon Vega 8 and, unfortunately, I have problems running Linux on it.
Most of the distributions I've tried until now either freeze during boot, or freeze a few seconds after getting to the desktop screen.

Anyone can help me trying to fix this?


Mine is working fine at the moment with the 5.4.0-26-generic #30-Ubuntu SMP kernel of the Advanced options for Ubuntu in Ubuntu version 20.4.1. I updated the GRUB_DEFAULT=0 to GRUB_DEFAULT="Advanced options for Ubuntu>Ubuntu, with Linux 5.4.0-26-generic" of /etc/default/grub. Then update grub with sudo update-grub

---

### Post by ActionParsnip on 2020-09-08
Do you have the latest BIOS?
Have you tested your RAM health?

---

### Post by cabpa on 2020-09-10
> **ActionParsnip said:**
> Do you have the latest BIOS?
Have you tested your RAM health?

BIOS version v1.04. RAM is working fine.
Below are the steps that I used. I set the older kernel in the grub  file: 
1. Download the Ubuntu desktop iso at [https://ubuntu.com/#download](https://ubuntu.com/#download)
2. Write the ISO file to a USB flash drive with Rufus. Instruction is at [https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)
3. Restart and keep pressing the F2 key to access the BIOS
4. Navigate to the Boot menu and set USB as the 1st boot priority with the F6 key
5. Press F10 to save and exit the changes
6. Select Install Ubuntu alongside with Windows 10
7. The installer will automatically set an Ubuntu partition size with your HDD but you can drag the vertical divider of the partitioning tool to set the Ubuntu partition according to your partition size preference.
8. Proceed and complete the installation.
9. Restart and keep pressing F2 and set Ubuntu as the 1st boot priority with the F6 key
10. Press F10 to save and exit the changes
11. Select Advanced options of Ubuntu in the grub boot menu
12. Select the recovery mode line Ubuntu GNU/Linux, with Linux 5.4.0-26-generic (recovery mode)
13. Select "Drop to root shell prompt"
14. Make a backup copy of /etc/default/grub with the cp command
15. Edit /etc/default/grub with nano and update GRUB_DEFAULT=0 to the older kernel listed in the Advanced options like GRUB_DEFAULT="Advanced options for Ubuntu>Ubuntu, with Linux 5.4.0-26-generic"
16. Edit also the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amd_iommu=off" in /etc/default/grub
16. Save the file and exit
17. Reboot with the reboot command
18. Login and Install lightdm and set as default display manager because the gdm display manager is very laggy even after system idle it becomes very slow.
19. Install LXQT
20. Reboot
21. Click the Ubuntu icon in the login input box. Select LXQt then login with your credentials

---

