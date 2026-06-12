---
title: "Problem when booting"
date: 2015-01-19
forum: Installation &amp; Upgrades
---

### Post by Nick2129 on 2015-01-19
I just got ubuntu loaded onto my gateway laptop and it booted since I saw bash running. Now it is on a screen that says to choosensure a .cat file and press restore. I found the boot.cat file under isolinux  but when I hit OK it does not appear in the selection box and hitting restore does nothing. I'm sorry if there is not enough information  but that is all it says. Does anyone know of a way to fix this?

---

### Post by oldfred on 2015-01-19
Are you booting live installer or after install? 
You should not have syslinux except on live installer in BIOS mode.
Installed system uses grub and new systems also use grub in UEFI mode to boot live installer.

May be best to see details:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

