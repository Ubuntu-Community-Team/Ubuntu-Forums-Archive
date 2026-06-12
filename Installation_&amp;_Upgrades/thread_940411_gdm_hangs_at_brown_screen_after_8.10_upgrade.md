---
title: "gdm hangs at brown screen after 8.10 upgrade"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by kmolnar on 2008-10-07
I just used "update-manager -d" to take a swing at Intrepid, and I'm encountering ... just this one issue, really:

First time I booted after installing Intrepid, I got X halting at its useless "x-shaped-cursor" stage, with no gdm. After a reboot and running xfix, I got to the normal gdm login screen and went to log in.

My default session hangs at the brown screen (of death?) between login and desktop.

Some potentially useful information:


[LIST]
[*]  I can successfully bring up the "GNOME Failsafe" session.
[*]I can get into a virtual terminal from the brown screen, but I'm not sure how to diagnose and treat the problem from there.
[*]I made a new user account to see if it's some kind of user-specific setitng thing, and it doesn't work either.
[*]I tried copying xorg.conf.failsafe over xorg.conf, which didn't solve the problem (although it did destroy my screen resolution -- good thing I backed up xorg.conf)
[/LIST]

As far as potentially X related stuff goes,...


[LIST]
[*]I used 915resolution to get my 1280x800 widescreen res to work, but that seems to be working just fine anyway, so I doubt it's the problem.
[*]Graphics are Intel GMA... about as standard as standard gets. It's using a plain ol' Vesa driver
[*]Compiz-fusion works fine when i start GNOME in failsafe mode, so I dont't think that's the culprit
[/LIST]

The one thing that I think might be involved is my UC-Logic tablet, which uses the Wizardpen driver. I used a HowTo on these forums to set it up, and it involved some InputDevice lines and such in xorg.conf, as well as modifying a startup script. Given as GNOME Failsafe circumvents these scripts, perhaps they are the issue?

(And before someone asks, I'll be digging out my xorg logs as soon as I get some spare time, and I'll post my xorg.conf too, if that would be helpful.)

I think the first thing I need to figure out is how to diagnose what's actually going wrong before I conjure up a wild goose to chase.

Any help would be greatly appreciated!

---

