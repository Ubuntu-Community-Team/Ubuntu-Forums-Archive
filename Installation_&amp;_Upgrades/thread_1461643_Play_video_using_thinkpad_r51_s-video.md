---
title: "Play video using thinkpad r51 s-video"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by faginbagin on 2010-04-24
I'm having trouble playing video using the S-video connection on my thinkpad r51. It's something I had working on mythbuntu hardy and now I'm trying to get it working on mythbuntu lucid.

On hardy, I modified the xorg.conf file adding:
```
        SubSection "Display"
                Virtual 1408    1818
        EndSubSection
```
to the screen section.

Then I used the following commands to enable S-video:
```
xrandr --output S-video --set load_detection 1
xrandr --output S-video --mode 800x600
xrandr --output S-video --below LVDS
```

Lucid doesn't install an xorg.conf file, so I'm not sure if I can/should create one or if doing so would interfere with the X server's ability to detect my hardware. But without it, how can I increase the virtual screen size?

The first two xrandr commands work and cause the upper left portion of the display to map to my TV. But the second one fails because the screen size isn't large enough to accommodate it. xrandr -q says it is "maximum 1400 x 1400." Although Xorg.0.log has this interesting tidbit:
```
(II) RADEON(0): Memory manager initialized to (0,0) (1408,5957)
(II) RADEON(0): Reserved area from (0,1400) to (1408,1410)
(II) RADEON(0): Largest offscreen area available: 1408 x 4547
```

I tried playing a video clip using mplayer. When I did, it was displayed on the LCD screen and not on the TV. All I could see on the TV was the mplayer window decorations surrounding a solid dark blue rectangle.

I suppose I could just try restarting gdm with the hardy xorg.conf, but I thought I'd first ask if there's a newer, better way to do what I want.

TIA,
Helen

---

### Post by faginbagin on 2010-04-24
FWIW, I just tried the hardy xorg.conf and it seems to do the trick. I'm still interested in knowing if this is the "lucid" way of getting video to play to an S-video attached TV.

Here's the xorg.conf in case anyone is interested. The key difference from the xorg.conf installed on hardy is in **bold**.

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
[B]        SubSection "Display"
                Virtual 1408    1818
        EndSubSection[/B]
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Synaptics Touchpad"
EndSection

```

---

