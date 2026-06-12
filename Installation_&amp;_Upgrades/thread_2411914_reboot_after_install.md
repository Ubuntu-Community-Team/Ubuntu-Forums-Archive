---
title: "reboot after install"
date: 2019-02-05
forum: Installation &amp; Upgrades
---

### Post by jpk1291 on 2019-02-05
Hi, have tried installing 18.04 lts desktop and all seems to proceed well. When I get to end of install and system wants me to remove cd and it reboots, I get a windows error message saying no ntldr. I get nothing showing any ubuntu startup at all. 
I installed with full install with apps, erase disk and install. I see no errors at all during install. It boots from cd into gnome fine, click install ubuntu and all seems to work well. If I put install cd back in and boot, it boots as it did 1st time into gnome with icon to intall ubuntu.
This is a generic pc with amd cpu.
What am I doing wrong?

---

### Post by yancek on 2019-02-05
Which version of windows did you have on the computer?  Was it a UEFI install, windows 8/10?  Did you install Ubuntu UEFI or Legacy?  If it was a Legacy install, did you select to install the Grub bootloader to /dev/sda?

---

### Post by jpk1291 on 2019-02-05
Had windows 7 on pc. Was a ubuntu 18.04 LTS desktop version downloaded from ubuntu site last week.

---

### Post by ubfan1 on 2019-02-05
Win 7 so probably legacy.  Error is looking for a Windows loader, so grub didn't get installed to /dev/sda.  If you installed grub to another location, like /dev/sda1, you would see an error like yours.

---

### Post by jpk1291 on 2019-02-11
Reinstalled wtih 16.04 LTS, same problem. Found good instructions on how to run/use boot repair tool, and works great now.

---

