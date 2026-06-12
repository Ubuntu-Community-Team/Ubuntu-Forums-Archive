---
title: "Installing Ubuntu via a USB memory stick"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by BattleGnome on 2007-05-24
I am looking at the documentation for installing ubuntu via a USB memory stick and it does not appear to have alot of information here.

[https://help.ubuntu.com/7.04/installation-guide/amd64/boot-usb-files.html#usb-copy-flexible](https://help.ubuntu.com/7.04/installation-guide/amd64/boot-usb-files.html#usb-copy-flexible)

It does not actually tell me what application I need to run to prepare the memory stick ?

---

### Post by frozinfire on 2007-05-31
Here's how I did it from Windows XP:

Download [this]("ftp://ftp.kernel.org/pub/linux/utils/boot/syslinux/syslinux-3.36.tar.gz").
Extract everything.
Go into the mbr folder and copy mbr.bin to your empty stick.
Run cmd, cd to the program's win32 folder, and type "syslinux b:" (or whatever drive your stick is).
Extract Ubuntu's iso to the flash drive, so that the folders look like they would on a cd.
Cut and paste the contents of the isolinux folder to the main area.
Rename "isolinux.cfg" to "syslinux.cfg"

That should get you up and running.

---

### Post by oxalá on 2007-05-31
When doing this, is it imperative that one use the contents from an alternative installation CD?

---

### Post by frozinfire on 2007-05-31
No. I just used the regular iso that I downloaded from the website.

---

### Post by oxalá on 2007-05-31
cool, thanks.
now only if i could get my Toshiba Portégé 3110CT to boot from the USB stick, i think i'd be in business.

---

### Post by frozinfire on 2007-06-01
No problem. :)

Does the Portege not support USB booting?

---

### Post by oxalá on 2007-06-01
it's a pretty old Portégé (Pentium II).
so far, it appears that it does not (that, or i am just not managing to configure it to do so).

i know that this worked on a Libretto, so there may be hope...

---

### Post by frozinfire on 2007-06-01
Are there any BIOS updates that you could download?

---

### Post by oxalá on 2007-06-01
yes, but i know that they won't help.
this particular flavor of Toshiba is near hopeless, it seems -- i may have to take the HD out, connect it to my desktop PC and install Ubuntu there before returning it to the laptop.

---

### Post by oxalá on 2007-06-01
...or, I could wait for [instLux]("http://instlux.sourceforge.net/") to work with Windows 98 (any day now, reportedly).

---

