---
title: "graphics problems after upgrade to gutsy (nvidia 6600 dual screen)"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by naurus on 2007-11-07
I recently did an automated upgrade from 7.04 to 7.10.  before the upgrade i had everything working perfectly, the grahpics, compiz, and all my apps.  After the upgrade and reboot, ubuntu started up in bulletproof X.  I set all the settings correctly (i think, both monitors set at 1680x1050 and widescreen) and pressed ok.  The resolution stayed at 640x480 and i was able to login.  The closest i've gotten is 1280x1024 without desktop effects :(

i have an nvidia 6600 dual head with two acer AL2216W LCD's hooked up.  I really need to have both monitors working as separate screens, twinview if possible, and both at 1680x1050.

thanks,
naurus

---

### Post by bulldog on 2007-11-07
I can not understand why people throw away a perfect working ubuntu.
Why don't you install Gutsy beside the 'old' install and test it before you decide to upgrade.
You only need 10GB at the most to do so.

Did you install any graphics driver?

---

### Post by Pumalite on 2007-11-07
[http://www.phoronix.com/scan.php?page=article&item=387&num=1](http://www.phoronix.com/scan.php?page=article&item=387&num=1)
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by dr.krap on 2007-11-07
I still haven't upgraded because i'm afraid this will happen to me. In fact, I don't think i'll upgrade until I build my new machine. I'm sorry to hear your setup is nutted. I wish I could offer some assistance, but I haven't even looked into gutsy. Good luck!

---

### Post by bulldog on 2007-11-07
> **dr.krap said:**
> I still haven't upgraded because i'm afraid this will happen to me. In fact, I don't think i'll upgrade until I build my new machine. I'm sorry to hear your setup is nutted. I wish I could offer some assistance, but I haven't even looked into gutsy. Good luck!

You can install it at the same time if you have some space left on your hdd.
10GB at the most and you can use the same swap.

---

### Post by Pumalite on 2007-11-07
I agree. You can install as many as you want as long as you have space and they all share same /swap.

---

### Post by naurus on 2007-11-13
lol, i did install it side-by-side and the graphics worked perfectly

---

### Post by naurus on 2007-11-14
i think it may have something to do with the nvidia restricted driver. after enabling it and rebooting it says it's in use but not enabled, that didn't use to happen in 7.04

---

### Post by naurus on 2007-11-15
GOT IT!!

After DAYS of messing around with xorg.conf, I decided to go a different route and work with drivers (should've known) and viola!

[FONT="Arial Black"]_**[SIZE="3"]THE FIX[/SIZE]**_[/FONT]
[FONT="Arial"]
[LIST=1]
[*]Install Envy
[*]Use Envy to MANUALLY install the 96.43.01 driver
[*]Reboot
[*]Use 'nvidia-settings' to edit configuration
[*]WOOT! It works!
[/LIST][/FONT]

Thanks everyone for the help :)

---

### Post by devout on 2007-11-16
I have a similar issue.

New System:

Mobo: GA-P31-DS3L
CPU: C2D E6550 2.33GHz 4M cache FSB 1333
HDD: WD3200AAKS
Graphics Card: Gigabyte Nvidia NX66T, Nvidia geforce 6600 GT
Primary screen ViewSonic VA702 LCD
Secondary screen ViewSonic E70 CRT

OS: Gutsy Gibbon 7.10

So far I've spent 2 days on this install.
Have had to reinstall several times.

The symptom I have is, both of my screens have a larger resolution than the physical size of the display. This means I can not see all of the desktop. If I move my mouse to one of the outside parameters the desktop moves to the oppisit side, enabling me to see the side of the desktop that I moved my mouse too. In essence, the desktop scrols as I move my mouse to the top, sides, or bottom. On each screen.

I've tryed fumbling around in the /etc/X11/xorg.conf (Only making things worse).
Have also tryed envy as in the last post.

If I try System->Preferences->Screen Resolution, I get a message box stating "The X Server does not support the XRandR extension. Runtime resolution changes to the display size are not available" Not sure what's going on there..?.

If I try Applications->System Tools->Nvidia Settings, X Server Display Configuration.
Each time I change the Resolution of the VA702 and save to X config file, restart X, and go back into Nvidia Settings the Resolution has reverted back to 1400x1050. The screen only supports 1280x1024 or smaller sizes.

Anyone got any ideas on this one?

Before I embarked on this gutsy gibbon mission I asked my linux guru mate if he thought there would be any problems with dual monitors. He assured me There shouldn't be any problems, but he is a bit stumped too now.

Any help will be much appreciated as usual.
Thanks.:-?

---

### Post by Pumalite on 2007-11-17
I hope it helps:

[http://www.phoronix.com/scan.php?page=article&item=387&num=1](http://www.phoronix.com/scan.php?page=article&item=387&num=1)
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

---

### Post by devout on 2007-11-17
Ok.

After quite a bit of reading other posts, trial and error.
This is what I've found out and it seems to have worked for now.
I enabled the main, restricted, universe and multiverse repositories using this post... [http://ubuntu.sun.ac.za/wiki/index.php/Repositories](http://ubuntu.sun.ac.za/wiki/index.php/Repositories)
I ```
sudo apt-get install nvidia-glx-new
``` (Not that I needed this with the next step)
I ended up installing the 100.14.23 version of the nvidia driver (thanks to Envy and it's creator Alverto Milone).
With one of the installs, either the nvidia-glx-new or the nvidia driver that Envy installed... the nvidia accelerated graphics driver (latest cards), which shows up in System->Administration->Restricted Drivers Manager was installed. This needs to be Enabled.
is with the Envy installer a nvidia X server settings utility is installed.
I played with this alot and in the end it was of no use. As all the changes I made would not stick. Although the driver and it's dependancies that Envy installed for me were crucial.

The X log /var/log/Xorg.0.log didn't give me much usefull diagnostic info.
I Then followd this link [http://ubuntuforums.org/archive/index.php/t-112164.html](http://ubuntuforums.org/archive/index.php/t-112164.html)
and replaced the relevant Sections of /etc/X11/xorg.conf with the Sections from the one suggested.
I then followd this [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
and ended up with a /etc/X11/xorg.conf like this...


# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Oct  4 10:33:51 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf " at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Screen0" rightof "Screen1"
  screen 1 "Screen1" 0 0    
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
    Option        "Xinerama"    "on"
EndSection

Section "Files"
EndSection

Section "Module"
    Load        "glx"
    Load        "v4l"
EndSection

Section "ServerFlags"
    Option        "Xinerama"    "true"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "stylus"
    Driver        "wacom"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier    "eraser"
    Driver        "wacom"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier    "cursor"
    Driver        "wacom"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier    "Monitor0"
    Vendorname    "ViewSonic"
    Modelname    "VA702"
    Displaysize    380    310
    Horizsync    30.0    -    80.0
    Vertrefresh    56.0    -    76.0
    Option        "dpms"
EndSection

Section "Monitor"
    Identifier    "Monitor1"
    Vendorname    "ViewSonic"
    # 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81:80 MHzModeline "1024x768_75.00" 81.80 1024 1080 1192 1360    768 769 772 802    -HSync +Vsync
    Modelname    "E70"
    Horizsync    30.0    -    80.0
    Vertrefresh    56.0    -    76.0
    Option        "dpms"
EndSection

Section "Device"
    Identifier    "Videocard0"
    Driver        "nvidia"
    #Driver "nv"
    Vendorname    "Videocard vendor"
    Boardname    "NVIDIA GeForce FX (generic)"
    Screen    0
    #Option "Rotate" "CW"
    Option        "RenderAccel"    "true"
    # Option "AllowGLXWithComposite" "true"
EndSection

Section "Device"
    Identifier    "Videocard1"
    Driver        "nvidia"
    #Driver "nv"
    Vendorname    "Videocard Vendor"
    Boardname    "NVIDIA GeForce FX (generic)"
    Busid        "PCI:1:0:0"
    Screen    1
    Option        "RenderAccel"    "true"
    # Option "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "VideoCard0"
    Monitor        "Monitor0"
    Defaultdepth    24    
    SubSection "Display"
        Depth    24
        Modes    "1280x1024_60.00"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Screen1"
    Device        "VideoCard1"
    Monitor        "Monitor1"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Modes    "1024x768_75.00"
    EndSubSection    
EndSection

Section "Extensions"
    Option        "Composite"    "Enable"
EndSection


I then ```
sudo /etc/init.d/gdm stop
```
```
sudo /etc/init.d/gdm start
```

---

### Post by devout on 2007-11-17
Cool. Thanks for that.
Plenty of reading there.

---

### Post by Pumalite on 2007-11-17
You are welcome. Good luck.

---

### Post by LPGDEV on 2007-11-17
I am having more or less the same problem. I am using ubuntu 7.10 and I have a nvidia graphics card and I am attempting to get a proper dual screen working.

I have managed to configure it so that I have two separate screens (which was my goal) but Ihave 3 problems:

1.  The desktop icons are moved from my "main screen" onto my secondary screen (which I had hoped would remain empty). 

2. The background image I have is stretched over both screens which totally messes up the resolution.

3. The "Advanced Desktop Settings" don't work at all.

Here isi my xorg.conf:

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:29:35 PDT 2007
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
# Section "ServerLayout"
# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
#    Identifier     "Default Layout"
#    Screen         "Default Screen" 0 0
#    InputDevice    "Generic Keyboard"
#    InputDevice    "Configured Mouse"
#    InputDevice    "Synaptics Touchpad"
# EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" rightof "Screen1"
# 1280 0
    Screen      1  "Screen1" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
    Option         "Xinerama" "true"
EndSection

Section "Files"
    # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "true"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier		"Monitor1"
    VendorName     	"Unknown"
    ModelName      	"Iiyama BX3814UT"
    HorizSync       28.0 - 64.0
    VertRefresh     48.0 - 78.0
    Option	   		"DPMS"
EndSection

Section "Monitor"
    Identifier     	"Monitor0"
    VendorName     	"Unknown"
    ModelName      	"QDS"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option	   		"DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7300"
    BusID          "PCI:1:0:0"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    Option         "UseDisplayDevice" "DFP"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7300"
    BusID          "PCI:1:0:0"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP: 1280x800 +0+0"
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
EndSection

```

Any help would be greatly appreciated.

---

### Post by devout on 2007-11-17
Just one thing I need to add from my last post...

Next time I tryed to run a terminal with in X. It wouldn't run.

type ALT + F2 and type 'xterm'.
Then type 'gnome-terminal" into that xterm terminal and see if you get any strange output from it. i.e. The program 'gnome-terminal' received an X Window System error.

disable the Composite extension by adding the following lines to /etc/X11/Xorg.conf:

    Section "Extensions"
    Option "Composite" "false"
    EndSection

This fixed the problem.

This info was glened from...
[http://ubuntuforums.org/showthread.php?t=429256](http://ubuntuforums.org/showthread.php?t=429256)
[http://www.nvnews.net/vbulletin/showthread.php?t=78843](http://www.nvnews.net/vbulletin/showthread.php?t=78843)


LPGDEV

> 1. The desktop icons are moved from my "main screen" onto my secondary screen (which I had hoped would remain empty). 

Can you not just drag the desktop shortcuts to your main screen? This works for me.

> 2. The background image I have is stretched over both screens which totally messes up the resolution.

Sounds like you have 2 physical screens setup, but only one real screen streched accros s the 2 physical monitors?

> 3. The "Advanced Desktop Settings" don't work at all.

Mmm, neither do mine. I wasn't to worried about that though, as I spent 2 solid days getting thus far, and it seems like we can configure every thing using the /etc/X11/xorg.conf

Not sure I can be of much more help if you have already tryed every thing recorded in this thread.
:???:

---

### Post by LPGDEV on 2007-11-18
> 
Can you not just drag the desktop shortcuts to your main screen? This works for me.


Yes I can, but every time I restart the icons are reset to their original position.

> 
Sounds like you have 2 physical screens setup, but only one real screen streched accros s the 2 physical monitors?


This is what I thought however, the stretching only applies to the desktop icons and background and not to the top and bottom panels, which makes it confusing.

---

### Post by naurus on 2007-11-18
for the icons, just switch the order of your monitors (in xorg.conf OR on your desk) and you should be fine

---

