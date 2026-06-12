---
title: "KDE won't start, Kubuntu doesn't get pasted x-windows"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by Oceanic on 2007-08-21
I am not able to use my Kubuntu feisty for 4 days now - getting desparate.

Please, does anyone have a clue ???

KDE won't start: booting goes till the black screen with the x shaped cursor of X-windows, then totally black and then  the x-shaped cursor reappears, then black etc etc. 

I have tried recovery modes, also of previous kernels. At some point I can
1) give my root password
2) continue with control d
Control D didn't resolve the issue...

This :    tail -f /var/log/Xorg.0.log
Resulted in :

[COLOR="Red"]Error opening /dev/wacom: No such file or directory
(EE) xf86OpenSerial : cannot open device /dev/wacom
no such file or directory
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial : cannot open device /dev/wacom
no such file or directory
Error opening /dev/wacom: No such file or directory
(II) configured Mouse: ps2EnableDataReporting: succeeded
Could not init font patch element /usr/share/fonts/X11/Cyrillic, removing from list!
Could not init font patch element /usr/share/fonts/X11/Type1, removing from list![/COLOR]


Thanks very much in advance, your help is greatly appreciated !

Cheerrrrrrssssss

---

### Post by jim_p on 2007-08-21
It seems like a problem witha some wacom tablet to me.
Try editing your /etc/X11/xorg.conf file and removin the section that says about wacom stuff.
It starts with the words "Section InputDevice" and ends with "EndSection".

Here is mine```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection
```

---

### Post by Oceanic on 2007-08-22
Thanks Jim_p

I have tried that but to no avail ](*,)

Seems that the problem is KDE

---

### Post by Benson17 on 2007-08-28
Any ideas? Can't login to my Ubuntu box since some days... :mad:

---

### Post by BillDozer on 2007-08-28
Try setting your device driver to vesa and see if that solves the strange behaviour.

---

### Post by Marat Galiev on 2007-08-28
You have installed system?
Try this:
after error messages press ctrl+alt+F2

login in text mode
sudo nano /etc/X11/xorg.conf
edit section 
"driver nvidia"(or driver "ati")
to driver "vesa".
sudo /etc/init.d/gdm restart
or boot with live-cd and mount you linux partitions and edit you xorg.conf file.

---

