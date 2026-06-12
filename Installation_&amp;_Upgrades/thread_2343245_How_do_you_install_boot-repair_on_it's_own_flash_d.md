---
title: "How do you install boot-repair on it's own flash drive instead of a disk?"
date: 2016-11-14
forum: Installation &amp; Upgrades
---

### Post by PopsTheSailor on 2016-11-14
I have an older laptop and the cd player no longer works. I  blew up grub and needed boot-repair but I couldn't find any directions on how to install it to a USB drive instead of a disk. When i tried Brasario to burn the iso, there was no option for the USB drive. Luckily I was able to carve out some space on my HDD and install a fresh install of ubuntu which fixed grub. I then booted on my real partition and move grub over so I'm back up and running but would like Boot-Repair on a USB in case it happens again. 

Note: when I tried the directions on how to install BR to a live usb stick, BR would run but never fix grub and didn't log any errors.

---

### Post by oldfred on 2016-11-14
Boot-Repair has its own ISO as live system with it already included.
But not sure what version ISO still is (update of 2014-11-30). It was an older Lubuntu so it still fit on CD, but flash drive recommended if UEFI.
[https://sourceforge.net/projects/boot-repair-cd/files/](https://sourceforge.net/projects/boot-repair-cd/files/)

You can use any Ubuntu live installer and add Boot-Repair, but have to re-add each time you reboot.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

[https://sourceforge.net/projects/boot-repair-cd/?source=recommended](https://sourceforge.net/projects/boot-repair-cd/?source=recommended)
[https://sourceforge.net/p/boot-repair-cd/home/Home/](https://sourceforge.net/p/boot-repair-cd/home/Home/)

---

### Post by PopsTheSailor on 2016-11-15
oldfred,
I guess I wasn't clear in my post. In fact, I think I'm going to repost my need to make it more clear. I have the ISO, I need to know what program I can use to burn an ISO file onto a flash drive since my DVD drive no longer works. I tried Brasario but I didn't see an option to burn to a flash drive, only a CD drive.

---

### Post by oldfred on 2016-11-15
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]https://wiki.ubuntu.com/Win32DiskImager/iso2usb
[https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)

[/URL]

---

