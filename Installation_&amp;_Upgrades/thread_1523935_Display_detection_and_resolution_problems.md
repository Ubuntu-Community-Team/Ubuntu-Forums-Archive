---
title: "Display detection and resolution problems"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by CARLMORE on 2010-07-04
Hi guys. I'm fairly new to linux. I've just installed the latest Xubuntu  on an older laptop with ATI RADEON XPRESS 200M graphics. The laptop has  a damaged display hinge and so I've attached a BENQ 24" LCD monitor to  it via d-sub connection. 

I'm currently restricted to using 1024x768 max resolution on both  displays as I'm unable to choose separate resolutions for each display.  Xfce Settings Manager only shows laptop display and does not show the  attached monitor for some reason.

Max resolution for laptop display should be 1280x800 and for attached  display should be 1920x1200. Using xrandr command at terminal I get the  following:

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis)  0mm x 0mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis)  289mm x 21mm
   1280x800       60.1 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9* 
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)

This is as far as I got. I don't know what to do next. Please help. Many  thanks.

---

### Post by Meneer Jansen on 2010-07-04
```
xrandr -d 0 -s 1280x800
```Will (probably ;)) set one of your displays to 1280x800 then you're left with the task of setting up */etc/X11/xorg.conf* so that the other one can be set to  1920x1200. 

I don't have two displays so I do not know ecactly how to to that. And I think it depends on your video card. What vid.crd. do you have?

This is my */etc/X11/xorg.conf *for inspiration:```

Section "ServerFlags"
  Option       "AllowMouseOpenFail"
EndSection

Section "Module"
  Load         "glx"
  Load         "dbe"
  Load         "v4l"
  Load         "freetype"
  Load         "type1"
  Load         "extmod"
EndSection

Section "InputDevice"
  Driver       "kbd"
  Identifier   "Keyboard[0]"
  Option       "Protocol" "Standard"
  Option       "XkbLayout" "us"
  Option       "XkbModel" "pc104"
  Option       "XkbRules" "xfree86"
EndSection

Section "InputDevice"
  Driver       "mouse"
  Identifier   "Mouse[1]"
  Option       "Buttons" "7"
  Option       "Device" "/dev/input/mice"
  Option       "Name" "ImExPS/2 Logitech Explorer Mouse"
  Option       "Protocol" "explorerps/2"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
        Identifier "Monitor[0]"
        ModelName "Generic Monitor"
        Option "DPMS"
        HorizSync 30-70
        VertRefresh 50-160
EndSection


Section "Screen"
  Identifier   "Screen[0]"
  Device       "Device[0]"
  Monitor      "Monitor[0]"
  DefaultDepth 24
  SubSection "Display"
    Depth      24
    Modes      "800x600" "1280x960" "1280x1024" "1280x800" "1152x864" "1280x768" "1024x768" "768x576" "640x480"
    Virtual    1280 960
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "800x600" "1280x960" "1280x1024" "1280x800" "1152x864" "1280x768" "1024x768" "768x576" "640x480"
#Virtual screensize. Beware: physical screen size cannot be larger!
    Virtual    1280 960
  EndSubSection
EndSection

Section "Device"
  Identifier   "Device[0]"
  Option       "NoLogo" "True"
  BoardName    "GeForce2 MX/MX 400"
  BusID        "1:0:0"
  Driver       "nvidia"
  Option       "CIOverlay"
  Option       "usevnc" "no"
  Option       "TVStandard" "PAL"
  Option       "TVOutFormat" "PAL"
  #Option       "NvAGP" "2"
  #Option       "NvAGP" "0"
  #Option       "NvAGP" "3"
  #Option       "NvAGP" "1"
  Screen       0
  VendorName   "NVidia"
#For Compiz-Fusion!
  Option "AddARGBGLXVisuals" "True" 
  Option "DisableGLXRootClipping" "True"
EndSection

Section "ServerLayout"
  Identifier   "Layout[all]"
  InputDevice  "Keyboard[0]" "CoreKeyboard"
  InputDevice  "Mouse[1]" "CorePointer"
  Option       "Clone" "off"
  Option       "Xinerama" "off"
  Screen       "Screen[0]"
EndSection

Section "DRI"
    Group      "video"
    Mode       0660
EndSection

Section "Extensions"
#For Compiz!
  Option "Composite" "Enable"
EndSection

```P.S. Why do you use Xubuntu and not the full blown Ubuntu? Considering the fact that you've got quite a hefty monitor, my guess is that you've got a computer of no more than 3 years old (i.e. "hefty"). No need for the lightweight Xubuntu....

---

