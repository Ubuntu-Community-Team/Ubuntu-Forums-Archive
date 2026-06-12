---
title: "A Simple Rescue Mode???"
date: 2019-04-06
forum: Installation &amp; Upgrades
---

### Post by ubuntcpmb on 2019-04-06
I've recently loaded Ubuntu 18 on my machine and other OS as well. I'm trying to recover the Ubu boot loader and configure it to multi boot.

I've looked at countless so called "rescue" mode instructions and none of them work because either:

A) they all assume your HD boot loader is already grub and actually works (mine doesn't, I'm trying to RESTORE it)

B) the instructions are wrong or vague, as in they tell you to boot the Live CD and don't tell you to press Ctrl-Alt-F1 AS THE CD BOOTS, or else you'll just end up in the installer, again, and again, and again....

C) they don't tell you how to activate the "Boot:" prompt (F6) or what arguments to type in for "Rescue" mode (ie rescue root=/dev/hd5 doesn't work)

D) I've tried rebooting to the "live" cd and managed to open a terminal, issue a bunch of commands to be told certain execs are not even on the system (ie grub, find)

Should I assume that I'm better off just doing a full reinstall in the future, or is there actually a "simple" way of restoring my boot sector and configuring it to multi boot?

Anybody got any suggestions?

Cheers,
AF

---

### Post by oldfred on 2019-04-06
If you can boot live installer in live mode, same as you installed UEFI or BIOS, you then can add Boot-Repair.
It will suggest some auto fixes, but if you have several installs, it often just picks one to fix.
You can use Boot-Repair's advanced mode and choose an install and install install grub. Sometimes a full reinstall of grub is required, not just resetting BIOS or UEFI and menu.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Normally fixing grub is relatively easy.
Your second install should allow you to also boot first install. And then from first install, just restore it as default boot.

       
 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

---

### Post by ubuntcpmb on 2019-04-22
Okay, so as I understand it I have two options:

1) I need a separate disk with this "Boot Repair" package on it, boot that disk and use it to fix grub

- OR -

2) Boot the Ubuntu installer, and run the "live" version instead of the "installer", and in the live version download and install "boot repair" and run it in the "live" environment.

Much of the docs I've come across don't seem to be that clear.

Much thanks.

---

### Post by oldfred on 2019-04-23
The Boot-Repair ISO is now pretty old.
Better to just use Ubuntu live installer and add Boot-Repair to it.

---

