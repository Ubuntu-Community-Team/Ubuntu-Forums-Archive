---
title: "Installtion Trouble"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by odu on 2007-12-31
I'm having difficulting running the live CD & installing.

When I try to run any of the live CDs (kubuntu 7.10, ubuntu 7.10, ubuntu 6.06, with either 32 or 64 architecture), it shows the splash screen, completes the loading, and gives me the error:
 "bcm43xx: Error: Microcode "bcm43xx_microcode.fw" not available or load failed."  Afterwhich, it proceeds to start loading gnome/kde, but ends up with the graphics being scrambled, and the computer locks up.

I can load the live CD fine in the safe graphics mode, and proceed to install.  When I restart the computer after installling, it tells me, "Error loading the operating system".

I'm totally at a loss here, I've been trying to find a solution in older threads, and searching google.  I've been able to install Ubuntu and Kubuntu on other systems with no problems (other than minor ones).

Any advice would be greatly appreciated! Thanks!

Computer Specs:
AMD X2 4600+
BFG Geforce 7800 GT
2GB Ram

---

### Post by Pumalite on 2007-12-31
Are you wired to the Internet during installation?

---

### Post by odu on 2007-12-31
No, my computer isn't wired to the internet during the installation.

---

### Post by Pumalite on 2007-12-31
Get wired. Configure your wireless later.

---

### Post by odu on 2007-12-31
I'm not worried about configuring my wireless, as that can be done at a later time.  My current issue is trying to install Ubuntu at all.  Every attempt ends with "Error loading the operating system".  It seems as if Ubuntu installs, but Grub loader never gets installed/configured properly.

---

### Post by Pumalite on 2007-12-31
Is best to be wired to the Internet in my experience. Beyond that, you should look at your iso; do an md5sum, burn at 4x, etc. Install again with your new CD.

---

