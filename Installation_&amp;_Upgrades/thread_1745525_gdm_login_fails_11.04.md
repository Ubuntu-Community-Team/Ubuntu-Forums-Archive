---
title: "gdm login fails 11.04"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Will B-R on 2011-05-01
After login-in with gdm, the desktop fails to launch.

I can only move the mouse, clicking does nothing, no hotkeys; no desktop.

All I can do is change to a TTY.

I have tried restarting the gdm service; this just lets me log in again to the same stalled desktop.

The panel at the bottom of the gdm doesn't list any sessions, all it has is universal access and the time.

---

### Post by drpjkurian on 2011-05-01
after login please type
> startx
then repair the broken packages through synaptic package manager

---

### Post by Will B-R on 2011-05-01
startx doesn't do anything because gdm is already running.

aptitude doesn't list any packages as been broken.

---

### Post by drpjkurian on 2011-05-04
Hi
I did not understand what do you mean by there is no 'desktop'. Does it mean that there are no click-able icons on the panel?

Can you give a screenshot of the screen.

---

### Post by khantastic on 2011-08-15
I'm having the same problem. After providing username and password I just get a desktop with no icons or panels. I can move around the mouse but nothing to click on.

It seems GDM is not able to continue to load my settings.

---

### Post by uBoldie on 2011-08-17
Hi All,
I'm trying to fix Ubuntu 11.04 with a similar problem for a friend.
I can log in, but OS moves to a black background with a white section in the top LHS.
I am at level 5 ('sudo runlevel <CR>').
Ubuntu updates worked.
startx doesn't do anything because gdm is already running.
The command line interface works, no GUI.
I have a desktop with no icons or panels. I can move around the mouse but nothing to click on. The CLI only works if the cursor is within the white area.
This PC works in dual boot mode with Vista as the other OS.
6 hours on this problem without any further progress.:confused:
TIA for any assistance.

One week later: after spending 8 more hours, I saved all the data files + email files, then reinstalled Ubuntu up again from scratch, then put all the data, etc, back, and returned laptop back to my friend. Pity I did not learn what the problem was......

---

