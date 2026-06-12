---
title: "USB Automatic installation"
date: 2015-07-24
forum: Installation &amp; Upgrades
---

### Post by jarrod2 on 2015-07-24
Hello, I was wondering if there was a way that I could make a USB that automatically installed ubuntu with pre-defined setting controlled by a text file or similar. 

Thanks, Jarrod

---

### Post by sudodus on 2015-07-24
You can install a portable installed system, that is stored as

1. a compressed tarball. [The One Button Installer](https://help.ubuntu.com/community/OBI), OBI,  is a tool for doing that, (create it with mktbl or zmktbl, and install it with the OBI itself.

2. a compressed ***dd*** image. Create it manually, and install it with [mkusb (safer)](https://help.ubuntu.com/community/mkusb) or dd (directly).

3. a [Clonezilla](http://clonezilla.org/) compressed image (a directory with several files). Clonezilla is the tool to create and install with this method.

-o-

If you make an [OEM system](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview), it can be tuned with individual user ID and password by the end user after the installation.

---

