---
title: "Ubuntu 11.10 Atheros wifi problems"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by fernandoch on 2011-10-15
Some of us after upgrading to Ubuntu 11.10, we are not able to connect the wifi. My chipset is Ahteros AR9285. Here is another thread about the same problem

[http://ubuntuforums.org/showthread.php?t=1859633](http://ubuntuforums.org/showthread.php?t=1859633)

What can we do? There are still no backports for oneiric

[https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)

Or at least I did not find them...

---

### Post by prosist on 2011-10-15
same problem here

---

### Post by fernandoch on 2011-10-15
I forgot to mention that I am using the 64 bit version.

Any ideas?

---

### Post by fernandoch on 2011-10-18
I fixed it. Edit the file

/etc/modprobe.d/blacklist.conf

and add this

blacklist acer-wmi

Then reboot and your wifi should work ;)

---

