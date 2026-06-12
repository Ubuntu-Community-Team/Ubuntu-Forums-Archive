---
title: "Desktop problem with 9.10 upgrade"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by cactusgal on 2010-03-31
I finally decided to upgrade my Ubuntu Studio from 9.04 to 9.10. Things went well for the most part (other than that I'm disappointed that I can no longer choose login screens). However, after the graphics card drivers installed and I set the visual effects to 'extra' my desktop went black. All the files are still there (in Home/Desktop) my wall paper shows in the panel (because I have it set to transparent) and I can see it as the computer is shutting down but other than that it's a black. Any ideas how I can fix this? I've searched the forum but couldn't find anything specific to this issue

Regards,
cactusgal

---

### Post by ajgreeny on 2010-03-31
You must have an ati graphics card with the open source driver, and are running compiz at a resolution of over 1024x768 at the default 24 bit colour.

Either use 16 bit colour or stop compiz with ```
metacity --replace
``` in the Alt+F2 run-dialog box.

I use 16 bit colour _and_ compiz, but to do that I have edited my /etc/X11/xorg.conf file as follows:-
```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
EndSection 

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```Put your own display figures in and give it a try.

---

