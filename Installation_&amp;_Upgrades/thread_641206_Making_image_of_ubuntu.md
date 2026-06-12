---
title: "Making image of ubuntu"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by klaasth on 2007-12-15
Is it possible to make an image of a linux partition in command line. Or do you have to do it with a bootle program like ancronis directory suite.

Thank you!

---

### Post by scxtt on 2007-12-15
it's generally not a good idea to make an image of an "active" filesystem - so it's in your best interest to boot something that doesn't use the f/s you want to backup ...

LVM has snapshots, which is pretty cool ... i still need to work something out to get good backups using them.

---

### Post by JangMunho on 2007-12-15
Use a live CD, then try to use "tar" command to do so.
Tar command will copy the attribution of a file as well as its content.

---

### Post by scxtt on 2007-12-15
> **JangMunho said:**
> Use a live CD, then try to use "tar" command to do so.
Tar command will copy the attribution of a file as well as its content.you have to explicitly tell it to.

---

