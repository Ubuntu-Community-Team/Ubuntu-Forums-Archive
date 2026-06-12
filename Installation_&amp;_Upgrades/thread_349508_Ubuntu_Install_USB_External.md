---
title: "Ubuntu Install USB External"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by jasrog on 2007-01-30
How do you exactly install Ubuntu on to external usb drive so that my internal drive is never affected and that i can boot into ubuntu every time i connect usb external drive?

---

### Post by logos34 on 2007-01-30
> **jasrog said:**
> How do you exactly install Ubuntu on to external usb drive so that my internal drive is never affected and that i can boot into ubuntu every time i connect usb external drive?

Provided your BIOS supports booting from USB or 'Other device', then all you'll need to do during install is make sure grub goes on the mbr of the usb external drive (and not to the internal as it will unless you specify otherwise).  Then you just set your bios to boot first from the usb and second from the internal hard drive.  When the usb drive is connected it will boot to the grub menu, which will give you a choice of linux or windows.  When it is not connected you will boot into windows.   

I think you can do this using the edgy livecd...when you come to the 'Ready to install' screen (see attachment), change the Grub location to **(hd1)** (which is how grub sees /dev/sda -- your usb drive). 

If it just gives you a choice of '(hd0)', then abort the install and use the alternate install CD instead.  See [this link]("http://www.ubuntuforums.org/showthread.php?t=80811").

(more [screenshots here]("http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html"))

---

