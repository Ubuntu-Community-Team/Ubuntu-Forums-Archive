---
title: "problems while upgrading from 7.10 to 8.04"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by pavaan on 2008-05-07
hello ,
  I m using 7.10 from sometime ..recently I tried to upgrade it to 8.04 over the net all the packages downloaded nicely and installation continued, in the middle of it power to my system was off. Then onwards whenever i tried to boot to ubuntu login screen appears, after logging in only blank screen is visible nothing else ..can someone help me how to get back all my settings and some important files in ubuntu

---

### Post by Rocket2DMn on 2008-05-07
If you are lucky, this is just an Xserver problem, so you can try booting into the recovery mode kernel and running
```
dpkg-reconfigure xserver-xorg
reboot
```
That will reset xorg.conf to a default detection.  Hopefully now you can get back into Ubuntu.
If that fails, you may need to boot from the LiveCD, mount your internal hard drive with your data, then mount a USB hard drive and copy your data from the internal to your external drive as a backup.  After you are sure you have everything, you can reinstall (a fresh install of Hardy) and reload your data onto the machine.

---

