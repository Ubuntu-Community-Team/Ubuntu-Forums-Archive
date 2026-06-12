---
title: "Defining a monitor in KDE"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by shultzjr on 2007-02-10
I just installed Kubuntu 6.10 on a clone.  Everything went ok except that the monitor which is a Dell Ultrascan 15TX was defined as a generic 800x600 crt.  The manual says that the monitor should go up to 1280x1024.   I looked at xorg.conf and it doesn't seem to show any clues on how to define this thing.  I found the following specs:

horizontal: 31.5 - 64
vertical:  50 - 120

                      horizontal      vertical
640x480        31.4                59.8
640x480        37.9                72.8
720x400        31.5                70.1
800x600        37.9                60.3
800x600        46.9                72.2
1024x768      56.5                70.1
1024x768      60                   75

So what do I put in the xorg.conf file?

thanks,
charles.....

---

### Post by daou on 2007-02-11
Edit the monitor section so it looks similar to this:

```
Section "Monitor"
    Identifier     "Monitor0"
    ModelName      "Dell Ultrascan"
    HorizSync       31.5 - 64.0
    VertRefresh     50.0 - 120.0
    Option         "DPMS"
EndSection
```

Then edit your screen section like this:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0" # Change this to your device Identifier name
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768"
    EndSubSection
EndSection
```

If you change your screen identifier, make sure you put the same name in the screen field in the ServerLayout section.

This should allow you to change between 1280x1024 and 1024x768 resolutions. If you get stuck on the lower resolution, try removing the 1024x768 res from the screen section.

---

### Post by daou on 2007-02-11
Always make a backup of your xorg.conf file before you edit it!
So if xserver fails to start, you can replace the faulty one with the backup from command line.

---

