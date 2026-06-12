---
title: "System all a mess after attempted upgrade to Gutsy"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by MattAd on 2007-10-22
Okay, so I attempted to upgrade to Gutsy. Everything was doing fine until the packages linux-restricted-modules and ttf-opensymbol, which the upgrade manager choked on with an ld_static: final link failed: Input/output error. There's all sorts of fun "ata1.00: exception Emask (big block of hex numbers)" which I'm assuming is a disk read error, so that might be something really bad that's hosing any attempt to upgrade or update my laptop.

When I restarted (which, granted, was probably a Bad Idea), GNOME was completely unusable, getting stuck into some sort of loop before it gets to the login screen- I can't even switch to a different terminal to see what's going on in the background. I've managed to get into recovery mode, and get my wireless card up so that I can use apt, but I have no idea where to go from here.

I'm just worried because this is my only computer, and it has a lot of work stored on it... I don't have any way to back up my files on it at the moment, and really can't afford to wipe the whole hard drive. Any suggestions?

---

