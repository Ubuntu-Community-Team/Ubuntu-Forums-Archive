---
title: "Stuck in 960 X 720"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by peakshysteria on 2008-03-17
Was stuck in 960 X 720 resolution in Gutsy. Upgraded to Hardy Heron Alpha 6 with:

Update-manager -d

Didn't solve anything. I'm still stuck in the same resolution. Everytime i try to change it in the Screens and graphics menu i must restart the system. Ctrl + Alt + Backspace sends me back to the low graphics mode again. Rebooting also only gives me the low graphic mode. So i'm in a loop. Unable to see how Hardy are functioning at all. Currently tv out is working. But with a crappy resolution on my lcd tv. Far from the quality in windows. And this is not because of the upgrade to Hardy. It's all the same as in my Gutsy.

I have an ATI Radeon Excalibur X700 Pro

The Hardy upgrade went smooth with no visible errors. Only thing i have done after upgrade is to install fglrx. The resolution loop problem was the same before the install of fglrx and is the same after the install.

fglrxinfo gives me the well known hell:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

Can anyone get me out of this mess? Been trying for a long time now. Been a while since i had a working Ubuntu now. Can't seem to shake the problems this time.

---

### Post by Pumalite on 2008-03-17
You might want to try Envy: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
(ATI does nor support Linux)

---

### Post by Peter09 on 2008-03-17
Look for threads talking about xorg.conf. You need to edit it to change your resolution.

PC

---

### Post by peakshysteria on 2008-03-17
> **Pumalite said:**
> You might want to try Envy: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
(ATI does nor support Linux)

Envy is tried under Gutsy. Didn't work. Maybe i shoould try it in Hardy as well. With luck EnvyNG might be different from Envy Legacy. I'll give it a shot as soon as i'm able to log in to Ubuntu again.

And there is no restricted ATI driver in the restricted drivers manager now. Is this right? 

And yes Peter09 i've tried to edit my xorg.conf without luck in Gutsy. I'm sure it's me doing something wrong. I thought i might wait to see the responds here before i tried once again to edit it. I guess there ain't to much difference in doing that in Gutsy and Hardy.

---

### Post by Pumalite on 2008-03-17
Good luck

---

### Post by Peter09 on 2008-03-17
Have you tried the following

```
 sudo dpkg-reconfigure  xserver-x
```

and changed the driver in there to ati.

Also when you use Envy you may have to enable the driver in the Restricted Driver Management
 utility.


PC

---

### Post by peakshysteria on 2008-03-17
> **Peter09 said:**
> Have you tried the following

```
 sudo dpkg-reconfigure  xserver-x
```

and changed the driver in there to ati.

Also when you use Envy you may have to enable the driver in the Restricted Driver Management
 utility.


PC

So do you mean to check the driver after i have installed Envy? Because right now there isn't a driver at all in the Restricted Driver Management utility.

And is it all vesa entries i'm supposed to change to ATI?

---

### Post by Peter09 on 2008-03-17
You haven't done Envy correctly if there is no driver in the restricted drivers utility.

The vesa one is the one for your video card driver.

---

### Post by peakshysteria on 2008-03-18
> **Peter09 said:**
> You haven't done Envy correctly if there is no driver in the restricted drivers utility.

The vesa one is the one for your video card driver.

Haven't installed it yet. In Gutsy there was a driver in the  restricted drivers manager before i installed Envy. It was there from the beginning actually (after a clean install). Ready to be checked an used. So thats what I'm referring to. Not sure if should be the same in Hardy or not.

---

### Post by Peter09 on 2008-03-18
Install Envy as it forms a good basis for the installation of the correct video driver. The fact that the current driver does not seem to support your required resolution is a good case for using it.

PC

---

### Post by peakshysteria on 2008-03-19
Booted Ubuntu last night. It startet with a resolution of 800 X 600. Managed to get to my desktop and change the resolution to 1280 X 1024. Restarted (ctrl + alt + backspace) since the rebooting still gives me the low graphics manager (and the loop is on again). Hardy then boots with 1600 X 1024 which give me screen out of range.

No other solution than rebooting. Which gives me the low graphics manager. Then getting to my desktop again but this time magically in 960 X 720 resolution again.

Then installed Envy for Hardy. Which went smooth and without problems. Restarted X. The resolution was still 960 X 720. Installed 41 waiting updates. Some of them where ATI specific apparently. Rebooted again. Low graphics manager. Resolution was still 960 X 720. Tried to find the Screens and graphics manager but it had disappeared!!

I kid you not, it was gone. So no i cannot change resolution at all. Trying ATI Catalyst Control Center but it says something is wrong with the ATI install.

So once again i'm stuck in 960 X 720 for some strange reason. Anyone have a solution from here on? Can i rebuild xorg or something?

Would really like to get a working Ubuntu once again. Preferably with Compiz :) And of course also with a working tv out. Priority one is of course to get a working Ubuntu (meaning a resolution of 1280 X 1024).

---

### Post by Pumalite on 2008-03-19
You would have better luck with an Nvidia Card. Something like 7800 GT.

---

### Post by Peter09 on 2008-03-19
Check that the Restricted Driver is enabled. I'm not at my Ubuntu desktop at the moment so I cannot post details. But sometimes ENVY will install the driver but not enable it.

PC

---

### Post by peakshysteria on 2008-03-19
I guess i would. But then again that's not the case. And for what seems like ages ago i had a perfectly working Gutsy. So it is possible to have a nice working Ubuntu with ATI. At least as long as you don't go for the impossible tv out quest.

Anyway, there should be possible to get a working Hardy.

Edit: The driver is checked, green and in use in the restricted drivers manager. Pretty strange it is. Not sure how to proceed from here on....

---

### Post by Peter09 on 2008-03-19
We posted at the same time, so I thought I'd bump this to ensure you saw my post

:)

PC

---

### Post by peakshysteria on 2008-03-24
fglrxinfo still gives me:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

Resinstalled the ATI driver just now. It is checked, green and in use in the restricted drivers manager. The proper resolution is set (1280x1024). But the resolution wont change at all. It's stuck in 800x600. At least that's what the screens and graphics manager tells me when i check. Still when i restart x i'm back into low graphics manager and the loops starts again. If i reboot the same thing happens. So i'm stuck in this loop.

The output of my /etc/X11/xorg.conf :

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "no"
        Option          "XkbVariant"    "no"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "vmmouse"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "vesa"
        Busid           "PCI:1:0:1"
        Driver          "fglrx"
        Screen  0
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1600    1200
                Modes           "800x600@72"    "800x600@75"    "800x600@56"    "800x600@60"    "640x480@75"    "832x624@75"    "640x480@72"    "1024x768@7$
        EndSubSection
        Option          "Defaultdepth"  "24"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection
Section "device" #
        Identifier      "device1"
        Boardname       "ATI Radeon (fglrx)"
        Busid           "PCI:1:0:0"
        Driver          "fglrx"
        Screen  0
        Vendorname      "ATI"
        Option          "MergedFB"      "off"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
EndSection
Section "screen" #
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
        SubSection "Display"
                Depth   24
                Modes           "1280x1024@60"  "1280x960@60"   "1024x768@60"   "800x600@60"    "800x600@56"    "640x480@60"
        EndSubSection
        Option          "Defaultdepth"  "24"
EndSection
Section "monitor" #
        Identifier      "monitor1"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1280x1024"
        Horizsync       31.5-64.0
        Vertrefresh     56.0    -       65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
        Gamma   1.0
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
        Option          "Composite"     "Enable"
EndSection

Can anyone see whats wrong here???

---

### Post by miggols99 on 2008-03-24
Wow! That xorg.conf is messed up. Delete
> Section "monitor" #
Identifier "monitor1"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1280x1024"
Horizsync 31.5-64.0
Vertrefresh 56.0 - 65.0
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
Gamma 1.0
EndSection
and
> Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Plug 'n' Play"
Modelname "Plug 'n' Play"
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
modeline "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
modeline "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
modeline "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
modeline "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
modeline "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
modeline "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
modeline "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
modeline "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
Gamma 1.0
EndSection
It has three monitor sections!!

---

### Post by peakshysteria on 2008-03-24
Thanks for extremely fast reply. I'll try that tomorrow. Any chance you could tell me how to edit this in a text converter and not in the terminal?

And how can you see witch of them to delete? I'm desperately trying to get a resolution of 1280x1024 you know.....

Deleted the two you asuggested. Didn't make any changes. Still stuck in a loop.

---

