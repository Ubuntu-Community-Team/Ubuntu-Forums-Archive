---
title: "How to Triple Boot Win7, OS X, and Ubuntu"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by streetlightman on 2010-02-07
Hey everyone,
 
I current have Windows 7 Pro x86 and OS x86 10.5.7 installed on my hard drive and can dual boot between them using the Vista Bootloader configured with EasyBCD.
 
I want to be able to triple boot and add Ubuntu to the mix. How do I do this? I want to put it on a separate partition but I'd like to keep the Vista Bootloader. How can I install Ubuntu and make this work?
 
Thanks!

---

### Post by drpjkurian on 2010-02-07
Hi
Please visit this thread of Favux, It might help you
[http://ubuntuforums.org/showthread.php?t=988916](http://ubuntuforums.org/showthread.php?t=988916)

---

### Post by Mark Phelps on 2010-02-08
> **streetlightman said:**
> ... I want to be able to triple boot and add Ubuntu to the mix. How do I do this? I want to put it on a separate partition but I'd like to keep the Vista Bootloader. How can I install Ubuntu and make this work?

Just make sure that you do NOT install GRUB to the MBR of the disk.  That will overwrite the Vista MBR.  Install GRUB to the Ubuntu partition.  It's more work, but it will leave the Vista MBR intact.

---

