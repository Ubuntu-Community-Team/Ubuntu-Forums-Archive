---
title: "Upgrade from 10.10 to 11.04..."
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by jim_naisium on 2011-05-04
Despite being warned from a friend of mine who works for Intel that the new version of Ubuntu 11.04 SUCKED I upgraded from 10.10 which worked perfectly fine and did everything that I wanted it to except work with my COBY MP3 player which is what I hoped 11.04 would do.

It all worked great until I rebooted.

I previously had the main screen on the left where all of the menus are and the right screen was the 2nd monitor.

Once it rebooted it let me login and loaded the desktop but the main screen is now on the right with that stupid application bar going up the side, all of my folders, etc. are all there but NOTHING is clickable, even the icons up in the right corner where you logout,etc. will not do anything other than highlight that you have clicked on them, the hard drive light flickers for a few moments then nothing. Also the left hand screen is completely blank unless I move the mouse cursor through it.

If I just leave the computer sitting there eventually the screens go dark and the monitor lights start flashing like it is supposed to but if I wiggle the mouse the screens come back on and the mouse is there but there is no login prompt to let me log back in.

Pardon my French but this OS is a piece of <bleep> and sucks just like I was told.

Ok, now that that is all over with... HOW DO I MAKE THIS OS WORK so that I can at the VERY LEAST click on something?

---

### Post by cbanakis on 2011-05-04
Sorry, but I have to say.

If it wasn't broke, why did you try to fix it?

I'm running 11.04, And I have to say its been good to me.

All that aside...

Having 2 monitors might be the root of the problem.

I would try and shut down, disconnect one, then boot up.

If all is well, then the driver may be the issue.

Installing restricted proprietary drivers for you video card may help.

---

### Post by jim_naisium on 2011-05-04
The reason that I put 11.04 on my system is that going clear back to v9.04 my Coby MP3 player has never worked with Ubuntu but works just fine with Windows XP, I was hoping that ~maybe~ it would be finally be supported under 11.04.

I have sort of figured this out and was thinking the same thing that you suggested and boot up with only one monitor plugged in, what it is doing right now is the weirdest bug that I have ever seen...

The screen with everything on it I cannot do anything with anything on the screen, but if I move my mouse to the exact same X-Y position on the blank screen as a folder, icon, menu option, button, etc. I can then open, copy, etc. (whatever) and it works, I'm sure over time I could probably get quite good at using it that way and it would probably be quite funny to watch people watch me try to use it way.

But for right now I have managed to figure out how to back up some files to the spare drive and then 10.10 is going on it if I can't figure this out within a reasonable amount of time.

---

### Post by cbanakis on 2011-05-04
lol

maybe it detected your monitor as a braille monitor?

Have you tried to feel your way over to update manager?

maybe there is an update that will fix this issue?

I think I have seen some updates come though that may be related.

---

### Post by jim_naisium on 2011-05-04
I figured it out finally, with one monitor attached it was forced into making the mouse work on the same screen.

At the login prompt after you click on your login name there is an option down at the bottom for "Ubuntu Classic" that gets rid of the vertical menu bar that nearly everyone I have read about hates.

11.04 disabled the graphics driver that I had been using with 10.04 and 10.10, I re-enabled it, plugged the other monitor in and rebooted, which after rebooting and turning on "Twin view" the other monitor popped on and started working just like 10.10 had been.

One thing that I have to say that I do like about 11.04 is that things in the System Menu (like display settings) no longer have to be SUDO'ed from a command prompt and just prompt you for the system password instead.

And I did need to do a back up anyway.

However... my MP3 player is still not being detected when I plug it in, but that is a battle for another day.

Thanks for the replies : )

---

