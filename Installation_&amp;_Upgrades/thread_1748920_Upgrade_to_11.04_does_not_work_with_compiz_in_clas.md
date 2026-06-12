---
title: "Upgrade to 11.04 does not work with compiz in classic view, no title bar!!"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by gioman22 on 2011-05-04
So I've upgraded, and its a been  a nightmare since! I not to ecstatic about unity and when reverting back to ubuntu class from the login session I now find that if I enable compiz I have no title bars and no close, maximize or minimize buttons and half of the compize effects are gone...

I'm strongly considering reinstalling 10.4 again.. Has any one else got this issue or found away arround it

---

### Post by ingenierox on 2011-05-04
> **gioman22 said:**
> So I've upgraded, and its a been  a nightmare since! I not to ecstatic about unity and when reverting back to ubuntu class from the login session I now find that if I enable compiz I have no title bars and no close, maximize or minimize buttons and half of the compize effects are gone...

I'm strongly considering reinstalling 10.4 again.. Has any one else got this issue or found away arround it

I have the same issue i have to configure the CompizConfig Settings Manager to defautl settings and then It works  but i loose all the cool stuff in the compiz cube, effects etc:frown:

---

### Post by [z]er0 HP on 2011-05-04
I've also got this same issue. Feeling a bit let down on the latest "upgrade"....

---

### Post by gioman22 on 2011-05-05
I'm currently being forced to use compiz fusion icon to switch my window manager each time I log in to Matacity, just so that I can work....

Is there any work around this issue, I can live with some of the compiz effect being gone but I need that title bar with minimize, close and maximize button...

HELP?

---

### Post by TennSeven on 2011-05-05
I had the same problem.  Upgrading to 11.04 really did nothing for me except disable just about every visual plugin I was using in my desktop, and break a few other things in xorg (for instance, now when I minimize windows in the window list they will sometimes jump out of place and into the end of the list, and now a lot of files are unresponsive to my mouseclicks when I try to open them).

At any rate, to fix your issue with the title bars:

Go to System -> Preferences -> CompizConfig Settings Manager, and enable "Window Decoration" in the "Effects" category.

-TennSeven

---

### Post by gioman22 on 2011-05-05
> **TennSeven said:**
> I had the same problem.  Upgrading to 11.04 really did nothing for me except disable just about every visual plugin I was using in my desktop, and break a few other things in xorg (for instance, now when I minimize windows in the window list they will sometimes jump out of place and into the end of the list, and now a lot of files are unresponsive to my mouseclicks when I try to open them).

At any rate, to fix your issue with the title bars:

Go to System -> Preferences -> CompizConfig Settings Manager, and enable "Window Decoration" in the "Effects" category.

-TennSeven

It alive :guitar:... Thanks for that, heads up though when doing this make sure that you using GTK window decorator, emerald doesn't work the the title bars just disappear again

---

### Post by OzzyFrank on 2011-05-16
Any ideas on how to actually get Emerald themes happening again? I have a white text on white titlebar that is getting a tad annoying.

---

