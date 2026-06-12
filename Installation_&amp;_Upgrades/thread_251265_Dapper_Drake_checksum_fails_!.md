---
title: "Dapper Drake checksum fails !?"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by MdaG on 2006-09-05
I'm trying Dapper Drake 6.06.1. The md5 on the ISO is correct, but the checksum fails when I check it upon booting with the CD. I'm currently trying to switch from Gentoo due to an annoying update (gcc 4.1 and glibc 2.4 + change of CHOST) that will take a week (at least) to perform. Anyone know how to get a working CD? I don't dare install from a CD that fails checksum.

This is my ms5sum:
```
fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso
```

---

### Post by chicken101 on 2006-09-05
Try burning it at a lower speed.  Maybe that would help.  Also, try to see if you can open the iso in windows (using winrar).

---

### Post by kostkon on 2006-09-05
Yeah, try a 4x speed write of the iso.

---

### Post by MdaG on 2006-09-05
I did burn it at a speed of 4x (it took little more than 20 min) and opening it using winrar works fine :confused:

---

### Post by confused57 on 2006-09-05
Did you burn it "as an image", not as a data cd, nor as a bootable cd...as described here?:

[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)

The iso has to be burned to cd "as an image".

---

### Post by nanbudh on 2006-09-05
yes u must burn the iso file as an image. for example in nero burner (windows) u have an option of burning an image. do that and it should work.

---

### Post by MdaG on 2006-09-05
Yes, I burned it as an image. Is it possible to boot from it otherwise?

---

