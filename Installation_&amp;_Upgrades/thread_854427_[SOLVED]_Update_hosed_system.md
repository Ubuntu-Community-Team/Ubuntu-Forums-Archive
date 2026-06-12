---
title: "[SOLVED] Update hosed system"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by billinmd on 2008-07-09
Ok, I took the plunge, setup 8.04 and all was well. Did all updates and the following things are hosed:

1) no min, max or close buttons on any window (they were there before)

2) no sticky keys or mouse keys (previously working)

3) can't change touchpad settings (previously working)

That's the three I've found so far. Any ideas where to start? Am I looking at a re-install?

Hardware is Dell C610 laptop P3 1.2ghz w/512mb ram.

TIA

---

### Post by unoodles on 2008-07-09
try creating a new test user and see if any of the issues are fixed when you login (as the new test user), if so you know that the problems lie in hidden folders in you /home/<user> folder. You could also try using sudo dpkg-reconfigure on some stuff (maybe metacity and xserver-xorg). If not of this does anything, you may be looking at a re-install.

---

### Post by billinmd on 2008-07-09
Ok, progress...

I noticed when I clicked Quit it bounced me to the login screen. Got that straight by fixing the session menu with gtweakui from the repositories. Once that was fixed sticky key/mouskeys and touchpad settings were back.

As far as the min, max, close goes, you pointed me in the right direction! Reconfiguring metacity/xserver didn't help. However reinstalling metacity and metacity-common fixed it right up!

i'm a happy camper again...thanks!

---

