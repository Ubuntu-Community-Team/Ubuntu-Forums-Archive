---
title: "My problems with dist-upgrade"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by el_itur on 2007-04-20
Hi everyone: I have updated from the alternate cd from edgy to feisty.

There are my problems:

third mouse button doesn't work anymore (the wheel does).

I've installed the nvidia drivers from restricted-modules-manager and although the xorg.conf seems to be right and I got no error on the xorg.0.log glxinfo complains about the following:
```
gandalf-desktop:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

I've reinstalled the driver but it's the same. Is there any known way to work around this?

---

### Post by el_itur on 2007-04-20
well slightly getting there. I've installed the glx-new  (nvidia's 9755) from synaptic and now everything works fine. The third mouse button ins't responding though

---

### Post by jfinkels on 2007-04-20
> **el_itur said:**
> well slightly getting there. I've installed the glx-new  (nvidia's 9755) from synaptic and now everything works fine. The third mouse button ins't responding though

You may be able to find the keycode using the program "xev" and then you could assign the button to do whatever you need it to do using the program "xmodmap" (I'm not exactly sure what command it would need to run...).

---

### Post by madcow72 on 2007-04-20
What does your Mouse configuration section from xorg.conf look like?
```
sudo gedit /etc/X11/xorg.conf
```
Mine looks like this:  
```
Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
```

---

### Post by el_itur on 2007-04-20
my xorg.conf looks like this 
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

```

I though xorg 7.2 catched the config on the fly. I belive the problem is related to that

---

### Post by Melonhead on 2007-04-21
I actually had the same issue come up for me on my mouse after I upgraded to Feisty.

Apparently one of my random extra buttons on my mouse got mapped as the middle mouse button, and my scroll wheel is no longer sending any mouse events when I press on it (according to xev).

You may want to check out the functionality of your mouse with xev to confirm that it's still getting mouse events.

---

### Post by el_itur on 2007-04-28
> **Melonhead said:**
> I actually had the same issue come up for me on my mouse after I upgraded to Feisty.

Apparently one of my random extra buttons on my mouse got mapped as the middle mouse button, and my scroll wheel is no longer sending any mouse events when I press on it (according to xev).

You may want to check out the functionality of your mouse with xev to confirm that it's still getting mouse events.

That's it the mouse isn't sending (or the server isn't receiving) the events of two of the five buttons. oddly the one that is sending events is one of the buttons that I've never used on linux (one of the side).

Could it be a xorg issue?. the hardware works well on windows.

---

