---
title: "Having problem with Grub"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by rajuchettri on 2013-04-29
While installing ubuntu 12.10 on usb drive, I mistakenly failed to choose the usb bootloader MBR to usb drive and the grub was installed on my netbook hard drive. I rectified the problem by reinstalling.  Now without my usb drive I cannot boot to Windows XP of my netbook. Now I want to remove grub from my netbook drive. Please help.

---

### Post by grahammechanical on 2013-04-29
Do you have a Ubuntu on your Netbook drive? No. Then I am guessing that you need to re-install the Windows XP boot loader that you replaced with Grub during the first install. That I think is what you need to do but I have no experience with Windows. This might help but I cannot say.

[http://answers.microsoft.com/en-us/windows/forum/windows_xp-system/how-to-remove-linux-grub-bootloader-and-restore-xp/5610bd4b-ff50-408b-8434-310a11eaaaef](http://answers.microsoft.com/en-us/windows/forum/windows_xp-system/how-to-remove-linux-grub-bootloader-and-restore-xp/5610bd4b-ff50-408b-8434-310a11eaaaef)

Regards.

---

### Post by oldfred on 2013-04-30
Easy as it is a gui.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by rajuchettri on 2013-04-30
thank you all for your kind help...rajuchettri

---

