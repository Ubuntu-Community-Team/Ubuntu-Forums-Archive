---
title: "Installing from USB"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by Mikey_MW on 2007-07-22
I'm trying to fix a laptop - and I figure a reinstall is in order. Problem - no bootable cdrom, no bootable usb. The only thing that is bootable is the hard drive (at the time, dell despised linux users so it wanted to lock them out). 

Anyway, I've found one thing that still works on the laptop - GRUB. So is it possible to boot the hard drive to grub, then use that to boot to an iso on a usb? I've been google-ing for ages, and can't seem to find exactly what I'm looking for...

---

### Post by raja on 2007-07-22
Since I have a thinkpad without an optical drive, I have always had to do my installations wthout a cd. If you can PXE boot, you can install using netboot. What you asked about it also possible. These links may be what you want - 
[https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd](https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd)
[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

---

### Post by Mikey_MW on 2007-07-22
PXE boot? I've heard of it, but not many of the guides were easy to understand. I'm going to try that. Heres what I've got...

 - One working ubuntu 6.10 desktop
 - One broken ubuntu laptop
 - A D-Link 4Port Router
 - A few ethernet cables

Do I need anything else?

---

### Post by raja on 2007-07-22
The first thing to do is to see if your Bios supports PXE booting. 
If it does, then you can follow the instructions [here]("https://help.ubuntu.com/community/Installation/Netboot") to setup a server on the desktop and boot the laptop from it.

---

### Post by Mikey_MW on 2007-07-23
Awesome, trying to follow that PXE guide. And yes, the laptop does boot from PXE

---

