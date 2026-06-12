---
title: "Unity Greeting Screen text Problem after upgrade to 3.16.2 kernel"
date: 2014-09-16
forum: Installation &amp; Upgrades
---

### Post by gpolkga on 2014-09-16
[ATTACH=CONFIG]256478[/ATTACH]


I'm using Ubuntu 14.04.1.   After upgrading the Linux Kernel to 3.16.2, the Unity Greeting screen text is unreadable.  Only the text is a problem.  Otherwise, the screen is fully functional as long as I know what to choose and where to type - i.e.  I can enter my password and continue.   When I logout the greeting screen then appears normal (with all user names and menu information correct).   I am not using any additional drivers.

Anybody have any ideas?   

Thanks.

---

### Post by gpolkga on 2014-09-18
Can anyone give me ideas on how to solve this ??

---

### Post by grahammechanical on 2014-09-18
Are the icons at the top right correct? They do not look correct to me. Have you installed another theme? Try switching themes.

---

### Post by gpolkga on 2014-09-19
Yes, all the icons are ok.  All images seem ok, it's only the text that is not correct.  Text characters do not seem distorted but rather just random and/or incorrect characters.  I'll try changing the theme and see what happens. 

Thanks.

---

### Post by gpolkga on 2014-09-22
I tried using another theme but the same problem exits.  The characters that I can see seem to be correct but are too spread out with some characters missing.  It's almost as if the font is incorrect.

---

### Post by gpolkga on 2014-10-10
Was finally able to solve this minor issue.  The solution was to revert back to an earlier kernel.  The original problem I was having with 3.13.x seems to have been fixed with the 3.14.xx (something to do with 16 bit segmentation) AND my login screen is back to normal.  Very interesting though that a kernel change would break the greeting screen to begin with.   I obviously don't understand the technical reason behind this.

---

