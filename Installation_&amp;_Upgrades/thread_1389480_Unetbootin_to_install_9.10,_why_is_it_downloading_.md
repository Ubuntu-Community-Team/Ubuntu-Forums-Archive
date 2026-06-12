---
title: "Unetbootin to install 9.10, why is it downloading a torrent?"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by Brinstar on 2010-01-24
i am installing Karmic 64-bit within Windows 7 using a unetbootin-type install, for some reason, it is not installing using the install files from the USB, after starting wubi.exe, it is now downloading ubuntu.9.10desktop.amd64.iso.torrent.

why??? :confused:

---

### Post by darkod on 2010-01-24
Unfortunately it seems wubi.exe was designed that way. It always downloads the full ISO from internet.
The only way to make it not download, is if you already have the ISO, you need to put both wubi.exe and the ISO image (unpacked) in the same folder, then start wubi.exe. In that case it will use the ISO from the same folder.
You could probably recreate the ISO from the files on the usb stick.

---

### Post by Brinstar on 2010-01-24
thanks for the info

someone should let the developer of unetbootin know about this.

---

