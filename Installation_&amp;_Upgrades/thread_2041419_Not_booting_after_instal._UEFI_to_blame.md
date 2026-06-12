---
title: "Not booting after instal. UEFI to blame?"
date: 2012-08-12
forum: Installation &amp; Upgrades
---

### Post by royalflush5 on 2012-08-12
So I recently upgraded my motherboard to an ASUS M5A97, and with that, went from bios to uefi. AS usual, I installed windows first, then Ubuntu on my other drive. It installs fine from my flash drive, then when I reboot, I cant get into either OS. Booting from my windows gets nowhere, and booting from my Ubuntu drive me a pinstriped screen, and pressing F10 seems to just change the color. 

Any help would be appreciated, thanks guys

---

### Post by darkod on 2012-08-12
Did you install ubuntu in UEFI mode? Did you boot the flash in UEFI mode?

You need to do that so that the installation will be done in UEFI mode if you are using UEFI boot.

---

### Post by royalflush5 on 2012-08-12
for some reason, my board wont let me boot the drive in uefi mode, is there a key I can press when it boots?

---

### Post by oldfred on 2012-08-12
As Darko mentioned, you have to install in UEFI mode (both Windows & Ubuntu) to get it to work in UEFI mode.

Post link to BootInfo from this:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

