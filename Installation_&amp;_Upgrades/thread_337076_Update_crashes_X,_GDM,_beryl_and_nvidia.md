---
title: "Update crashes X, GDM, beryl and nvidia"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by jbtito03 on 2007-01-12
Hi folks...

Okey... my last update crashed it all :D

I had to reinstall xorg, nvidia and gnome cause nothing seemd to work anymore. How could something like this happen. Now i have a so so crippled system.

For example my keymaps are gone.... dunno what to do.. reconfigured xorg and did set it up in gnome.. manually searched in the xkb dir and nothing there... sucks...

beryl however did not run.. tried to reinstall but... the repo is down... so...

anyone with same problem and/or any awnsers/solutions...

cheers

JB

---

### Post by dabl on 2007-01-12
I can confirm that Beryl and its "Windows Decorators" can indeed crash things including your desktop, taskbar, and composure.  That is related to Beryl's development status at 0.1.4 (if I got that right) -- it's far less than stable.  On my Kubuntu Edgy system, for example, if I choose the Aquamarine Windows Decoration from the Beryl menu, my taskbar goes bye-bye, windows have no borders, and I have to Ctrl-Alt-F1 to a console screen to get back any ability to control the system.  Then there's some fiddling around to restart the xserver and pop up the Beryl menu and choose "KDE" for the Windows Manager, and then another re-start of xserver and finally when I choose "Emerald" for the Windows Decoration I can go back to "Beryl" as the Windows Manager.  I guess you could say it's a "Beryl in the rough"? :mrgreen:

---

### Post by Pobega on 2007-01-12
This has been reported multiple times, and yeah, update breaks Beryl because it's unofficial and in *beta*, which means it isn't stable and is not guaranteed to be stable.

---

