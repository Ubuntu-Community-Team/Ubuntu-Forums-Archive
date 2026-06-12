---
title: "Fresh Install won't login"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by hippykilla on 2007-08-16
I've just done a clean install of 7.04 onto my new laptop. The live cd booted perfectly, everything working sound wireless etc. 
I installed Ubuntu onto my HD and when it restarted for the first time it got to the Login screen, I entered my username and PW and clicked ok. 
The screen then just goes orange with some horizontal orange bar in the middle and a grey rectangle occupying the top left quarter of the screen. The system hangs here and I am unable to do anything

Specs are
Core duo t2080 @ 1.73ghz
1gig ram
120gig HD
128mb onboard intel gfx chip

Any help would be greatly appriciated :(

*EDIT*
If I hit esc at the GRUB loader and choose to boot in recovery mode then type "startx" at the prompt it goes into the gui fine. But it still wont boot normally

---

### Post by kraylus on 2007-08-16
boot into safemode, and open /etc/X11/xorg.conf or boot regularly and when the x server crashes hit CTRL-ALT-F1 and login there.

look and find what video driver its using. might even try bootin with the livecd and copying the xorg.conf it uses to yours.

we know the system works in safe mode, we know the live disc worked, so there's no reason this oughtta be happening. only culprit i can come up with is that file.

good luck,

ryan

---

### Post by hippykilla on 2007-08-16
I tried reinstalling ubuntu, now when I log in I get an error message and the system freezes. The error message is as follows: 

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in."

any ideas?

---

