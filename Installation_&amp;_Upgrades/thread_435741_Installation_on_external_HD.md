---
title: "Installation on external HD"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by liberalist on 2007-05-07
Hi everyone,

I am a Mac OS X Intel user and wish to install Kubuntu on an external (LaCie USB 2.0) drive. Is this possible? If so, please tell me how to install Kubuntu 7.04 (Feisty Fawn) on this external drive.

Thank you very much in advance.

---

### Post by NilsE on 2007-05-07
1) Burn the CD from the ISO file
2) Attach external drive
3) Boot from the CD
4) Take the install option from the desktop
5) Follow the instructions
6) Make sure grub boot is written to the external drive (SEE NOTE)


NOTE: One way to make sure of #6 is to temporarily remove the internal drive and boot from the CD unless you want setup dual boot from the internal drive. This also assumes you can boot from the external drive at the BIOS level.

---

### Post by liberalist on 2007-05-07
> **NilsE said:**
> 
(...)
NOTE: One way to make sure of #6 is to temporarily remove the internal drive and boot from the CD unless you want setup dual boot from the internal drive. This also assumes you can boot from the external drive at the BIOS level.
I have an iMac Intel and it is almost impossible to remove the internal drive, are there any other options? When I install Kubuntu 7.04, can I select the external drive somewhere in the setup?

---

### Post by NilsE on 2007-05-07
Yes, you definitely get to select the drive you install on.  It will more than likely be SDBx.  I was just cautioning that if you don't want to touch the boot record on the internal drive make sure you watch for the option of where the boot record goes.  This option is somewhere around when you do the partitioning within the install.

---

### Post by liberalist on 2007-05-07
Is the speed of Kubuntu Linux acceptable when running from an external (USB 2.0) drive?

---

### Post by NilsE on 2007-05-07
> **liberalist said:**
> Is the speed of Kubuntu Linux acceptable when running from an external (USB 2.0) drive?
Yes, it was for me on USB 2.0.

---

