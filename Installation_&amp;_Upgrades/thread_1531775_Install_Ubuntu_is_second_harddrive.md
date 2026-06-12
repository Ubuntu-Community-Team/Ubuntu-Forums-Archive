---
title: "Install Ubuntu is second harddrive"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by cazador31 on 2010-07-15
I am running windows 7. I want to install Ubuntu 10.04 on a second harddrive. I am new at this and would like to know the correct way to do it. Easy instructions would be appreciated since I am new to Ubuntu

Thank You

---

### Post by andrewthomas on 2010-07-15
I would change the boot order in BIOS to boot the CD/DVD first, then the drive that does NOT have windows 7 on it, last the win7 HD. Then install from the live CD, just make sure that you select the right drive when the installer asks you where you want to install Ubuntu.

---

### Post by YesWeCan on 2010-07-15
If you are new to this I would also recommend physically disconnecting the W7 HD before you install Unbuntu. This guarantees that the Ubuntu bootloader, called Grub2, is not put on the W7 drive (like it could be if you make a mistake).

Lots of people make mistakes. It is easy to make a mistake.

Once Ubuntu is installed, shut down and reconnect W7 HD and then tell bios to boot Ubuntu HD first and boot Ubuntu. Then from a terminal type 'sudo update-grub' and this will add W7 to the grub boot menu.

This process is not strictly necessary but is bullet-proof and keeps your W7 installation safe.

---

### Post by nah40 on 2010-07-15
> **YesWeCan said:**
> If you are new to this I would also recommend physically disconnecting the W7 HD before you install Unbuntu. This guarantees that the Ubuntu bootloader, called Grub2, is not put on the W7 drive (like it could be if you make a mistake).

Lots of people make mistakes. It is easy to make a mistake.

Once Ubuntu is installed, shut down and reconnect W7 HD and then tell bios to boot Ubuntu HD first and boot Ubuntu. Then from a terminal type 'sudo update-grub' and this will add W7 to the grub boot menu.

This process is not strictly necessary but is bullet-proof and keeps your W7 installation safe.

Absolutely the simplest way to do it without problems.

---

