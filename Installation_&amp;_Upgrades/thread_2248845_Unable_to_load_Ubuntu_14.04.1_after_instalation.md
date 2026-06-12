---
title: "Unable to load Ubuntu 14.04.1 after instalation"
date: 2014-10-17
forum: Installation &amp; Upgrades
---

### Post by mathieu7 on 2014-10-17
I installed Ubuntu over Windows 7 (not a dual boot). When I turn on the PC, I see the Ubuntu logo for a few seconds and then just a black screen. I am able to press CTRL+ALT+F2 to get in the Virtual Console, so it's kinda of running I guess, but can't see the interface.

---

### Post by Bashing-om on 2014-10-17
mathieu7; Hi ! Welcome to the forum.

let's say this is - in all likely hood - a graphics driver issue,
Try this:
Reboot, as soon as the bios screen clears depress and hold the right -shift- key -> grub boot menu;
With the latest kernel highlighted press the 'e' key for edit mode -> boot option screen;
Arrow down and across to the terms "quiet splash" and add the term "nomodeset";
Key combo ctl+x to continue the boot process to the GUI login. Login here .
Do you now get to the GUI desktop ? Degraded graphics at this point is OK.

Next is to install the recommended graphics driver:
Left side of screen is the launcher ->ubuntu Software Center ->Software Sources(edit menu option on top task bar) ->Additional Drivers (tab in Software Sources) [must have 'net connectivity ]//assumes that 3rd party software sources have been enabled// Install the recommended driver.

Reboot, all good now ?

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

