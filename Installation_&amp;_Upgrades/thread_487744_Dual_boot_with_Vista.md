---
title: "Dual boot with Vista"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by gkennery on 2007-06-29
I'm having trouble dual booting with Ubuntu. Here's my dilemma:

I partitioned my drive correctly, but when using the Ubuntu Installer, it does not recognize Vista. This is my second attempt at doing it, the first time was nearly fatal.

Because Ubuntu isn't recognizing Vista on installation, last time, it completely ruined the MBR and I got the dreaded "No Operating System Found" error. I repaired the MBR and here I am again.

The Migration Assistant for some reason can not see Vista.

Would there be a way for me to not install a boot loader and configure through windows? Or is there a way to force recognition of another operating system?

---

### Post by confused57 on 2007-06-29
You could install grub to the root partition, then use Vista to boot Ubuntu:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

