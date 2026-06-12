---
title: "Installation from external CD fails to find it during installation"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by darrelljon on 2008-08-18
I have a laptop on which I am trying to install Kubuntu 8.04 alternate cd (text installation).

It boots and lets me choose what to do e.g. Start Kubuntu installation, memory test, boot from hard disk etc. However during the installation it fails to find the CD asking me for a location /dev/cdrom or similar.

The laptop doesn't have a floppy disk drive either. Booting from USB seems to be an enabled option in the BIOS too and the external CD drive is connected via 2 USB ports.

I tried a few normal live CDs and some (but not all) have the same problem - they boot but then forget where the CD drive is connected. What is the location (/dev/???) I need to enter to proceed with the installation?

---

### Post by meindian523 on 2008-08-18
/dev/cdrom is the cdrom drive.

---

### Post by darrelljon on 2008-08-18
> **meindian523 said:**
> /dev/cdrom is the cdrom drive.

Tried that and it doesn't work.

---

### Post by darrelljon on 2008-08-19
If it helps my laptop is a Medion MIM 2080.

Also, I can get into a system shell (pressing Alt+F2) and type ls /dev but it just gives me a huge list. If I type ls /dev/usb it gives me 6 results, if I remember rightly they are;
/dev/usb1.1_eo00
/dev/usb1.1_eo81
/dev/usb2.1_eo81
/dev/usb3.1_eo81
/dev/usb4.1_eo00
/dev/usb4.1_eo81

If I can understand ls /dev better maybe I can sort it out.

---

