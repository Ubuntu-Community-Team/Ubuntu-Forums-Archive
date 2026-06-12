---
title: "Dell poweredge hangs when starting Ubuntu"
date: 2015-03-07
forum: Installation &amp; Upgrades
---

### Post by ben148 on 2015-03-07
I just recently got a Dell Poweredge 1850 and put in a 140GB Hard drive to start installing Ubuntu Server 14.04.2. It was installed from my USB Flash drive, and was able to find the drive after some setup and the installation finished okay. Once I had the server restart it will stop after it goes through everything after doing POST and will just sit there with no error message.

---

### Post by tgalati4 on 2015-03-07
Did you boot into RAID BIOS (Control-S) and set up the drive as JBOD?  If you don't set it up in BIOS, then the OS can't mount it properly.  Check the log files by pulling the drive and putting in another server.  Or boot from USB again and check the log files.  I presume that you checked the media on the USB stick by selecting the "Check Media" option from the USB/GRUB bootup menu.

---

