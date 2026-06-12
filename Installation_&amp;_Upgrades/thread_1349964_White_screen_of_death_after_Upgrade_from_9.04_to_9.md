---
title: "White screen of death after Upgrade from 9.04 to 9.10"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by fuwkej on 2009-12-08
Title says it all. System worked great with Jaunty. Upgraded to Karma (9.10) and after the splash screen & login, even the desktop loads with conky but then **the entire screen goes white**. I've upgraded distro's several times on this computer an never had this problem before. Attempted all the steps suggested in similiar threads, but I could not get a functional desktop. Played around with xorg.conf, and deleted it since many folks suggested it was not needed with the new versions (auto generates one).

I type <startx> on the command line in safe mode and it starts the desktop up, loads everything like a normal boot but freezes the same way. It's as if a process is killing the display and whiting it out. CTRL&ALT F1-F6 work fine even with the white screen for command line functions.

Video card is Intel Integrated Graphics (on-board graphics) and I'm using xserver-xorg-video-intel.

**Any suggestions are much appreciated**, as I'm at a loss for fixes at this point. Next time I get this system working I'm not upgrading until 15.10! Upgrades bring nothing but pain.

---

### Post by u.b.u.n.t.u on 2009-12-08
Q1. Is Ubuntu 9.10 your current installed version?

Q2. Does the file xorg.conf exist at the location /etc/X11 ?

15.10 is quite a ways away. I am sure that this issue will be resolved well before then.

---

### Post by jaylsi on 2009-12-08
If you are only using on-board graphics, I think your problem is most likely in gdm configuration. (since you have tried removing /etc/X11/xorg.conf and didn't help). Were you able to login successfully with 'failsafe gnome' mode? To do that:

1) On login screen, click user and type password, but don't hit enter yet
2) Select 'failsafe gnome' on session list at the bottom of screen
3) Now click login

---

### Post by fuwkej on 2009-12-08
Right, but 20 more will come up! :P

I had 9.04 installed and upgraded to 9.10. It started up fine, with the "fancy" new graphics, and then died and the screen went white. Xorg.conf did exist, I tried xorg.conf backups as well as X -configure copy as well as deleting it entirely. 

I think I'm somehow still using the Jaunty kernel as it is the older numbers. I noticed when I was looking here: [http://brandon-harris.com/2009/11/01/dell-studio-15-white-screen-of-death-karmic-koala-workaround](http://brandon-harris.com/2009/11/01/dell-studio-15-white-screen-of-death-karmic-koala-workaround)

I'm going to try to figure out how to use the newer kernel..


(Ah I love "upgrading" completing wasting 6 hours of my life, when all I want is a functional computer. "Upgrades" like this should stay in beta for a little bit longer where people with actual programming knowledge can deal with the minor issues that are major to me.)


Now I can't even get to the command line, lovely.

---

### Post by u.b.u.n.t.u on 2009-12-08
> **laverabe said:**
> I noticed when I was looking here: [http://brandon-harris.com/2009/11/01/dell-studio-15-white-screen-of-death-karmic-koala-workaround](http://brandon-harris.com/2009/11/01/dell-studio-15-white-screen-of-death-karmic-koala-workaround)

I'm going to try to figure out how to use the newer kernel.

Please keep us updated. As for the kernel, I would think that the latest may not be the best where a GPU and drivers are concerned.

---

### Post by fuwkej on 2009-12-10
Thanks for the help. I wasn't able to fix the problem (white screen, touchpad not working, and so on), but I was able to log in with gnome failsafe as jaysli suggested. That gave me enough access to back up everything and just do a fresh install. Everything worked on fresh install.. I think they should just disable the "upgrade" feature since it never works. I'll keep home on a seperate partition this time, so next time I "upgrade" I can just do a fresh install after it doesn't work.

Karmic Koala does look a little nicer.. we'll see.

---

### Post by u.b.u.n.t.u on 2009-12-10
Well it is good that you have your system up and running again!

---

