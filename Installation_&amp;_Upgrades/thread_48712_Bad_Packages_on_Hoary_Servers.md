---
title: "Bad Packages on Hoary Servers"
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by electronerdz on 2005-07-13
I seem to think there are some problems with the packages on these servers:

I also tried to upgrade Mozilla and it needs libcairo1, and got the same thing. So I downloaded it manually, and used dpkg, but it told me that it wasn't a valid .deb file.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2_i386.deb)
  MD5Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu1_i386.deb)
  MD5Sum mismatch

---

### Post by electronerdz on 2005-07-13
Nevermind... I read on the Gaming forum to just remove the "us" on the archive sites, as there is some problem with the us servers. Maybe they were hacked like the debian servers :-p

---

