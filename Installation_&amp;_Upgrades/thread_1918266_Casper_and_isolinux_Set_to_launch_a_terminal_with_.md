---
title: "Casper and isolinux Set to launch a terminal with a single application?"
date: 2012-01-31
forum: Installation &amp; Upgrades
---

### Post by Barcel0 on 2012-01-31
I have a personalized system of ubuntu, is a livcd, I've added an installer console (Serer - terminal) and set casper and isolinux need to add an entry in the start of the boot to allow me to start the installer directly into a console without having to lift the system in live mode and then run the installer.

 I have 2 isolinux entry:
 - Start the system in live mode
 - Install directly (this does not work)

label live
  menu label live - Probar Yayabo
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz quiet splash --

label install
  menu label install - install (serere --terminal)
  kernel /casper/vmlinuz
  append  text only-serere initrd=/casper/initrd.gz quiet splash --


some body help me?

---

