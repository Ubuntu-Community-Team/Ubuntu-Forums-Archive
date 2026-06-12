---
title: "Reinstalling ubuntu 10.10 from inside ubuntu 10.10 using pendrive"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by pancham on 2011-02-19
Few days back I installed Ubuntu 10.10 .iso using pendrive from windows 7. After meddling with ubuntu few problems started. Now I want to reinstall Ubuntu 10.10, but when i run Universal USB Installer to create bootable pendrive it is not working. So how to reinstall Ubuntu 10.10 using Pendrive from inside Ubuntu.

---

### Post by Sean Moran on 2011-02-19
> **pancham said:**
> Few days back I installed Ubuntu 10.10 .iso using pendrive from windows 7. After meddling with ubuntu few problems started. Now I want to reinstall Ubuntu 10.10, but when i run Universal USB Installer to create bootable pendrive it is not working. So how to reinstall Ubuntu 10.10 using Pendrive from inside Ubuntu.
I assume you mean 'pendrive' the same as a USB flash drive, which I think is fairly certain; just to be sure.

If you have a running Ubuntu 10.10 system whether on the pendrive or on the HDD, then the smoothest way I know, (and there might be better ways than I know), is to **sudo apt-get install unetbootin** which on 10.10 should install unetbootin4.71 and then open it, and select your ubuntu-10.10-desktop-i386.iso or the one you want to install, and make sure to select the blank formatted USB drive if you're running the current session from USB, then it should setup that newly formatted USB drive as a Live-CD with a few unetbootin extras.

I've never tried the USB Startup-Disk Creator, which I guess you mean by Installer, but I assume that only copies what is already installed, so it would copy the same problems from your current session to the USB drive.  Many experts seem to advise Unetbootin as the best way to go, although why that is exceeds my understanding.

---

