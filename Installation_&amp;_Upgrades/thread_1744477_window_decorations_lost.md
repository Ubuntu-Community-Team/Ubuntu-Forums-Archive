---
title: "window decorations lost"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by QNo on 2011-04-30
Hi,

after upgrading from 10.10 to 11.04, at first everything worked fine. Then i changed the compiz configuration to cube, confirmed some questions, and now i have no window decorations. No icons for close, minimize, maximize. No resizing by mouse. No title bar.

In the launcher, i lost applications and files&??, and in the top menu bar, i lost the leftmost part, where some menus and the Ubuntu icon were found.

Seems i did something terrible wrong. How to repair?

TIA
Christian

---

### Post by mc4man on 2011-04-30
When switching to rotate/cube all the plugins got unset, you could go back into ccsm and start enabling them
or reset back to the defaults and switch from wall to rotate/cube in a less destructive way
which would you prefer

---

### Post by Papex on 2011-04-30
I have the same issue. I'm on Ubuntu Classic.

My window decorations are gone and emerald is not working. I use the Compiz fusion Icon to easily get to the Compiz settings. Now when I use compiz as window manager I loose Windows decorations and part of the windows disappear under the top panel.
When I'm NOT using Compiz as window manager Docky is in only in 2D and with no effects. 

Frustrating... :(

BTW: I'm using Ubuntu 64-bit and Nvidia driver and I've already checked the "Window decoration" box in the Compiz settings.

---

### Post by MugOTea on 2011-04-30
> **QNo said:**
> Hi,

after upgrading from 10.10 to 11.04, at first everything worked fine. Then i changed the compiz configuration to cube, confirmed some questions, and now i have no window decorations. No icons for close, minimize, maximize. No resizing by mouse. No title bar.

In the launcher, i lost applications and files&??, and in the top menu bar, i lost the leftmost part, where some menus and the Ubuntu icon were found.

Seems i did something terrible wrong. How to repair?

TIA
Christian

I just resolved this issue on my laptop - and your the first I'm telling so I hope it works for you too....

Basically stop using Emerald with unity for now.

1/ Open teminal
2/ Type: cd ~/.config/compiz
3/ Type: gedit compiz-manager
4/ Make sure it only says - USE_EMERALD="no"
5/ Save the file, and log off, and on again!
:guitar:

---

### Post by QNo on 2011-04-30
I tried a lot, and anyhow i got most of the desired results. Most.

> **mc4man said:**
> reset back to the defaults

How? I did not find a default-button.

---

