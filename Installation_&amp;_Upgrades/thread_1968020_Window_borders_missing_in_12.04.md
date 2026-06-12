---
title: "Window borders missing in 12.04"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by AKADAP on 2012-04-28
I just upgraded to 12.04. I had been using gnome classic, but now I get no window borders or windo manipulation icons.

I tried unity, but I got nothing but the windows for the programs that auto run there (terminal, and skype). It did not seem that any part of unity was running.

I tried normal GNOME (this is what I'm using at the moment) this has window borders and title bars with a close icon (not sure if this is normal since I did not use it under 11.10).

Any suggestions on how to debug this issue?

---

### Post by simbot on 2012-04-28
Try gnome classic (no effects). I'm also having similar issues, which I believe are related to this bug in compiz [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/973559](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/973559)

---

### Post by AKADAP on 2012-04-28
> **simbot said:**
> Try gnome classic (no effects). I'm also having similar issues, which I believe are related to this bug in compiz [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/973559](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/973559)

Yah, that looks like what I am seeing. gnome classic (no effects) is working thanks.

---

### Post by mjpoetic on 2012-04-29
Hey you guys...make sure you have ccsm (Compiz Config Settings Manager) installed and check the "Window Decoration" section. Under command I had "emerald --replace" listed as the command and had to reset it to the default for window decorations to reappear.  It may work this way for you too.

---

### Post by AKADAP on 2012-04-30
> **mjpoetic said:**
> Hey you guys...make sure you have ccsm (Compiz Config Settings Manager) installed and check the "Window Decoration" section. Under command I had "emerald --replace" listed as the command and had to reset it to the default for window decorations to reappear.  It may work this way for you too.

I just tried this with no luck. My window decorations were already set to the defaults. Still no decorators on Gnome Classic, only Gnome Classic (no effects)

---

### Post by mjpoetic on 2012-05-01
Oh my instructions would only apply if you're using Unity. With GNOME, everything is controled through Advanced Settings. Install it through Ubuntu Software Center if you haven't already. Then you can control window borders and other things there

---

### Post by AKADAP on 2012-05-01
> **mjpoetic said:**
> Oh my instructions would only apply if you're using Unity. With GNOME, everything is controled through Advanced Settings. Install it through Ubuntu Software Center if you haven't already. Then you can control window borders and other things there

I have no menus at all when I try and run Unity. Something broke when I tried to use it under 11.04 and it did not get fixed under 12.04 All I get are a few programms running that are auto-run, their windows have no decorations and are not movable. Luckally one of them is a terminal window so I can cleanly restart my system.

---

### Post by AKADAP on 2012-05-05
I have partially recovered from this, and I think I know how to proceed to fix the rest.

It appears that a bunch of the settings on the "CompizConfig Settings Manager" got wiped out.

I was able to get the decorations back under Gnome Clasic, and get Unity running again. But for some reason under Gnome Classic, the applications menu bar is missing, and changing settings in Gnome Classic, affects Unity.

I need to do a clean install on a spare disk, and see if I can find the differences.

---

### Post by elomage on 2012-05-14
You may get the borders back by entering the following (from a terminal):

 compiz-decorator

--Leo

---

### Post by threepwood960 on 2012-07-04
I have this same problem, but I cannot get back the icon arrows (up and down). Any idea?

---

