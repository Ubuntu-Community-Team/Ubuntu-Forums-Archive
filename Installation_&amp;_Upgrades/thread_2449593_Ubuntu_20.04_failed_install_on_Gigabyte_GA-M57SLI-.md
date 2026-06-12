---
title: "Ubuntu 20.04 failed install on Gigabyte GA-M57SLI-S4"
date: 2020-08-30
forum: Installation &amp; Upgrades
---

### Post by dodgy geezer on 2020-08-30
[COLOR=#5F6368][FONT=arial][B]Hi,
[/B][/FONT][/COLOR][COLOR=#4D5156][FONT=arial]
[/FONT][/COLOR]I'm a Newbie to Linux - I'm trying to install Ubuntu [COLOR=#4D5156][FONT=arial]20.04 on a [/FONT][/COLOR]Gigabyte GA-M57SLI-S4 with 8Gb ram.   The install disk I am using has worked on another system, and I can install xUbuntu on this system, but when I try to load a full Ubuntu, the install process stops with the install bar showing 'Running update-grub'.  The cursor still moves.

If I try to push a few buttons, I can drop into a command-line window, which has the following last message:

"XDG_Runtime_DIR not owned by us (uid0) but by UID 999 - this could happen if you try to connect to a non-root Pulse Audio as a Root user over native protocol. Don't do that."

Further failures below occur - "Task ZPool 27382 blocked for more than 996 seconds"  and "Bad RIP value" lead onto dump messages from Ubuntu kernel. And then all I can do is power down.

Has anyone got an idea what I can do next?

Thanks....

---

### Post by yapidumoac on 2020-08-31
Try [[SOLVED] update-grub fails at install]("https://forums.bunsenlabs.org/viewtopic.php?id=4128")

---

### Post by dodgy geezer on 2020-09-01
Thanks for the response - reading it suggests to me that a bios update for this old motherboard might be an answer - I will try this...

---

### Post by dodgy geezer on 2020-09-02
Updated the Bios - and also noticed that you have moved from 20.04 to 20.04.01. So I re-burned a CD with the new O/S.

Loads perfectly now..... Thanks.

---

