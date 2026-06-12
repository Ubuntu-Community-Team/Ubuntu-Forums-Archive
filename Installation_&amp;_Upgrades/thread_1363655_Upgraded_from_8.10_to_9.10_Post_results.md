---
title: "Upgraded from 8.10 to 9.10: Post results"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by DThurman on 2009-12-24
[UPDATED via edits]

I have seemingly been able to upgrade from v8.04 to v9.10
but I am still left with some problems I have yet to resolve:

1) I cannot seem to figure out how to complete the updates as
   the Software Updater claims there is nothing update.  However
   I see this:

    # apt-get install -f
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

   Is there a command-line program I can use to force an update?

   Is there a command-line program I can use to do a complete integrity
   test to see if there are any obsolete programs left over?

2) When logging in as a user, there seems to be some problems:

    a) The login screen shows no background - just a plain solid
       orange background color & the login box itself is black.
       perhaps an issue with KDE/Gnome images lost during install?

[SOLVED b->d: Disable compriz via 'Change Background->Visual Effects: None']

    b) There are 1/4" black borders around all windows and it's
       applications including popups - wherever there is a window.

    c) The windows are very sticky and it takes quite some effort
       pry them away from whatever window or edges they are stuck
       to.  How can I reduce the sticky and attractors?  If in the
       compiz settings, what values are recommended for these?
 
    d) Everytime that I used the desktop switcher, this ugly popup
       appears and it is very distracting.  Also, I cannot drag a
       a window-application from within to another desktop.  Seems
       to do nothing at all.

    e) Compared to previous releases, the screen/operations appear to
       be rather sluggish and slow to keep up with the user's movements
       from typing to moving the mouse.  Is this due to compiz sucking
       up some bandwidth somewhere?  I have a fast Intel DQ35J0 MOBO
       w/ 2GB Fast RAM and a Intel(R) Core(TM)2 Duo CPU, E6750 @ 2.66GHz
       so why the sluggishness?  Is there a way to disable compiz to see
       if it is the program causing it?

[SOLVED: Change Appearance: Fonts tabs via Nautilus 'Preferences']
3) The screen appears to be rather huge for icons and fonts for a
   screen resolution of 1680x1050 for a 22" flat-screen?  Can this
   be adjusted?  Not sure this has anything to do with it, but
   during the upgrades, I was forced to remove fglrx as it caused
   the screen to get squished up to the top with about 1/4" height
   and removing it got my screen working.

   [^- fglrx has nothing to do with it & needed to be removed!]

That is all for now.

Thanks-
Dan

---

