---
title: "Any one??? I NEED HELP! UPGRADED FROM 6.0 to 8.04 and lost all all text and backgroun"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by kwamex on 2008-09-28
I NEED HELP! UPGRADED FROM 6.0 to 8.04 and lost all all text and background...

After I upgraded from the update manager and restarted i lost all text all letters are now replaced with square boxes...also my background is completly black...all applications work fine games, web, etc..just no text or background...i can not navigate with text...icons show up just fine...what can i do???


i have no cd

please help...any commands that can restore my settings so i can have the desktop look normally...i checked and i knw i defintely upgraded fully to 8.04..let me know please....

---

### Post by run1206 on 2008-09-28
click the ubuntu sign at the top of your screen... that should send you to the main menu.  then scroll down til you see a picture of a computer (this should be the "System" box).  then the next windows should appear; scroll to the one that shows a pull down picture (this should be the Preferences selection).  then click the second choice from the tab (this should be the appearance button).  from there, click on the 3rd tab (which should be the Fonts Tab).  from there, you can check to see if any other fonts are available.  

i hope this helps.write back if you can get to it or not.

---

### Post by Sef on 2008-09-28
What languages did you have installed?

---

### Post by kwamex on 2008-09-28
I had english installed...

---

### Post by kwamex on 2008-09-28
i tried looking in the fonts menu but again all the fonts are just squares...no real fonts available..

---

### Post by mindoms on 2008-09-28
> **kwamex said:**
> i tried looking in the fonts menu but again all the fonts are just squares...no real fonts available..

have you tried one of the other fonts?
For sure you could not read them, because your current font doesnt work, but maybe they work.

If this didn't work:

maybe you dont have permissions to open the font-files:
run this in a terminal and post the output:
```
ls -ld /etc/fonts/ /etc/X11/fonts/
```

---

