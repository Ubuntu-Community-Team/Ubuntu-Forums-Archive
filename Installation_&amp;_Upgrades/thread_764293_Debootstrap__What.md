---
title: "Debootstrap?  What?"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by metroidnemesis13 on 2008-04-23
Okay, so the hashes are the same. Why is linux not installing? I've tried to install 8.04, the alternate cd i386 three times and it ends with an error which reads something about a debootstrap? I tried different ways of partitioning it. What have I done wrong?

Thanks.

---

### Post by dstew on 2008-04-23
Did you check the CD integrity (opening menu choice)? Maybe it is a bad burn.

---

### Post by metroidnemesis13 on 2008-04-23
Yeah, that's the thing, when I boot it it comes up with the ubuntu logo and tells me for regular install, press enter.  For help, press F1.  It's not the regular menu I've seen in the pictures.  It's a pentium 3 750 mhz intel with 384 mb of ram, so it's old.

---

### Post by metroidnemesis13 on 2008-04-23
debootstrap is used to create a Debian base system from scratch, without requiring the availability of dpkg or apt. It does this by downloading .deb files from a mirror site, and carefully unpacking them into a directory which can eventually be chrooted into.

So, is my problem that the setup CD can't access the internet?  It's hooked in anyways.  Help!!1 x(

---

### Post by metroidnemesis13 on 2008-04-23
Kudos to you, dstew.  I figured out that the disc wasn't working because there were too many scratches on it when I burned the CD-RW.  I feel like an idiot.  Thanks.

---

