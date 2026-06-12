---
title: "Install on Thinkpad S540: No GUI after first reboot"
date: 2014-03-29
forum: Installation &amp; Upgrades
---

### Post by ferdez2 on 2014-03-29
Hi all,

I'm trying to install 13.10 or 14.04b on a Lenovo Thinkpad S540. Booting with ubuntu on a usb stick works fine. The installation procedure works fine all to the end.

The problem is that, when I get to the first reboot, X doesn't work anymore. It says the system will go into low graphics mode but X will dump core and never come up again.

I'd like to find a way of simply replicating the X configuration used during install to put on the hard disk installation. 

I had some success changing /etc/X11/xorg.conf.failsafe but it seems to be overwritten every time and the configuration is lost. Tha same seems to happen with xorg.conf

I attach my lshw output, xorg.log and apport.log.

I got the the same behavior from both versions.

Any ideas?

TIA

Fernando

---

### Post by ferdez2 on 2014-03-29
Sorry, forgot to attach files. But the Xorg.log is to big to upload, apparently

---

### Post by grahammechanical on 2014-03-29
Are you aware that the Ubuntu live session does not use a proprietary video driver? The live session use the Nouveau open source video driver. Also, when we install and tick "Install third party software" we get a proprietary video driver installed. That is the big difference between getting a working live session and a broken installation at the first reboot.

At the Grub boot menu select Advance Options for Ubuntu and the select Recovery mode. At the Recovery menu select Resume. That will load (may be) to a desktop without using the proprietary video driver. Instead the desktop session will be running on a fallback video mode called Gallium llvmpipe, which is part of Nouveau. The user experience will seem a little slow but at the desktop you can go to System Settings>Software and Updates>Additional Drivers tab and experiment with video drivers. Allow time for the utility to search for some video drivers.

Regards.

---

### Post by ferdez2 on 2014-03-29
The problem seems to be that, after install, X finds two cards: Intel and ATI:
> 
[ 10053.658] Loading extension GLX
[ 10053.658] (==) Matched intel as autoconfigured driver 0
[ 10053.658] (==) Matched fglrx as autoconfigured driver 1
[ 10053.658] (==) Matched ati as autoconfigured driver 2
[ 10053.658] (==) Matched intel as autoconfigured driver 3
[ 10053.658] (==) Matched modesetting as autoconfigured driver 4
[ 10053.658] (==) Matched fbdev as autoconfigured driver 5
[ 10053.658] (==) Matched vesa as autoconfigured driver 6


But the X on the usb stick only finds the Intel card:
> 
[    20.347] Loading extension GLX
[    20.347] (==) Matched intel as autoconfigured driver 0
[    20.347] (==) Matched intel as autoconfigured driver 1
[    20.347] (==) Matched modesetting as autoconfigured driver 2
[    20.347] (==) Matched fbdev as autoconfigured driver 3
[    20.347] (==) Matched vesa as autoconfigured driver 4


Possibly, on quick solution could be to disable the ATI card.

---

### Post by ferdez2 on 2014-03-29
Thanks for your input, grahammechanical. But my board is an hybrid with AMD/ATI+Intel. The Nouveau driver, I think, is only for Nvidia cards. Also, I'm not using proprietary drivers. 

Xorg just seems so find different cards when installing and when booting from disk. Maybe it's the kernel drivers that come in the usb stick for live session... 

I found a workaround, for the moment. Run "Xorg -configure" to generate a xorg.conf.new and edited it to use only one od the devices, with the intel driver. It seems to work. 

Here is my new /etc/X11/xorg.conf:
> 
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "kmsdev"                 # <str>
        #Option     "ShadowFB"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


---

### Post by ferdez2 on 2014-03-30
Filed a bug on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1299792](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1299792)

---

