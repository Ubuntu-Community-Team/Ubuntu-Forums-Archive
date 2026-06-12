---
title: "wubi downloads the amd64 installation instead of i386"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by mosheho1 on 2010-09-19
Hi
I am trying to install Ubuntu with wubi.
When wubi starts, it downloads the amd64 version instead of the i386 version.
I have a pentium4 CPU, I should install the i386 right?
How does wubi decide which version to download and install?

---

### Post by howefield on 2010-09-19
Scroll down the page for the answer :)

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

> Why is the AMD64 version of Ubuntu getting downloaded and installed?
You probably have a 64 bit machine, the 64AMD installation is appropriate for all 64 bit architectures whether AMD or Intel.
Can I force Wubi to download and install a 32 bit version of Ubuntu?
Yes, either pre-download the appropriate 32 bit ISO manually and place it in the same folder as Wubi.exe or start Wubi with the "--32bit" argument.

---

### Post by sikander3786 on 2010-09-19
I think it is a bug with the new version of Wubi. See the following thread.

[http://ubuntuforums.org/showthread.php?p=9851992#post9851992](http://ubuntuforums.org/showthread.php?p=9851992#post9851992)

The OP was also worried that Wubi was downloading 64-bit instead of 32-bit, but in the end it was revealed that actually Wubi downloaded the 32-bit version. Let the download finish and see what happens.

---

