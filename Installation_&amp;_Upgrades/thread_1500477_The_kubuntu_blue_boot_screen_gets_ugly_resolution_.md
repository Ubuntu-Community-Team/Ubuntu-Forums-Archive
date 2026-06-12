---
title: "The kubuntu blue boot screen gets ugly resolution after installing nvidia drivers"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by Istrebitel on 2010-06-03
Greetings!

I have recently tried kubuntu and had installed it twice already. Each time after installation (and during it) a nice high resolution boot screen is shown (kubuntu written on it on a blue background and dots changing colors).

When i install nvidia drivers, though (i have GTX 280), the boot screen changes to some ugly low resolution one. Like going from 1600x1200 to 800x600. The word and dots become larger and look "crude" like pixelated...

Is there any way to revert this to normal "high res" look or i have to deal with it if i want to have nvidia drivers installed? Or is it not drivers problem?

---

### Post by wojox on 2010-06-03
Try this [Ubuntu 10.04 – Default Login Screen Resolution]("http://chrisjakeway.wordpress.com/2010/05/19/ubuntu-10-04-default-login-screen-gdm-resolution/")

---

### Post by Istrebitel on 2010-06-03
Thank you will do when i get back to my linux...

---

### Post by Istrebitel on 2010-06-03
no this is for ubuntu apparently i dont have said folder (Init) in the /etc/gde/ folder

I found this: 
[https://bugs.launchpad.net/plymouth/+bug/571567](https://bugs.launchpad.net/plymouth/+bug/571567)
[https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/551290](https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/551290)
[http://forum.kde.org/viewtopic.php?f=66&t=20494&start=10](http://forum.kde.org/viewtopic.php?f=66&t=20494&start=10)

As usual (this is starting to annoy me with linux, why do people give advices that DO NOT WORK? and how does it happen that some people have files i dont have on the same distributive installed system?) people are saying that the "fix" works. "fix" starts with:
> I figured out that I only have to add the following 3 lines to  /etc/X11/xdm/Xsetup:

And person who has kubuntu 10.04 says that the fix works for him... But i have freshly installed kubuntu 10.04...
AND there is no such directory "xdm"!!!!

---

### Post by Istrebitel on 2010-06-03
and finally, adding what they suggest to /etc/kde4/kdm/Xsetup does not work at all. i tried adding

xrandr --output VGA_1 --mode 0x3f
xrandr --output DVI-I_1/digital  --mode 0x58
xrandr --output DVI-I_1/digital --right-of VGA_1

as well as
xrandr --output default --mode 1024x768

still not working

---

