---
title: "Got &quot;Could not find kernel image: linux&quot;  error from pen drive installation"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by Tinkersteel on 2008-02-17
I downloaded Xubuntu 7.10 for my older model IBM thinkpad plus the Xubuntu ISO. I research a page on how to install Xubuntu with USB pen drive. I followed the instructions given from this[ site]("http://xubuntublog.wordpress.com/2007/07/03/xubuntu-feisty-now-from-usb-drive/")

When I tried my first boot install, I got a "no partition active" error. I then followed the trouble shooting advice: "you have to set it active for boot. Open up a Terminal (Applications->Accessories->Terminal) and type sudo fdisk /dev/sdx (you know, replace sdx with your drive). Press “a” and then “1&#8243;. Press “w” to save and then it should work!" At the second boot install attempt, I got "Could not find kernel image: linux" error. I looked just about everywhere for any solution to bypass that problem, but those infos have subtle messages, too difficult for a beginner for me to understand. Anyone could provide useful advice help would be most appreciated. Please provide a step-by-step detail instructions to fix that error, as I mentioned I'm not too familar with Linux.
__________________

---

### Post by mrsteveman1 on 2008-02-17
Thats a syslinux error which comes up when the config file is missing.

There should be a file in the root of the drive: isolinux.cfg

Rename it syslinux.cfg and see if that helps.

---

### Post by zellar on 2008-03-06
I used the guide USB [Ubuntu 7.10 Gutsy Gibbon Install]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") and came across the same problem and mrsteveman1 solution worked for me. Thanks!

---

### Post by micgel on 2008-03-14
May be simple solution, check if all needed files for booting Linux are inside a folder ex: Pendrivelinux08.
 If it is the case, move it outside,  at the root level.

---

### Post by mesusa on 2008-06-13
Folks ~
FYI, this fix almost corrects the problem with instructions for loading Linux Mint on a USB. If you change the name of the file, and copy all files in that iso directory to the root directory, it works just fine.

Cheers

---

