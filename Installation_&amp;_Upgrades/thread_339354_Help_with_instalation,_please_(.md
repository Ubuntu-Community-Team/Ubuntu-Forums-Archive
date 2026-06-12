---
title: "Help with instalation, please :("
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by yoguko on 2007-01-15
Hello

We are trying to install from Ubuntu live CD (32bit) onto an AMD64 with an Nvidia 6600GT.

The Grub starts, however, after that, we heard the music, but have no video. Instead we have a bunch of multicoloured vertical lines...

Newbies here, so please go slowly :)

Thank you!

---

### Post by Richard Kut on 2007-01-16
Hello yoguko, and welcome!  An AMD64 is a 64-bit CPU, and so the 32-bit version which you tried to run will probably not do very well. Please get the 64-bit version of Ubuntu here:

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

Select a geographic region closest to you, and then select the "Other" category CD, which includes the 64-bit version which you will need.

I hope that this helps. Good luck!

---

### Post by bulldog on 2007-01-16
> **Richard Kut said:**
> Hello yoguko, and welcome!  An AMD64 is a 64-bit CPU, and so the 32-bit version which you tried to run will probably not do very well. Please get the 64-bit version of Ubuntu here:

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

Select a geographic region closest to you, and then select the "Other" category CD, which includes the 64-bit version which you will need.

I hope that this helps. Good luck!

I have to correct you,the 32bit version will do fine,the 64bit is a little tricky and certainly not a good start for a beginner.

@TS Reboot and use the recovery mode which brings you to a console with root permission.
Log in and type ```
dpkg-reconfigure -phigh  xserver-xorg
```
After that type ```
startx
``` and if that won't work ```
/etc/init.d/gdm start
```

Hope you get it working.

---

