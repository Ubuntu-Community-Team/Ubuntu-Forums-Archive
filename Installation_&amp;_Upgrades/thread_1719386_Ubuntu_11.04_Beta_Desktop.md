---
title: "Ubuntu 11.04 Beta Desktop"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by doppel.ganger on 2011-04-01
I put Ubuntu 11.04 Natty Desktop Beta 1 on a flash drive using 7-zip and am trying to install it on a (this is all I know about it) an HP G71 laptop, but when I hit Esc (as instructed) to interrupt the boot process, when I hit USB DEVICE, It starts up with Windows. HELP!!!! Is there a way to do a basic install with wubi without booting up from the drive?!?!?!?!

---

### Post by uRock on 2011-04-01
What OS are you using to place the image on the USB?

---

### Post by doppel.ganger on 2011-04-01
Windows 7.

---

### Post by uRock on 2011-04-01
You need to use [PenDriveLinux]("http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe") or [Unetbootin]("http://unetbootin.sourceforge.net/") to place a bootable image on the USB.

---

### Post by doppel.ganger on 2011-04-01
give me a few minutes to do that

---

### Post by doppel.ganger on 2011-04-01
There is no UBUNTU 11.04 in Pendrive, so it doesn't show up in the SELECT ISO.

i gotta have dinner i won't beback for 30 mins

---

### Post by doppel.ganger on 2011-04-01
I'm Back!

---

### Post by doppel.ganger on 2011-04-01
Oh, I also have the ubuntu startup disk creator, i'll try that.

---

### Post by uRock on 2011-04-01
> **doppel.ganger said:**
> Oh, I also have the ubuntu startup disk creator, i'll try that.

That is what I used from within Ubuntu. The installer detected my grub and didn't over write it, so I had to boot 1010 and run update-grub.

---

