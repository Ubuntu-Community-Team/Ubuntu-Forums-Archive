---
title: "ATI transparency issues"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by Oscar Portela on 2007-10-24
Hi there,

I recently replaced the NVIDIA graphics card in my desktop computer with an ATI HD 2600 XT. While the new drivers seem to work flawlessly for the most part, I'm experiencing some annoying issues with transparency when trying to play a certain game with Wine. In fact, I don't think I use any other app which employs transparency right now.

In particular, anything partially transparent is either drawn as totally transparent or as a dark box, so all I see is the background with a couple of rectangles on top. This occurs also in another computer with an ATI Radeon Xpress 1270, and with both the 8.41 and 8.42 drivers. I remember having used this software in that second computer with the 8.40 drivers and this didn't happened.

I use the following X configuration in both computers:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
    FontPath       "/usr/share/fonts/X11/misc"
    FontPath       "/usr/share/fonts/X11/cyrillic"
    FontPath       "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath       "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath       "/usr/share/fonts/X11/Type1"
    FontPath       "/usr/share/fonts/X11/100dpi"
    FontPath       "/usr/share/fonts/X11/75dpi"
    FontPath       "/usr/share/fonts/X11/misc"
    FontPath       "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "dri"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "es"
    Option         "XkbOptions" "lv3:ralt_switch"
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

# LG L226W
# DELL Inspiron TFT
Section "Monitor"
    Identifier     "Flat Screen"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    Option         "DPMS"
EndSection

# ATI HD 2600 XT
# ATI Radeon Xpress 1270
Section "Device"
    Identifier     "ATI Graphics Card"
    Driver         "fglrx"
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "ATI Graphics Card"
    Monitor        "Flat Screen"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "DRI"
    Mode           0666
EndSection

Section "Extensions"
    Option         "Composite" "enable"
EndSection

```

I have tried enabling and disabling several options (including the composite extension, UseFastTLS, VideoOverlay, etc.), but haven't been able to overcome this problem. Does anyone have any clue on how to fix it?

Thanks in advance.

---

### Post by jimerickso on 2007-10-24
you could try installing 8.42.3 as it has been released now.

wget [http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run)

it uses aiglx now! hope this helps...

---

### Post by Oscar Portela on 2007-10-24
Yes, I'm using the 8.42.3 driver right now.

At first I thought it was perhaps something related to the 8.41 version, but after updating the driver the issue persists... :(

---

### Post by Oscar Portela on 2007-10-25
I have taken a few screenshots to illustrate the issue:

[IMG]http://www.kirja.es/images/2007.10.25.07.25.40.jpg[/IMG]

[IMG]http://www.kirja.es/images/2007.10.25.07.26.51.jpg[/IMG]

[IMG]http://www.kirja.es/images/2007.10.25.07.27.15.jpg[/IMG]

---

