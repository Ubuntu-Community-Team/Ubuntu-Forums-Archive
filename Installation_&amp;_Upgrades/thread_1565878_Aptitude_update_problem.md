---
title: "Aptitude update problem"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by anfreita09 on 2010-09-01
Hello,

I'm currently experiencing a problem when trying to upgrade my system through aptitude (apt-get *). I can install programs, but whenever it tries do anything with the kernel I get this error:

E: linux-image-2.6.32-24-generic: subprocess installed post-installation script returned error exit status 2

This started about a month ago when I was trying to install some upgrade (with apt) which stalled and I unknowingly shut down the comp while it was running. 

I appreciate any help anyone has to offer.

Thanks,
Andrew

---

### Post by arrange on 2010-09-01
Just to make sure - it means you're not running on that kernel (2.6.32-24)```
uname -r
```is that right?

---

### Post by andrewthomas on 2010-09-01
I would try and reinstall initramfs-tools and initramfs-tools-bin

---

### Post by anfreita09 on 2010-09-03
I am running the kernel (2.6.32-24-generic).
How would I go about reinstalling initramfs-tools

---

