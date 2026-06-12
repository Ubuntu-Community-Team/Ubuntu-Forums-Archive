---
title: "linux crashes after booting from cd"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by garis94 on 2013-04-27
[COLOR=#000000][FONT=sans-serif]Hello everybody!.[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]I download Ubuntu 12.04.01 because I have an Ati HD 3850 that need some particulars requirements so that the official catalyst driver can work. On the screen that shows the options of booting i select "start linux from CD" with the option "nomodeset", after the screen that shows the lines "Ubuntu 12.04" the system show a black screen with the mouse that does not move smoothly. [/FONT][/COLOR][IMG]http://www.kubuntuforums.net/images/smilies/angry.gif[/IMG]
[COLOR=#000000][FONT=sans-serif]Someone has any idea to solve this problem?[/FONT][/COLOR]

---

### Post by dino99 on 2013-04-27
nomodeset is the worst setting to boot with; select & test the other acpi/apic/lapic options (hit F6 while booting)

---

### Post by garis94 on 2013-04-27
Thanks anyway, but I have solved the problem!
I start linux with the on board video card, install the official amd driver, shutdown the system, attach the cable of my screen in the screen port of my ati card, boot linux, reinstall the driver and now all works perfectly :)

---

