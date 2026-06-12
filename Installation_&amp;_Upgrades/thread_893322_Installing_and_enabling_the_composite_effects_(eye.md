---
title: "Installing and enabling the composite effects (eye candy)"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by Yesideez on 2008-08-18
I've been browsing through the preferences and noticed (I think in Appearance - can't remember as I'm back on my XP boot) but when I select the bottom option for complete eye candy I get an error message saying not available.

Is this something that needs to be installed (I'm using the Live DVD with Linux Format Special) or is it a driver issue?

---

### Post by rohedin on 2008-08-18
Do you have the correct ATI drivers installed?

If not then you have to go to System> Hardware Drivers manager and then select 'ATI accelerated graphics driver' and make sure it's enabled. I'm on Kubuntu so I'm not sure but it's something like that.

---

### Post by Yesideez on 2008-08-18
Yes, when I first booted my installation it gave me that requester and I enabled it.

As for whether it's the correct ATI drivers I'm not sure - Ubuntu gave me alternate drivers. I did try looking for specific drivers and a link I was given yesterday pointed me to a website that did provide ATI drivers but it looked like by X1650 Pro wasn't supported so I'm still a little lost.

---

### Post by Yesideez on 2008-08-18
Just found this:
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

Seems this is the Mobility pack which supports my graphics card.

In the installation instructions it says this:
> If the initial installation of the driver was done via the Operating Systems package management software (rpm, apt, etc.) then please use that package management software to remove the ATI Proprietary Linux Graphics Driver.

My existing drivers were installed and activated by the system when it detected it wasn't set up right - is this what this text means? If so, how do I go about uninstalling the proprietry fglrx drivers using the RPM/APT? (whatever they are lol)

---

### Post by rohedin on 2008-08-18
Fglrx should be fine for running Compiz actually, I'm using it now.

Try running '  compiz --replace  ' from the terminal, post any output here.

---

### Post by Yesideez on 2008-08-18
Thanks rohedin, I'll try that as soon as I can get back into my Linux boot.

I'm having to use Windows right now as I only installed Ubuntu yesterday afternoon and am trying to get some discs backed up before I head off to work.

---

### Post by Yesideez on 2008-08-18
I just tried it and got this:
```
master@zebslinux:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```

---

### Post by meindian523 on 2008-08-18
Looks like your driver is blacklisted.Look here:
[http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

---

### Post by Yesideez on 2008-08-18
oooo!

I ran that mkdir command and nothing was returned to the shell. How do I know if anything worked?

When I try and enable the eye candy the message I get is "The composite extension is not available"

Any way I can get around this?

I just ran this after installing the X1600 series Mobility driver:
```
master@zebslinux:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

(gtk-window-decorator:13551): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:13551): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap
/usr/bin/compiz.real (core) - Fatal: No composite extension
```

---

### Post by Yesideez on 2008-08-18
I found this link:
[http://ubuntuforums.org/archive/index.php/t-698544.html](http://ubuntuforums.org/archive/index.php/t-698544.html)

Will try that when I get home from work later. Tried it just now and it failed for some reason (sorry, closed window but I tried this when it failed:
```
sudo sh ati-driver-installer-8-02-x86.x86_64.run --buildpkg Ubuntu/gutsy
```

---

