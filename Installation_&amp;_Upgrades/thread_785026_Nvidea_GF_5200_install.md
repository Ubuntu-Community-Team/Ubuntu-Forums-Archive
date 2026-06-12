---
title: "Nvidea GF 5200 install"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by illbashu on 2008-05-07
I upgraded from 7.10 to 8.04 and i had installed the video card fine on 7.10 and it worked fine but after the upgrade it wont find my card and i installed the drivers and it is saying it is in use but it acting like its not. i am stuck with a max res of 800x600 (:() and i need to know how to install my video card and get it actually work. i tried to install the .run file of the drivers (that i got from nvidia's site) but it is saying i am running "x severs" and i have to turn it off :/ how do i get the drivers to actually work? :mad:

---

### Post by illbashu on 2008-05-07
bumpage!!!

---

### Post by N.N. on 2008-05-07
Perhaps the drivers are actually installed and functioning properly, but the refresh rates are incorrectly set in your /etc/X11/xorg.conf file. Try running the following command in the terminal:
```
glxinfo | grep rendering
```
If it outputs "direct rendering: Yes", then the drivers should be properly installed, and you should then be able to enable higher resolutions by specifying the proper vertical and horizontal refresh rates for your monitor in your /etc/X11/xorg.conf file (see [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) and [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292) for information on how you do this).

I have the same video card as you, and I haven't encountered any problems with the way the Restricted Driver Manager installed the drivers for it.

---

### Post by illbashu on 2008-05-07
this is what i got....

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

---

### Post by N.N. on 2008-05-07
> **illbashu said:**
> this is what i got....

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```
It seems that either the drivers aren't actually installed properly after all or that xorg isn't recognizing them any more. If the latter is the case, you could try to reconfigure xorg by typing the following command in the terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
Follow the instructions in the guide and make sure that the video card drivers are set to "nvidia". Then reboot for the changes to take effect.

If that doesn't help, you could try to disable the driver in the Restricted Driver Manager and then re-enable it. I'm afraid I can't give you other advice than that. Hope that someone with more experience will drop by and help you out. :(

EDIT: In case you want to try to install the drivers from NVIDIA's website, perhaps [this]("http://ubuntuforums.org/showthread.php?t=596875") guide can be of use to you.

---

### Post by illbashu on 2008-05-07
i did those and it didn't work :( 

i dont get how to install the nvidia drivers every time i type ```
sudo /etc/inid.d/gdm stop
``` it takes me to a screen with a blinking "-" and i cant use my keyboard :/
--------------------------------------------------
i am trying envy... ill post if i get it working.
---------------------------------------------------
it didn't work. every time i restart my comp it says something like "could not detect screen and graphic card run in low graphics?, and then it says configure (which does nothing, i changed the driver to nvidia from vesa? and changed my monitor to 1600x1200 and it did nothing :/) and it says continue and shutdown....

---

### Post by illbashu on 2008-05-07
bump! when i turn off the drivers from the hardvare drivers (and restart) the res get stuck at 1600x1200 ??? :/

ok i went to the screen res thing and it worked, it changed to 1024x786! i checked the hardware drivers program and it says its in use but its not checked off :/ and when i went to turn on compiz it said "desktop effects could not be turned on :/ compiz worked fine on 7.10 for me :/ how do i get it to turn on?

i got it fixed 

[http://ubuntuforums.org/showthread.php?t=765104&page=2](http://ubuntuforums.org/showthread.php?t=765104&page=2)

---

