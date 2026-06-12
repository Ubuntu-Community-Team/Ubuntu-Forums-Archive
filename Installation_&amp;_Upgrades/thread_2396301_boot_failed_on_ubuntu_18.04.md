---
title: "boot failed on ubuntu 18.04"
date: 2018-07-13
forum: Installation &amp; Upgrades
---

### Post by sadtoot on 2018-07-13
i have an acer e5-575, which was previously running ubuntu 16.04.  automatic upgrade wasn't working so i installed 18.04 through USB.  booting from the USB works fine, and the installation doesn't seem to show any errors, but boot keeps showing "default boot device missing or boot failed".


[http://paste.ubuntu.com/p/CHFZDYdBFz/](http://paste.ubuntu.com/p/CHFZDYdBFz/)

---

### Post by westie457 on 2018-07-13
Have you tried setting 'Trust' on the new file? You almost certainly had to do that with the original installation.

---

### Post by sadtoot on 2018-07-13
i'm not sure what you're talking about.  i did have trouble on my first install, but i do not remember the steps i took to fix it, just a bunch of trial and error until something worked.

---

### Post by oldfred on 2018-07-13
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
 [https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 


You also have several obsolete UEFI entries.
Once you know which one works, you can and should delete the others.
To see entries like shown in Boot-Repair report:
sudo efibootmgr -v
      
 The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete example in man page:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

