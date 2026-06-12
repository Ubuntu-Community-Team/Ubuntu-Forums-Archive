---
title: "Laptop Install"
date: 2004-11-27
forum: Installation &amp; Upgrades
---

### Post by Prorixum on 2004-11-27
I previously had Fedora Core 2 running on my Toshiba Laptop (Sateliete 5005-S507), but have tried installing several other distros, yet none using a 2.6+ kernel seem to work. 

Each distro hangs on install, but often at different points. A few (including I *think* Ubuntu) hang on the "floppy" module. (The laptop has a detachable usb floppy drive.)

If anyone has thoughts, I'd love your help.

---

### Post by knappen on 2004-11-27
I had the same problem when installing Fedora core 2. I dont have a floppy so Fedora just stopped ...

Ubuntu however worked perfectly!

But that is what you expect from the best Linux distro :-)

---

### Post by knappen on 2004-11-27
By the way, I added "init 3" to grub and Fedora worked fine even without a floppy.

---

### Post by jdong on 2004-11-27
you only need the '3', the 'init' is extra and ignored.

---

