---
title: "White Screen covers desktop"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by onewaylimited on 2011-10-14
I just upgraded to ubuntu 11.10. When i opened it up, all i had was the desktop and one shortcut. After some digging, i went into terminal and reset unity. Now, whenever I boot up, the log in screen works fine, but the desktop is a large blank white screen. The unity toolbar is on the side with no icons. (although i can hit icons and they will start, right clicking works and i can see that) The only problem is they all start behind this white screen which makes them difficult to use. Please help!

---

### Post by EvilBro on 2011-10-14
I am running the live-CD and I am encountering the same problem (so I won't update for real). After booting up I get a blank white screen with a panel at the top and the unity toolbar. I select 'dash' and start an xterm. I type 'metacity --replace &' and things become visible (but I lose the top panel).
'usr/lib/nux/unity_support_test -p' says I am using Gallium 0.4 on NV36 (which seems right as I have a GeForce FX5700). All tests say 'yes'.

If I do a 'compiz --replace' I get the white screen. If I do a 'unity --reset' I get the original situation again (no icons, white screen, top panel).

Is this a compiz thing as 'compiz --replace' gives me the white screen?

---

### Post by onewaylimited on 2011-11-02
Ok, after three fresh installs of the Ubuntu 11.10, my problem is fixed. Well more or less. Now gnome3 is lagging so badly its unusable but i think thats a different thread.

---

### Post by Trent T on 2012-02-27
Same thing happened to me, EvilBro, when I upgraded from Ubuntu 10.10 to 11.04.  This one is described in launchpad bug report #763680, entry #7.

I may have found a work-around for it;

Work-Around;

Go to Preferences/Power Management/On AC Power
    Setting "Put computer to sleep when inactive"
    Change to "Never."

Go to Preferences/Screensaver
    Select a screensaver (vs default, which is 'blank')
    Uncheck "Lock screen when screensaver is active"

Since making these changes, I have not had the white screen problem.

Non-programmer comments;

I found that blank white windows still contained clickable objects (which I could not see, but that I could activate by hovering the mouse in areas where clickable links should be.  A comment box would sometimes pop up on the white screen.  Problem is thus likely to be a bug in rewriting the content of the window...

The 'white screen' with loss of all function happened when I left my computer idle for 5 minutes or longer.  It seems that Ubuntu locked itself and was probably waiting for me to re-enter my password.  However, I could not see the login screen.

Disabling the sleep function and leaving Ubuntu unlocked when the screensaver is active seems to have solved these problems.  

This condition may have been fixed in Ubuntu 11.10 -- In a few weeks, I may even get the courage to upgrade further ;-)

--Trent T


> **EvilBro said:**
> I am running the live-CD and I am encountering the same problem (so I won't update for real). After booting up I get a blank white screen with a panel at the top and the unity toolbar. I select 'dash' and start an xterm. I type 'metacity --replace &' and things become visible (but I lose the top panel).
'usr/lib/nux/unity_support_test -p' says I am using Gallium 0.4 on NV36 (which seems right as I have a GeForce FX5700). All tests say 'yes'.

If I do a 'compiz --replace' I get the white screen. If I do a 'unity --reset' I get the original situation again (no icons, white screen, top panel).

Is this a compiz thing as 'compiz --replace' gives me the white screen?

---

