---
title: "Twinview problem after Gutsy upgrade"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by theARE on 2008-01-19
Just upgraded to Gutsy from Feisty and I'm having trouble getting my nvidia twinview setup to work like it did before the upgrade.

I have a CRT as my main monitor operating a 1024x768 and it's also hooked up to my TV which operates at 1680x1050

On the kdm login screen everything is fine, I get the login dialog on the monitor and just the background image on the TV screen.

Once logged in though I'm getting 1 huge desktop so the wallpaper is stretched across both, I cant see the kicker on the monitor and windows maximize across both screens rather than inside individual screens like it did previously in feisty.

I think it's a problem with Xinemera, but after trying multiple things, I just cant get it working.

Here's my xorg.conf, any help would be very appreciated

```

Section "ServerLayout"
    Identifier     "TwinView Configuration"
    Screen      0  "Screen0" 0 0
    InputDevice    "Configured Mouse"
    InputDevice    "Generic Keyboard"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
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
    Load           "type1"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Card0"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Card0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "1024x768,1680x1050 ; 1024x768 , 1680x1050"
    Option         "SecondMonitorHorizSync" "30-120"
    Option         "SecondMonitorVertRefresh" "40-150"
    Option         "UseDisplayDevice" "CRT"
    Option         "NoTwinViewXineramaInfo" "False"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection



```

---

### Post by theARE on 2008-01-19
Sorry sorted it now.
In case anybody else has the same problem, just uninstall xserver-xgl .

After that everything seems to be working fine

---

