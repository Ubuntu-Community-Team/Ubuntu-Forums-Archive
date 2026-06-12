---
title: "Using Ubuntu Installer for Windows"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by Mejorado on 2010-01-01
If I use [ ubuntu installer for Windows]("http://www.ubuntu.com/getubuntu/download-wubi") would it still allow me to daul boot? and what boot-loader will I be using?

---

### Post by SecretCode on 2010-01-01
Yes. It uses the same NTLDR that windows already has in place, and adds an entry to C:\boot.ini which loads ubuntu via grub (although you shouldn't see the grub menu).

---

### Post by tachuela on 2010-01-01
[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29)

---

### Post by Mejorado on 2010-01-01
..ah I see, Dual booting is possible. So there isn't any difference between his and using a live CD?

---

### Post by SecretCode on 2010-01-01
Big difference - you get a permanent file system to save data and install packages!

---

### Post by tachuela on 2010-01-01
Right. I'd never install with wubi.

---

### Post by SecretCode on 2010-01-01
> **tachuela said:**
> Right. I'd never install with wubi.

Nor would I now that I'm familiar with Ubuntu - but it was a good thing to do as a beginner.

---

### Post by tachuela on 2010-01-01
I got lucky; I guess.

---

### Post by Mejorado on 2010-01-01
> **SecretCode said:**
> Big difference - you get a permanent file system to save data and install packages!

Oh, well! LiveCD it is then ;)

---

### Post by Mark Phelps on 2010-01-02
The other big difference is that Wubi does not require you to mess around with shrinking your MS Windows to make room for Ubuntu.  If you're running Vista or Seven and are going to do a traditional dual-boot install, be sure to use the Vista or Win7 Disk Management utility to shrink the Windows partition; using GParted or the Ubuntu installer to do that runs the risk of corrupting the Vista or Win7 OS partition and rendering it unbootable.

---

