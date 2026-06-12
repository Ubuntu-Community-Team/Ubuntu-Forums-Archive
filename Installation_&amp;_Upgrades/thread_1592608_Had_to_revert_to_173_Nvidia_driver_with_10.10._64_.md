---
title: "Had to revert to 173 Nvidia driver with 10.10. 64 bit"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by sjbaugh on 2010-10-10
I Upgraded from 10.04 64 bit to 10.10 64 bit. The upgrade seemed to go OK.

On reboot, it re-booted said:

Starting Up...

the text changed to a different font then the screen went blank and the monitor power light flashed continually (as it does when no video is present).

The boot up proceeded and I heard the bing-bing of the login screen followed by the normal start up tune and eventually the skype start up noise. but still no sign of video.

Going to Safe Mode I could start up in low-res graphics. I tried the nvidia configuration utility but it said I did not seem to have the nvidia X utility running. I looked at /etc/X11 and there did not seem to be an xorg.conf file (but there were a number of xorg.conf backup files).

The only way I have been able to get high res graphics is to revert to the 173 version driver using System>Administration>Additional Drivers

I am using an nvidia 8400GS.

It seems quite a bit slower than the last nvidia driver.

Hope you can help,

Steve

---

### Post by aero13972486 on 2011-08-02
I'm on 64-bit 11.04 GeForce6100 n405 and same problem.
I got latest drivers from nVidia yesterday (280.13 I think) and installed them manually. Still getting blank page canvas for large windows. This is so frustrating!

Now when I revert back to 173 and restart I don't even get the login page, just the purple screen of infinite patience.

How can I get my gnome2 desktop back?
ANy ideas please...........

aero

---

### Post by dino99 on 2011-08-02
the latest working is 280.04 (newers have issues) 

[https://launchpad.net/~portis25/+archive/test/](https://launchpad.net/~portis25/+archive/test/)

---

