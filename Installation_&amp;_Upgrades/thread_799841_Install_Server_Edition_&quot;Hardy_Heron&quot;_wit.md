---
title: "Install Server Edition &quot;Hardy Heron&quot; with GUI"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by Lapp-Same on 2008-05-19
How/ what is the commands for installing the simplest desktop GUI on Ubuntu 8.04 Server Edition "Hardy Heron"


-Christoffer-

---

### Post by galileon on 2008-05-19
sudo apt-get install ubuntu-desktop, i'd say...

---

### Post by Lapp-Same on 2008-05-19
> **galileon said:**
> sudo apt-get install ubuntu-desktop, i'd say...

and it are clean with no orginal applications installed?

I want it to be most possible clean with no other stuffs, only what it installs... maybe only with a command console

---

### Post by dstew on 2008-05-19
You could start with the x-window-system package:```
sudo apt-get install x-window-system
```After that you can take your pick of a variety of x-window managers. See [this Wikipedia article]("http://en.wikipedia.org/wiki/X_window_manager"). The [Xfce desktop environment]("http://packages.ubuntu.com/hardy/xfce4"), based on the Xfwm windows manager might make a nice minimal desktop environment.

---

### Post by Lapp-Same on 2008-05-19
> **dstew said:**
> You could start with the x-window-system package:```
sudo apt-get install x-window-system
```After that you can take your pick of a variety of x-window managers. See [this Wikipedia article]("http://en.wikipedia.org/wiki/X_window_manager"). The [Xfce desktop environment]("http://packages.ubuntu.com/hardy/xfce4"), based on the Xfwm windows manager might make a nice minimal desktop environment.

Thanks!

---

### Post by aysiu on 2008-05-19
*x-window-system* is now called *xorg*

I'd go with ```
sudo apt-get update && sudo apt-get install xorg icewm
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by Lapp-Same on 2008-05-19
> **aysiu said:**
> *x-window-system* is now called *xorg*


Thanks i did try the first one but that one didn't work soo i will try this one when i get time and hope it work

Thanks for you're help 


But this is the simplest desktop i can get right?

---

### Post by aysiu on 2008-05-19
> **Lapp-Same said:**
> Thanks i did try the first one but that one didn't work soo i will try this one when i get time and hope it work

Thanks for you're help 


But this is the simplest desktop i can get right?
Yeah, it basically has nothing.

xorg just allows you to have graphics of any kind, and IceWM (or Fluxbox, or PekWM or whatever lightweight window manager you want to install) will allow you to open windows for applications and *that's it*. No desktop icons. No fancy effects.

---

### Post by Lapp-Same on 2008-05-19
> **aysiu said:**
> will allow you to open windows for applications and *that's it*. No desktop icons. No fancy effects.


Like a Dedicated server program for a game? or other server programs from games or applications?

-Christoffer-

---

### Post by Xyem on 2008-05-19
Just a quick warning.

I have done a command line install of Hardy in QEMU and then tried adding xorg to it ( along with wdm and fluxbox for a light set-up ) and it doesn't work.

They have moved away from having the configuration in xorg.conf to auto-detection. In QEMU, at least, it doesn't work. I think it might have something to do with the fact a minimal install + xorg + dm + wm does not include the files used by this new auto-detection ( I think it is something like ~/.gnome2/monitors.xml ).

See this bug for ( possibly ) more info: [Bug #182743]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/182743")

Doing a full install in QEMU, results in a working display but without the ability to change resolution ( if I recall correctly ).

I'll be sticking to 7.10 and backports. Auto-detection is fine until it doesn't work and every tool you have for fixing it seems to be removed. I want my configuration in xorg.conf where 1) everyone else has it (?) 2) I can fix it :P

---

### Post by galileon on 2008-05-19
as far as i understand it, you can still forcefully create/maintain an xorg.conf to your liking, and it shud override the autodetection... so if u got an old copy lying in the backups, it shud work...

if they changed it so that doesnt work anymore, then ubuntu is going foobar...

---

### Post by Xyem on 2008-05-19
I use virtual machines to experiment with things before putting them on my server ( which is running 7.10 ). I wanted to test Tagsistant. Should have taken me a few minutes to install ( I have an apt proxy/cache ) and then I could play with it for an hour or so to get a feel how it works. I'm 5 hours in and I haven't gotten a working 8.04 install yet ( I was testing 8.04 because I *was* going to upgrade my server to it. )

I don't keep copies of xorg.conf when using virtual machines. I create and delete them at a whim. I'm not going to spend any time faffing to get 8.04 working in QEMU..

I don't think they have over-ridden xorg.conf but I don't know enough to create it manually ( quickly ) and 'dpkg-reconfigure -phigh xorg' doesn't set it up the Old Way (TM) either.

It would be a nice option somewhere ( in dpkg-[re]configure? ):
Would you like to use auto-detect or standard xorg.conf creation?
[Auto detect]  [xorg.conf]

---

### Post by Lapp-Same on 2008-05-19
> **Xyem said:**
> Just a quick warning.

I have done a command line install of Hardy in QEMU and then tried adding xorg to it ( along with wdm and fluxbox for a light set-up ) and it doesn't work.

They have moved away from having the configuration in xorg.conf to auto-detection. In QEMU, at least, it doesn't work. I think it might have something to do with the fact a minimal install + xorg + dm + wm does not include the files used by this new auto-detection ( I think it is something like ~/.gnome2/monitors.xml ).

See this bug for ( possibly ) more info: [Bug #182743]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/182743")

Doing a full install in QEMU, results in a working display but without the ability to change resolution ( if I recall correctly ).

I'll be sticking to 7.10 and backports. Auto-detection is fine until it doesn't work and every tool you have for fixing it seems to be removed. I want my configuration in xorg.conf where 1) everyone else has it (?) 2) I can fix it :P


I'am not sure i understand exacly what you mean?

---

### Post by Xyem on 2008-05-19
In a nutshell, a minimal installation of Hardy, then installing xorg, will result in a non-functioning X server, in my experience, because it lacks certain configuration files.

---

### Post by Lapp-Same on 2008-05-19
> **Xyem said:**
> In a nutshell, a minimal installation of Hardy, then installing xorg, will result in a non-functioning X server, in my experience, because it lacks certain configuration files.

But isn't that wrong? soo far i have understand it you just install the Ubuntu Server edirion "Hardy Heron" and to get a minimal GUI on the server you install xorg!

isn't that right?

-Christoffer-

---

### Post by galileon on 2008-05-19
> **Xyem said:**
> I use virtual machines to experiment with things before putting them on my server ( which is running 7.10 ). I wanted to test Tagsistant. Should have taken me a few minutes to install ( I have an apt proxy/cache ) and then I could play with it for an hour or so to get a feel how it works. I'm 5 hours in and I haven't gotten a working 8.04 install yet ( I was testing 8.04 because I *was* going to upgrade my server to it. )

I don't keep copies of xorg.conf when using virtual machines. I create and delete them at a whim. I'm not going to spend any time faffing to get 8.04 working in QEMU..

I don't think they have over-ridden xorg.conf but I don't know enough to create it manually ( quickly ) and 'dpkg-reconfigure -phigh xorg' doesn't set it up the Old Way (TM) either.

It would be a nice option somewhere ( in dpkg-[re]configure? ):
Would you like to use auto-detect or standard xorg.conf creation?
[Auto detect]  [xorg.conf]

here's an old one of mine

<quote>
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
       Identifier      "Generic Keyboard"
       Driver          "kbd"
       Option          "CoreKeyboard"
       Option          "XkbRules"      "xorg"
       Option          "XkbModel"      "pc105"
       Option          "XkbLayout"     "gb"
       Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "mouse"
       Option          "CorePointer"
       Option          "Device"        "/dev/input/mice"
       Option          "Protocol"      "ImPS/2"
       Option          "ZAxisMapping"  "4 5"
       Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
       Driver          "wacom"
       Identifier      "stylus"
       Option          "Device"        "/dev/input/wacom"
       Option          "Type"  "stylus"
       Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
       Driver          "wacom"
       Identifier      "eraser"
       Option          "Device"        "/dev/input/wacom"
       Option          "Type"  "eraser"
       Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
       Driver          "wacom"
       Identifier      "cursor"
       Option          "Device"        "/dev/input/wacom"
       Option          "Type"  "cursor"
       Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
       Identifier      "nVidia Corporation GeForce 6500"
       Driver          "nvidia"
       Busid           "PCI:1:0:0"
       Option          "AddARGBVisuals"        "True"
       Option          "AddARGBGLXVisuals"     "True"
       Option          "NoLogo"        "True"
EndSection

Section "Monitor"
       Identifier      "L1715S"
       Option          "DPMS"
EndSection

Section "Screen"
       Identifier      "Default Screen"
       Device          "nVidia Corporation GeForce 6500"
       Monitor         "L1715S"
       Defaultdepth    24
       SubSection "Display"
               Modes           "1280x1024"     "1024x768"      "800x600"       "720x400"       "640x480"
       EndSubSection
EndSection

Section "ServerLayout"
       Identifier      "Default Layout"
 screen "Default Screen"
       Inputdevice     "Generic Keyboard"
       Inputdevice     "Configured Mouse"

       # Uncomment if you have a wacom tablet
       #       InputDevice     "stylus"        "SendCoreEvents"
       #       InputDevice     "cursor"        "SendCoreEvents"
       #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
       Load            "glx"
EndSection

</quote>
you might need to clean up the nvidia bits and try a vesa driver...

this seriously calls for a bug report :)

---

### Post by Xyem on 2008-05-19
That is how it has been done in recent versions but Hardy has changed the way it does X configuration.

Instead of xorg.conf being the definitive configuration, it is set to 'auto detect' your hardware ( i.e. is rather blank, containing lots of 'Configured *' statements ). However, the files containing the 'Configured *' are missing when it is installed like this.

'dpkg-reconfigure -phigh xorg' won't save you either, it doesn't write the "true" configuration to xorg.conf either.

**galileon**: Thanks for the xorg.conf but I won't be using it. I am simply not fiddling about every time I install Linux in a virtual machine ( i.e. worryingly often ).

---

### Post by Xyem on 2008-06-06
Update/Bump:

I got a CLI install + Xorg to work in QEMU. You have to add a line to xorg.conf to override the auto-configuration.

> Section "Screen"
...
  DefaultDepth 16
EndSection

The reason this is required ( in QEMU at least ) is because the auto-configuration in Hardy defaults to 32bpp which isn't supported with the Cirrus driver/emulation ( not sure which ) whereas in previous versions, it defaulted to 24bpp which is.

---

