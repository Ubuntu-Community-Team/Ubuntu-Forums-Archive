---
title: "Ubuntu black screen"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by Speedfx on 2011-03-18
I have installed Ubuntu desktop edition with Wubi. Ubuntu shows up in the Boot Menu of my pc. After selecting it it says the installation was completed. Then the option to press ESC for other boot options, after the countdown my pc is still running but my monitor says there is no signal.
I can press ESC for the boot options, but running in other modes gives the same result

I have an old nVidia 6200SE Turbocache, my monitor is also a tv-screen(well actually my tv is my monitor). I'm currently using Windows XP 32-bit(CPU: Pentium IV 2.93GHz). But I'd like to get Ubuntu 10.10 working on this desktop.

---

### Post by bcbc on 2011-03-18
See post #8 in this for specifying nomodeset as a boot option for Wubi installs [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Then after installing, when you boot into Ubuntu (the next boot) see post#1 for overriding the boot options manually (ignore where it says "Not for Wubi").

Nomodeset is generally required for nvidia cards. (Hopefully this will be fixed in the next release)

---

### Post by Speedfx on 2011-03-19
> **bcbc said:**
> See post #8 in this for specifying nomodeset as a boot option for Wubi installs [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Then after installing, when you boot into Ubuntu (the next boot) see post#1 for overriding the boot options manually (ignore where it says "Not for Wubi").

Nomodeset is generally required for nvidia cards. (Hopefully this will be fixed in the next release)

Yup adding nomodeset as a boot option solved my problem. Thanks alot, loving ubuntu atm :).

---

