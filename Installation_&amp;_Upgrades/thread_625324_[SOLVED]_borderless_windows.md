---
title: "[SOLVED] borderless windows"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by tal82k on 2007-11-27
I have a strange issue.  I just upgraded to 7.10 from 7.04.  When I restarted, My windows did not have title bars (nor minimize, maximize, and close).  I did look this up, and every response was about compiz.  I was unaware of having compiz (still don't know what it is).  I thought that perhaps my problem was a compiz problem.  I tried alt+F2, but that did nothing.  I went into terminal, and did```
emerald --replace
``` and my message was something like "emerald is not installed on your system.  You can install it by doing apt-get emerald install".  I thought 'hmm, it's not emerald'.  I tried ```
compiz --replace
``` and i had borders for a moment.  i closed a window, and my screen flashed.  Now I have no borders or a main menu bar at the top of GNOME or a bar at the bottom with the open apps.  This is only true if Firefox is the top window.  If I use alt-tab, i can view other windows and the top and bottom bars come back.  Still no title bar.

If it helps, my graphics card is nvidia 7600.

Any suggestions?

---

### Post by user1397 on 2007-11-27
> **tal82k said:**
> I have a strange issue.  I just upgraded to 7.10 from 7.04.  When I restarted, My windows did not have title bars (nor minimize, maximize, and close).  I did look this up, and every response was about compiz.  I was unaware of having compiz (still don't know what it is).  I thought that perhaps my problem was a compiz problem.  I tried alt+F2, but that did nothing.  I went into terminal, and did```
emerald --replace
``` and my message was something like "emerald is not installed on your system.  You can install it by doing apt-get emerald install".  I thought 'hmm, it's not emerald'.  I tried ```
compiz --replace
``` and i had borders for a moment.  i closed a window, and my screen flashed.  Now I have no borders or a main menu bar at the top of GNOME or a bar at the bottom with the open apps.  This is only true if Firefox is the top window.  If I use alt-tab, i can view other windows and the top and bottom bars come back.  Still no title bar.

If it helps, my graphics card is nvidia 7600.

Any suggestions?you need to disable compiz fusion completely because obviously your hardware or drivers have some sort of incompatability with compiz fusion (compiz fusion is the merge between 2 projects, compiz and beryl; emerald is the theme manager for beryl and fusion)

Go to either system > administration > screens and graphics, or system > preferences > appearance, i can't remember which.  you will see an option in one of the tabs to disable "desktop effects."

---

### Post by tal82k on 2007-11-27
That and rebooting seems to have done it.  Thanks!

---

### Post by user1397 on 2007-11-27
> **tal82k said:**
> That and rebooting seems to have done it.  Thanks!no prob.

---

