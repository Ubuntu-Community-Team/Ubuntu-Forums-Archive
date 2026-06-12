---
title: "A lead on why 7.10 is so slow"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by josefs on 2008-01-18
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=589555](http://ubuntuforums.org/showthread.php?t=589555) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Some people have reported that they experience a slowdown when they upgrade to 7.10. I upgraded earlier this week and also found my previously so lean machine almost griding to  a halt. It has been rather frustrating.

Today I've found some hints as to where the slowdown comes from but I need some help with how to proceed and eventually solve the problem. 

I've been using the System Monitor to try to find a possible explanation for the cause of the slowdown. When I select to watch all processes (not just my own) I find one process which is bouncing up and down, taking roughly 30% CPU at the most. It's the ksoftirqd/1 process. According to the following web page, having this process "taking more than a tiny percentage of CPU time, this indicates the machine is under heavy soft interrupt load."
[http://www.penguin-soft.com/penguin/man/9/ksoftirqd.html](http://www.penguin-soft.com/penguin/man/9/ksoftirqd.html)

So I assume that my machine is getting swamped by soft interrupts from somewhere. Is there a way to find out where they come from so that I can do something about it?

---

### Post by josefs on 2008-01-18
It seems I was a little quick on assigning blame to Gutsy. What I suspect now is that Xorg might be the source behind the problems. Watching the system monitor I can see that Xorg takes a lot of CPU every now and then, roughly 50%. The funny thing is that is seems to take turns with ksoftirqd, which might have to do with the fact that ksoftirqd is nice'd or that Xorg is producing these soft interrupts which ksoftirqd then later have to deal with.

Anyway, one possible explanation for Xorg's behavior is that I misconfigured it when upgrading to 7.10. I have a nVidia Geforce 8400 card which was a bit of a hassle to get to work after the upgrade. I had to edit xorg.conf quite a lot, both by hand and by tools and I suspect something broke. Here's what it looks like now:
```

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
    Option         "XkbOptions" "lv3:ralt_switch"
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
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8400M GS]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8400M GS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

Any help on what I can do to reduce the CPU load is appreciated.

---

### Post by biodiesel-bri on 2008-02-26
[http://ubuntuforums.org/showthread.php?p=4410733#post4410733](http://ubuntuforums.org/showthread.php?p=4410733#post4410733)

---

### Post by Partyboi2 on 2008-02-26
[Here]("http://ubuntuforums.org/showthread.php?t=595825") is some info on a few known bugs in Gusty and workarounds

---

