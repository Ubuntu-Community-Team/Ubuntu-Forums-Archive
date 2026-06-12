---
title: "Strange mouse cursor problem in Unity-based Ubuntu"
date: 2012-04-01
forum: Installation &amp; Upgrades
---

### Post by fizyxnrd on 2012-04-01
I have been trying to install a newer version of Ubuntu to a ThinkPad T60 (model 2613-HKU to be precise).

I have tried both CD and USB installations of 11.04, 11.10, and 12.04-beta2.  All installations have failed to produce satisfactory installs.
The 12.04-beta2 version appears to give a clean install, but does not boot, displaying only a desktop background.
The 11.x versions install cleanly, but the graphics are slightly glitchy (icons flicker on mouse-over).  And here's the really odd part:  I can move the mouse around the screen (verified by enabling "show position of pointer when control key is pressed" courtesy of assistive technologies), but the cursor itself doesn't move.  I'm flying blind, except when I press Ctrl.

These were clean installs, with updates downloaded and installed at installation, and not upgrades.
I've now installed 10.10, with absolutely no issues.

Any idea what could produce (and better yet, solve), this strange problem, so I can finally upgrade to modernity?

---

### Post by Paddy Landau on 2012-04-02
Two suggestions, but I'm not at all sure they would work.

After installing, when you get the desktop background and no launcher, open a terminal (Ctrl-Alt-T).

[LIST=1]
[*]Enter the command [FONT=Lucida Console]jockey-gtk[/FONT] to check if you need extra drivers. If you see any, try enabling them and reboot.
[*]Type the following command to reset Unity and get your Launcher:```
unity --reset
```It can take several minutes (really!), so be patient; if it takes more than about 10 minutes, you may need to cancel. Log out and in again (or just reboot).
[/LIST]

---

### Post by fizyxnrd on 2012-04-03
Thanks, I'll give this a try in a couple of weeks when my lappy isn't mission critical.

---

