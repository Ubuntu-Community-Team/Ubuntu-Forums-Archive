---
title: "Extremely Slow &amp; Jerky Firefox Scrolling in Ubuntu Intrepid Beta"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Jags_FL on 2008-10-04
Just installed Intrepid beta / Oct 04 daily build successfully an i386 desktop. 

Everything including Nvidia drivers and Compiz works just fine but Firefox scrolling is extremely slow & jerky on many/most sites (including this forum site) and on some its freezes and screen turns gray for a while.

I tried with/without 'Use Smooth Scrolling' in Firefox advanced preferences but to no avail. Is there any solution for this highly annoying thing ? Also where to find some kool looking fonts for Intrepid please (have already tried that are in Firefox)...

Many thanks.

---

### Post by bpl07 on 2008-10-04
See if it's any different using metacity instead of compiz:

> metacity --replace

---

### Post by psyke83 on 2008-10-04
> **Jags_FL said:**
> Just installed Intrepid beta / Oct 04 daily build successfully an i386 desktop. 

Everything including Nvidia drivers and Compiz works just fine but Firefox scrolling is extremely slow & jerky on many/most sites (including this forum site) and on some its freezes and screen turns gray for a while.

I tried with/without 'Use Smooth Scrolling' in Firefox advanced preferences but to no avail. Is there any solution for this highly annoying thing ? Also where to find some kool looking fonts for Intrepid please (have already tried that are in Firefox)...

Many thanks.

It's because of compiz.

You need to use the 177 drivers (if compatible), and apply the driver settings as detailed [here]("http://www.nvnews.net/vbulletin/showthread.php?t=118088").

Also, be sure to turn OFF "smooth scrolling" in Firefox.

---

### Post by tact on 2008-10-04
I found that by reconfiguring xorg my scrolling in FF was fixed.

xorg.conf is not updated if it has any mods and you upgrade.  After reconfiguring xorg i found xorg.conf replaced with minimal version but everything works perfectly.

You find this in xorg.conf:

# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Jags_FL on 2008-10-04
Many thanks for the replies guys.


@ 'psyke83'

Nvidia 177 is not applicable to me as I have Nvidia GeForce FX 5200 installed on this machine.

nvidia-glx-173 (173.14.12-1-0ubuntu3) was auto-installed by Intrepid.


@ 'tact'

yes, I found that "# sudo dpkg-reconfigure -phigh xserver-xorg" in xorg.conf and when I ran that, it displayed this message:

:::::::
root@ubuntu:~# sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081004191002
:::::::


and it changed xorg.conf **FROM :**

:::
Section "Monitor"

Identifier "Configured Monitor"

EndSection


Section "Screen"

Identifier "Default Screen"

Monitor "Configured Monitor"

Device "Configured Video Device"

DefaultDepth 24

EndSection


Section "Module"

Load "glx"

Disable "dri2"

EndSection


Section "Device"

Identifier "Configured Video Device"

Driver "nvidia"

Option "NoLogo" "True"

EndSection
:::


**TO :**


:::
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
:::


But still Firefox scrolling is too slow and jerky with/without 'use smooth scrolling'.

---

### Post by Jags_FL on 2008-10-04
Ok after that change (post# 5) in xorg.conf by "# sudo dpkg-reconfigure -phigh xserver-xorg"

when I restarted the PC, the screen alignment was off (like there were no Nvidia drivers installed) and the Compiz effects were gone too.


So I copied following (I had a copy of xorg.conf from an earlier installation) into xorg.conf and restarted the PC. Screen alignment & Compiz effects are back again BUT Firefox scrolling is still too slow.


:::::::
Section "ServerLayout"
    Identifier     "Layout[all]"
    Screen         "Screen[0]" 0 0
    InputDevice    "Keyboard[0]" "CoreKeyboard"
    InputDevice    "Mouse[1]" "CorePointer"
    Option         "Clone" "off"
    Option         "Xinerama" "off"
EndSection

Section "Module"
    Load           "dbe" # Double-Buffering Extension
    Load           "type1"
    Load           "freetype"
    Load           "extmod"
    Load           "v4l" # Video for Linux
    Load           "glx" # 3D layer
    Load           "i2c"
    Load           "bitmap"    
EndSection

Section "ServerFlags"
    Option         "AllowMouseOpenFail" "on"
EndSection

Section "InputDevice"
    Identifier     "Keyboard[0]"
    Driver         "kbd"
    Option         "Protocol" "Standard"
    Option         "XkbLayout" "us"
    Option         "XkbModel" "microsoftpro"
    Option         "XkbRules" "xfree86"
EndSection

Section "InputDevice"
    Identifier     "Mouse[1]"
    Driver         "mouse"
    Option         "Buttons" "5"
    Option         "Device" "/dev/input/mice"
    Option         "Name" "ImPS/2 Generic Wheel Mouse"
    Option         "Protocol" "explorerps/2"
    Option         "Vendor" "Sysp"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Modes"
    Identifier         "Modes[0]"
    ModeLine     "1280x1024" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor[0]"
    VendorName     "DELL"
    ModelName      "1702FP (ANALOG)"
    UseModes       "Modes[0]"
    DisplaySize     338    270
    HorizSync       30.0 - 80.0
    VertRefresh     56.0 - 76.0
    Option         "CalcAlgorithm" "XServerPool"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    VendorName     "NVidia"
    BoardName      "GeForce FX 5200 (0x0322)"
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "800x600"
    EndSubSection
        option     "AddARGBGLXVisuals" "true"
        option     "DiasableGLXRootClipping" "true"
EndSection
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
:::::::

---

### Post by Nullack on 2008-10-04
That conf is a nightmare. Minimalist is the way to go.

---

### Post by Jags_FL on 2008-10-04
'Nullack' thanks for the reply.

But its 'experimental' PC and I entered that extra long conf just to check out if its gonna have any effect on Firefox scrolling... but it had no effect.

---

### Post by psyke83 on 2008-10-05
Trust my advice, as I have a FX 5200 as well.

Compiz is sluggish with this card. Although you are forced to use the 173 drivers, you *can* still tweak the driver to get some extra performance.

```
$ nvidia-settings -a InitialPixmapPlacement=2
```

This will improve scrolling in Firefox for 90% of cases, but a small minority of websites will scroll slightly slower.

Of course, you can always disable compiz.

---

### Post by Jags_FL on 2008-10-06
Thanks psyke83

I did apply

```
$ nvidia-settings -a InitialPixmapPlacement=2
```

On some sites Firefox scrolling does feel little improved but on others its still very slow.

Thanks again for the tweak.

---

### Post by stats on 2008-10-06
it might be because of the flash plugin. i had that problem.
[http://fpreto.wordpress.com/2008/09/27/flash-high-cpu-usage-on-intrepid-a-better-solution/]("http://fpreto.wordpress.com/2008/09/27/flash-high-cpu-usage-on-intrepid-a-better-solution/")
solved it for me

---

### Post by Jags_FL on 2008-10-07
Thanks 'stats'

I did apply the patch from this link

```
http://fpreto.wordpress.com/2008/09/27/flash-high-cpu-usage-on-intrepid-a-better-solution/
```

It sounds like Firefox scrolling has improved, (and I'm sorry to mention this here) but its still not at par with Firefox in Windows.

---

### Post by psyke83 on 2008-10-07
Supported Product list for the 177.80 drivers: [http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

Hopefully this is accurate, which means you can benefit from the driver optimizations. You can try manually installing the driver (not recommended) or just wait for the update.

---

### Post by Jags_FL on 2008-10-07
Thanks 'psyke83' for :

> Supported Product list for the 177.80 drivers: [http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

I guess I'll wait instead of installing it manually.

---

### Post by DavidONE on 2008-10-24
I'm seeing the same problem.  It's only an issue on some pages - e.g. [http://dotearth.blogs.nytimes.com/2008/10/22/inventor-aims-to-aid-poorest-billions/](http://dotearth.blogs.nytimes.com/2008/10/22/inventor-aims-to-aid-poorest-billions/)

If I use cursor key to scroll down, there's an intial delay and then it scrolls slowly.  Also, if I hold down the cursor for a few seconds and then release it, the pages continues scrolling.

I don't see this problem in XP with same plugins for Firefox.

---

