---
title: "Installing Ubuntu with dual video cards"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by Mykal73 on 2008-04-05
I have an ATI X1900XTX and an ATI X1900XT crossfire setup on my PC. I've tried to install several different versions of Ubuntu I know I've had it on here before but now when I try to install it sends me to the command line which I have no idea how to work with without guidance. Does anyone have the steps I need to take so I can get the GUI working so I can complete the install?

---

### Post by Mykal73 on 2008-04-05
I got Ubuntu to install on an IDE drive I have on my pc, but when I finished the install  and rebooted when grub was initializing I got "error 22". I had to go into the windows recovery console and do a fixmbr to be able to boot to windows again, I can see the ubuntu installation but I'm not sure what I need to put into boot.ini so I can have a dual boot system. (My windows install is on a 160 GB sata drive. I have 2 80 GB sata drives I use for data storage) can someone tell me what I need to do so I can get Ubuntu running?

---

### Post by tamoneya on 2008-04-05
im not very familiar with boot.ini so I would do it the linux way by inserting the ubuntu LiveCD and reinstall in GRUB. Take a look here for help in reinstalling GRUB.  [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Mykal73 on 2008-04-08
I wound up wiping and using the whole IDE drive (no biggie since I planned on doing a linux install on it) that took care of the GRUB error and let me boot into ubuntu so I could install the ATI drivers. So far everything seems to be running fine. :KS

---

