---
title: "Install edgy with no gui, then install kde-core?"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by Kirky_D on 2007-01-17
Hi there. I would like to install the base ubuntu system with no extra apps, then after that is complete i would like to install kde-core to get the base kde installation.

I tried doing the commandline only install (from kubuntu alternate cd) then apt-getting kde-core, which see,ed to work as it installed a mass of programs and libraries.

I tried startx but it came up with errors.

I tried looking at xorg.conf but it wasn't there.

Is there a way to do this kind of installation?

Cheers all!

---

### Post by taurus on 2007-01-17
I would install the server version and then install kde-core after that.

Now, what's the error message when you try to start X with startx from a terminal?

---

### Post by Kirky_D on 2007-01-17
Unfortunately i cant look at the error message at the moment because i installed the normal way.

Are you saying download and install using the server CD rather than the alternate CD?

---

### Post by taurus on 2007-01-17
Yes, if you want a barebone machine.  At least that's what I would do.

---

### Post by Kirky_D on 2007-01-17
And then just install kde core and reboot? or startx?

thanks for your help

---

### Post by taurus on 2007-01-17
If you want to boot into GUI login screen, then you need to install kdm.  Otherwise, you can log in and then run **startx** to start your KDE session.  I suppose when you install kde-core, it would also install Xorg on your machine too.

---

### Post by Kirky_D on 2007-01-17
Thanks Taurus.

I'll Give it a go now!

---

### Post by NeoLithium on 2007-01-17
Also to save time, you can use hte command line browswers to check the forums as well, if anything happens, so you don't have to reinstall with the normal Ubuntu disk. I'm not sure if they come standard, but you can just use (from the CL)

links [http://www.ubuntuforums.org](http://www.ubuntuforums.org)

That little browsers' helped me a LOT in the past ;)

---

### Post by Kirky_D on 2007-01-17
ok, so i have installed using the server CD, i then installed kde-core, then tried installing kdm, which it said was already installed, but while looking through the end of the packages to be installed i noticed that xserver-xorg was not selected to be installed. so i installed that.

i then tried startx which gave me the following errors: (at the end of the error message because there was more further up that i couldn't see)

(EE) xf86OpenSerial: Could not open device /dev/wacom

Could not init font path element /usr/shar/fonts/X11/(a few different names were here)

Any ideas?

---

### Post by taurus on 2007-01-17
```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by Kirky_D on 2007-01-17
Should have said that i tried that aswell. sorry

---

### Post by Kirky_D on 2007-01-17
Ok so i figured it out. After installing xserver-xorg you also need to install 'xorg' Which kde-core clearly does not.

Could this be classed as a dependancy problem?

---

