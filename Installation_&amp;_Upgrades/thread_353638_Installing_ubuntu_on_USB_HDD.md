---
title: "Installing ubuntu on USB HDD"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by Prinz on 2007-02-04
Hi everyone I am new to the site and to ubuntu. So heres the problem: I have two hard drives: One is a 40GB internal drive (which has Windows XP on it), and the other is a 100GB USB external drive. I want to install ubuntu on the USB drive, but the problem is my motherboard wont allow a USB device to be bootable. So I am wondering how I would go about doing this. I would like to make it so that I could boot either OS whenever I want...preferably Ubuntu on the external HDD and Windows on the Internal HDD. Thanks in advanced for the help.

---

### Post by glotz on 2007-02-04
I think there's no problem or then I've misunderstood the situation somehow. The normal drill is, acquire a CD and modify BIOS to boot off it, insert the disc and reboot. Ubuntu should now start. Install and select to install onto the external disk. During the install, the MBR (master boot record) of the internal disk will be modified so that when you next time boot, you'll see a menu to choose which OS you'd like to boot to.

---

### Post by Prinz on 2007-02-05
So once I have it installed on the external disk whenever I reboot (to the internal disk) It will ask me which OS it run? I dont need to modify the internal drive or copy anything over to it in order for it to ask me?

---

### Post by glotz on 2007-02-05
Correct. The installer will modify the MBR for you to contain GRUB, which presents the menu. [http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

---

### Post by Prinz on 2007-02-05
Cool. Thank you so much for you help!  Im off to install ubuntu now!

---

### Post by glotz on 2007-02-05
You're so welcome! :)

Welcome to the tribe!

---

