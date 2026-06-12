---
title: "advanced installation help"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by jtso8 on 2011-11-14
The problem is that I have just bought a new computer will all new components. My graphics card is too advanced and Ubuntu 11.10 - 10.10 will not display anything on during the installation process. I can install Ubuntu 10.04 but my wireless and graphics driver can be installed normally by Ubuntu. My graphics comes on with 10.10 but my wireless come on with 11.10. It takes a very long time to get a usable computer as I have to use a wired internet connection to upgrade. How would I get my wireless to work on Ubuntu 10.04? I thought about upgrading to the latest kernel (3.1 or something) but that didn't go so will.

---

### Post by vidtek on 2011-11-14
> **jtso8 said:**
> The problem is that I have just bought a new computer will all new components. My graphics card is too advanced and Ubuntu 11.10 - 10.10 will not display anything on during the installation process. I can install Ubuntu 10.04 but my wireless and graphics driver can be installed normally by Ubuntu. My graphics comes on with 10.10 but my wireless come on with 11.10. It takes a very long time to get a usable computer as I have to use a wired internet connection to upgrade. How would I get my wireless to work on Ubuntu 10.04? I thought about upgrading to the latest kernel (3.1 or something) but that didn't go so will.

Jts
During the boot process from the cd, **_immediately_** after the POST screen hit the F2 key and you will be able to choose a text install with minimal graphics.
You don't say what wireless card you have, but if oneric is the only kernel which recognizes the card, stick with oneric.

Tony

---

### Post by Quackers on 2011-11-14
What graphics card is being used?
You may need a boot option for 11-10, such as nomodeset

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by jtso8 on 2011-11-14
I have tried nomodeset but after rebooting I have a black screen as I had on my other a temps. I can install Ubuntu 10.04 but that takes a very long time to go though all the upgrades.  I have a AMD Radeon graphics cared.  Any ideas?

---

