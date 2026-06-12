---
title: "GRUB2 woes with 10.04"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by shortridge11 on 2010-05-04
I had 9.10 on my old setup, which is 5 drives in one machine.  I booted 10.04 off usb (courtesy of Unetbootin =D) and installed it.  After reboot, the system dropped to grub-rescue and wouldn't respond to normal commands like 'help' so I assumed i had a bad image or bad usb.  I redownloaded the iso, redownloaded Unetbootin, and used a different brand of usb drive just for fun. Same issue, I'm sure the system installed fine, just having troubles navigating around grub2.  I've checked out the wiki, etc, and after trying the things they recommend i'm here as a last resort.  the one command that works is 'ls' and it gives me
```

grub rescue>ls
(hd0) (hd0,6) (hd0,5) (hd0,3) (hd0,1) (hd1) (hd1,1) (hd2) (hd2,1) (hd3) (hd3,1) (hd4) (hd4,3) (hd4,2) (hd4,1) (fd0)

```

any ideas?

---

### Post by shortridge11 on 2010-05-04
also, i'm assuming 10.04 shipped with grub2...

---

### Post by shortridge11 on 2010-05-04
It's looking like i'll have to uninstall grub and reinstall using the livecd...was hoping to avoid doing that =\

---

### Post by shortridge11 on 2010-05-04
booting from the livecd i used
```
sudo dpkg-reconfigure grub-pc
```

and it failed to install to all drives.

---

### Post by shortridge11 on 2010-05-04
all else failing i ended up reinstalling grub via
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
if anyone else has any problems and grub rescue is unresponsive, please save yourself time and just reinstall, it's really fast.

---

