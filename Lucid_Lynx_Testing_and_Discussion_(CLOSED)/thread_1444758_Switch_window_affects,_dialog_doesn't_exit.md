---
title: "Switch window affects, dialog doesn't exit"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by muecker on 2010-04-01
I just upgraded from Karmic to Lucid. On my machine, compiz hasn't wanted to auto-start for the last couple of releases (not sure why).  When I change the visual effects from None to Normal, I get a dialog where it checks for drivers (I'm using ati).  After turning on the visual effects, I get a dialog to either revert or keep the current config.  I click Keep and the dialog never goes away.  I have to use xkill to get rid of it.

None of this process has changed from Karmic to Lucid.

A similar thing happens with the calendar, I don't have evolution configured on this machine so clicking on the calendar reports an application problem (evolution-data-server-2.28 closed unexpectedly) and the calendar will never close at that point.  This error has happened under previous releases, usually it just caused the panel to crash and reload.

I'm not sure if the two problems are related.

---

### Post by ajgreeny on 2010-04-01
> **muecker said:**
> I just upgraded from Karmic to Lucid. On my machine, compiz hasn't wanted to auto-start for the last couple of releases (not sure why).  When I change the visual effects from None to Normal, I get a dialog where it checks for drivers **(I'm using ati)**.  After turning on the visual effects, I get a dialog to either revert or keep the current config.  I click Keep and the dialog never goes away.  I have to use xkill to get rid of it.

None of this process has changed from Karmic to Lucid.

A similar thing happens with the calendar, I don't have evolution configured on this machine so clicking on the calendar reports an application problem (evolution-data-server-2.28 closed unexpectedly) and the calendar will never close at that point.  This error has happened under previous releases, usually it just caused the panel to crash and reload.

I'm not sure if the two problems are related.

Which ati card do you have?  I run a 9200SE with the open source driver, and it works fairly well in karmic with compiz, provided I use 16 bit colour.  I presume you are also running the OS driver, or the system would not search for another one when you use "normal" desktop effects.

---

### Post by cianca on 2010-04-01
Same problem here, i'm using a 9200SE

---

### Post by TChiOBi on 2010-04-02
similar problem
using nvidia gt8500
nvidia drivers: 195.36.15

---

### Post by ajgreeny on 2010-04-02
@ meucker

Try running your 9200SE with both the open source driver and an /etc/X11/xorg.conf based on mine, which I know works fine in karmic with 16 bit colour, but gives no desktop background with 24 bit.

Here's the working info from my file; just change the figures to suit your screen display, and with luck it will work in both karmic and lucid, the latter of which I still have yet to try.
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

```
EDIT:
I have just installed lucid daily build from April 2 to a test partition I keep for such things on my machine, and am surprised to see tha same thing happening on mine, ie, if I use the Visual Effects tab of System-Preferences-Appearance to change from either normal or none to extra, it just sticks on the screen.  I can remove it with ```
killall gnome-appearance-preferences
```and the new setting sticks, but it's annoying.  The same may happen in karmic, but I always use compiz-switch normally to turn compiz on and off so I don't really know about that ubuntu version; I will try when I am using it next.

At least in lucid it is not necessary to use the 16 bit colour with compiz as the 24 works just as well, or badly, depending on your point of view.

---

