---
title: "Intrepid Screen Resolution Problem"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Midnightsun on 2008-10-24
Hey guys,

My graphics adapter is an SiS Mirage 3, which unfortunately do not have linux drivers.  With hardy, I had to use vesa driver.  Whenever I did a fresh install of hardy, screen resolution would not allow me to select higher than 800x600 and to get around this I had to run ```
gksu displayconfig-gtk
``` and manually select my monitor (LCD 1024x800) and resolution.  Log out and in...Bob's your uncle.

Unfortunately, in Intrepid, this command (displayconfig-gtk) doesn't appear to open anything.  Does anyone know if this feature has not been included in intrepid, or has the command changed, or any other workaround to my problem?

Any help would be greatly appreciated.

---

### Post by Midnightsun on 2008-10-25
Sorry to bump guys but I'm getting nowhere fast with this problem and 800x600 is driving me insane.

---

### Post by xc3RnbFO8P on 2008-10-25
If you go System> Preferences> Main Menu> Other
can you see **Screen and Graphics**.

---

### Post by Midnightsun on 2008-10-25
Thanks for the reply!

I'm looking where you said, but can't see what you're referring to.  I'll include a screen shot to show what I mean.

---

### Post by xc3RnbFO8P on 2008-10-25
> I'm looking where you said, but can't see what you're referring to
Here is the reason why :)
[http://ubuntuforums.org/showthread.php?t=958392]("http://ubuntuforums.org/showthread.php?t=958392")

---

### Post by rue1341 on 2008-10-25
Many thanks Ringi this sorted out my screen resolution problem when I updated my system I now need to change my keyboard to a UK one.
Sorry I can't help with your problem Midnightsun.

---

### Post by Midnightsun on 2008-10-25
> **Ringi said:**
> Here is the reason why :)
[http://ubuntuforums.org/showthread.php?t=958392]("http://ubuntuforums.org/showthread.php?t=958392")

Thanks for the reply Ringi,

Unfortunately, the command that guy mentions (gnome-display-properties) brings up a window that only allows you to change resolution for the current monitor, not actually change the monitor which is what I require.

I'll upload a screenshot of the window I have to use in Hardy.  Hopefully what the chap in the other link suggests about gnome-display-properties replacing displayconfig-gtk is inaccurate.

I don't suppose, lacking a gui, anyone is aware of a way to manually edit the config files to achieve the desired result?

Thanks

---

### Post by Midnightsun on 2008-10-25
Just a not - attempted to manually add new resolution using xrandr (as per instructions from a helpful IRC chap) but that got us nowhere either.  

Would REALLY appreciate some help on this. Not only am I reduced to using 800x600, but because it's a laptop widescreen, some important windows go beyond the bottom of the screen preventing me from accessing settings, pressing OK etc!

---

