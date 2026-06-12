---
title: "seeking Thinkpad X61 Tablet config help vs. Compiz"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2008-12-01
I have ubuntu hardy running on a Thinkpad X61 tablet along with compiz 3d effects. Compiz is not happy when I swap from landscape to portrait mode.

Anyone know how to:
1. cleanly toggle compiz(3d effect) on/off
[for those times when I want to do tablet things]

2) tell compiz to change geometry (and whatever else)
into portrait mode instead of landscape mode.

NOTE -- Other than tablet PCs, I know their are monitors that swap orientation. Has this problem been solved for them?

~~~ Saint 0;-D

---

### Post by norman_069 on 2008-12-04
Yes i am looking for this information as well

Thanks

---

### Post by SaintDanBert on 2008-12-06
I know a few things and think that I know about a few others. Mostly, I have questions. I would welcome any answers or pointers to answers so that this thread might form a complete explanation.

** something, somewhere says "enable" and "disable" for special (3d) desktop effects.

** something, somewhere says "use Compiz" for special (3d) desktop effects.

** something, somewhere says "use HxW as the physical screen geometry"

** something, somewhere says "use VVVxHHH as the screen resolution"

** I think that ACPI launches some script when the tablet changes from landscape to portrait display.

** I think that ACPI launches some script when the tablet changes from portrait to landscape display.

** I have no idea how ACPI gets told that the tablet display orientation changed.

** The standard (not special 3d) desktop properly reacts/responds to changes in table display geometry.

** I believe the standard desktop is gnome-desktop or something similar

** I have not tried any of this running KDE desktop

---

### Post by RoundSparrow on 2009-01-09
Older information, but gives you an idea of the drivers you are looking for:

[http://www.krizka.net/2008/01/23/thinkpad-x61-tablet-tilt-detection-and-ubuntu-hardy-heron/](http://www.krizka.net/2008/01/23/thinkpad-x61-tablet-tilt-detection-and-ubuntu-hardy-heron/)

---

### Post by Pumalite on 2009-01-09
[http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_X61](http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_X61)

---

### Post by SaintDanBert on 2009-01-11
Thanks to both RoundSparrow and Pumalite for the links.
There was much useful Think-tablet information on each source. The sources also lead to other pages with useful information.

I still seek a solution to my original problem:
1. Rotate the tablet screen from landscape to portrait.
2. ACPI scripts launch and run when change detected.
3. Scripts dance as required so that tablet features are enabled in portrait orientation. [Note 1]
4. Return the table screen to landscape format
5. More ACPI scripts launch and run when change detected
6. Scripts dance as required so that 3D-effects are enabled
in landscape orientation. [Note 2]

It would be wonderful if 3D-effects could learn to play tablet features as well as landscape.

Thanks,
~~~ 0;-D

___________________
Note 1. Out of box ubuntu hardy handles the switch when 3D-effects are disabled. Simple toggle-off-3D might be
all that is required.
Note 2. Out of the box Compiz-Fusion works fine in landscape format. Simple toggle-on-3D might be
all that is required.

---

