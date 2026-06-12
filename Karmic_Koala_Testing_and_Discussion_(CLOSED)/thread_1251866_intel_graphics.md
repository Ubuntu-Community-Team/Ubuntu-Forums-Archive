---
title: "intel graphics"
date: 2009-08-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wirate on 2009-08-28
In my preferences>display, I have 1024x768 as the maximum resolution. i would like a little more like I had in Jaunty.
I have Intel GMA 3100 and here's the xorg.conf output:

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

---

### Post by wirate on 2009-08-29
anybody?

---

### Post by warreno on 2009-08-29
> **waqar said:**
> anybody?

This is strictly a guess, but have you installed the third-party drivers package?

Go to Accessories -> Add/Remove and type "third" into the search field. If the item labeled "Hardware drivers" is unchecked, check it and click "Apply Changes". (See the attached screenshot.)

If it's already selected, it might be better to get into Synaptic Package Manager (System -> Administration -> Synaptic Package Manager) and see if there's Intel graphic support there, or another set of third-party or proprietary drivers you can install.

EDIT: Oh yeah. Then go to System -> Administration -> Hardware Drivers, I suspect, and see if there's anything there that seems useful.

Hope this helps…

---

### Post by taavikko on 2009-08-29
> **warreno said:**
> This is strictly a guess, but have you installed the third-party drivers package?

Go to Accessories -> Add/Remove and type "third" into the search field. If the item 

There is no restricted driver for intel chips.

For OP, try booting with "nomodeset" if it clears the resolution.

---

### Post by seeker5528 on 2009-08-29
> **waqar said:**
> In my preferences>display, I have 1024x768 as the maximum resolution. i would like a little more like I had in Jaunty.

Assuming it works... :roll: the easy solution would be to add a display subsection in the screen section with the additional modes you want to use and the mode you want as the default listed first, so if you wanted to keep 1024x768 as the default resolution and add some additional higher resolutions the screen section might then look something like:

```

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
		Modes		"1024x768" "1280x1024" "1600x1200"
    EndSubSection
EndSection
```

The way I read it other detected resolutions should continue to be available without having to be specifically listed. If X thinks the hardware is incapable of displaying the listed resolutions it will not make them available and some other hackery will be needed.

I have not had to mess with this stuff much so my trouble shooting skills in this area are a bit deficient, so if another solution is needed maybe someone else with Intel specific experience or that knows some modeline voodoo will chime in.

Later, Seeker

---

