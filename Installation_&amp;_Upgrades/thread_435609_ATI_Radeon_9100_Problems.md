---
title: "ATI Radeon 9100 Problems"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by igb on 2007-05-07
I am having problems with an Asus Pundit that has a Radeon 9100 1GP video card. This has worked fine with the fglrx drivers from Breezy->Edgy. I have done a clean install of Feisty and when I try to install the fglrx driver the Xserver hangs at startup.

The free driver won't let me set a desktop resolution of anything greater than 1024x768 even after editing xorg.conf to enable the other resolutions.

Here is an extract from the log:

```
(II) ATI Proprietary Linux Driver Build Date: Feb 20 2007 11:49:19
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.34.1.1.2.3-drive
r-lnx-x86-x86_64-327152
(EE) No devices detected.

Fatal server error:
no screens found
```

It looks as though it can't find the card.

Here is my xorg.conf (some sections edited out)

```
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
     edited out)   FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
  Load  "int10"
        Load  "vbe"
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    28.0 - 51.0
        VertRefresh  43.0 - 60.0
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "ATI Technologies Inc Radeon 9100 IGP"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:5:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies Inc Radeon 9100 IGP"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes     "1680x1050" "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes     "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes     "1680x1050"  "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection


```

Ian.

---

### Post by ionel on 2007-05-07
I also have the same problem with two ATI cards that in Edgy worked fine with fglrx driver but with Feisty i have the same error  "(EE) No devices detected." 
Can someone help please !!!

---

### Post by blacksarah on 2007-05-07
I just installed feisty on my desktop, and with proprietary fglrx drivers I get the same problem (radeon 9200).
Have you found a solution?
:cry:

---

### Post by gmjs on 2007-05-13
I know Sarah - I've got exactly the same graphics card and the same problem.  I hope there will be an update to the xserver-xorg-ati package that runs just as well as the fglrx driver.  It's spoiling my Blender UI!

---

### Post by FishRCynic on 2007-05-13
backport to the older driver - the new drivers do not have the 9100 included - i have no problem with the xorg default driver though. ATI has discontinued support in the new driver.  (i have an onboard 9100 though so i don't expect as much ;-) )

---

### Post by kabanowster on 2007-05-21
try viewing this page:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

It helped me alot. I can run now Americas Army 2.8 game on Wine with no problems.

---

