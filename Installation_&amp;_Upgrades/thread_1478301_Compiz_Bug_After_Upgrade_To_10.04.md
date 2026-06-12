---
title: "Compiz Bug After Upgrade To 10.04"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by dreamsburnred on 2010-05-09
:mad:  I upgraded to 10.04 and I seem to have found a compiz bug.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/576696](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/576696)

and 

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/433488](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/433488)

I have to run compiz from the terminal for the windows to appear right (otherwise there is clipping, everything clips on the top left when launched).

I have reinstalled compiz, and mesa.

What's left? :confused:

Intel 945GM.

EDIT: I Auto login and seem to have no boot splash. I do have a logout splash.

EDIT2: FIXED!!!

[LIST]
[*]Open System>>Preferences>>Startup Applications
[*]Select the ADD button to enter ADD Startup Application
[LIST]
[*]In the  Name field enter a value that will sort to the end-- I use zzz-fix  windows decoration
[*]In the command line enter:  /usr/bin/compiz --replace
[*]then save
[/LIST]
[/LIST]
from [http://ubuntuforums.org/showpost.php?p=9256230&postcount=25](http://ubuntuforums.org/showpost.php?p=9256230&postcount=25)

Blank boot splash is fixed with startup-manager selecting show boot splash.

---

### Post by DavetheDude on 2010-05-10
Epic fix. You win.

---

