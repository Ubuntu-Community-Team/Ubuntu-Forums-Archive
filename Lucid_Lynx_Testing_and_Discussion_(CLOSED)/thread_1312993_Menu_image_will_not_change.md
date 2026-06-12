---
title: "Menu image will not change"
date: 2009-11-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-11-03
Ok, it is not breakage, but it will have to do for now.

I have 2 Lounge installs.  One is vanilla and the other an update 9.04>9.10>10.04.  This is a Stoner Edition so it is slightly modified but the upgrades have taken care of about all that except the theme so I do not think this is a factor.

The vanilla will change the theme fine.  The StonedLizard will not.

I have compared the 05_debian-theme file from both of them and they appear,except for the background image choice to be the same.  The images are the same size and resolution and both .png

WTF?

---

### Post by ranch hand on 2009-11-03
Well, that was no FUN at all.

I got the wild hair to do a transplant.  Cut the grub.d files in StonedLizard and put them in a new folder (grub.d.d), copied all the grub.d files from Lounge and pasted them to grub.d in StonedLizard.  Dumped the custom file and put the origanal back, changed theselected image to the one I am trying to use in StonedLizard, saved the file, ran update-grub and there it is in the terminal output.

There had to be something in there that was wrong but I sure could not see any difference in the two 05_debian-theme files or the 00_header files.

Beats me, but it works.

---

