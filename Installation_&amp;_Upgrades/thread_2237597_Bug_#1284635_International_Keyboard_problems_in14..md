---
title: "Bug #1284635 International Keyboard problems in14.04"
date: 2014-08-02
forum: Installation &amp; Upgrades
---

### Post by elpidiovaldez5 on 2014-08-02
Lubuntu 14.04 release notes state that there is a bug affecting many none-US keyboard layouts.  It suggests removing ibus fixes the problem, citing bug report 1284635 .

I have read the bug report and it recommends removing ibus, but then somebody comments that ibus is necessary to Lubuntu Desktop, then it all just peters out. Another person says that for Croatian keyboards 'In Lubuntu just go to "Preferences &#8594; Language Support" and on "Language" tab set "Keyboard input method system" to "none".'.  There are no further comments on that solution.

Is there any consensus on how to fix this problem ? An actual procedure to follow would be useful for those who don't really know what ibus is or how to remove it. 

I have not installed Lubuntu 14.04 yet, and I don't want to unless I have a solution to this problem. It seems to be quite a big issue, affecting most of the world, and yet I just cannot find out if it has been solved or not.  The same bug is reported in the release notes of 14.04.1 so it does not appear that anybody is trying to fix it very urgently.

---

### Post by mikewhatever on 2014-08-03
You probably shouldn't worry about it too much, get Lubuntu installed, and see what happens. If affected by the bug, try some of the workarounds suggested, and if not, then ...worry about something else.
Most of the world has never heard about Lubuntu, let alone being affected by its bugs.

---

### Post by Dennis N on 2014-08-03
> **elpidiovaldez5 said:**
>  Another person says that for Croatian keyboards 'In Lubuntu just go to "Preferences &#8594; Language Support" and on "Language" tab set "Keyboard input method system" to "none".'.  There are no further comments on that solution.

Is there any consensus on how to fix this problem ? An actual procedure to follow would be useful for those who don't really know what ibus is or how to remove it. 


This was discussed on this forum on this thread:
[http://ubuntuforums.org/showthread.php?t=2227109](http://ubuntuforums.org/showthread.php?t=2227109)
The same solution that you mention is given there in post #3, and works fine (I used it).  ibus is not uninstalled and can be reenabled easily.


> Specific to Lubuntu there is a permanent fix through Language Support:

Code:

```
Preferences > Language Support > (close any pop up window) > Keyboard Input Method System > change from ibus to none.
```

Permanent, in that once set, you don't need to repeat this. 

---

### Post by vasa1 on 2014-08-03
> **elpidiovaldez5 said:**
> ... It seems to be quite a big issue, affecting most of the world, and yet I just cannot find out if it has been solved or not.  The same bug is reported in the release notes of 14.04.1 so it does not appear that anybody is trying to fix it very urgently.
Lubuntu is developed by volunteers who have limited time at their disposal. If you want an operating system which "fixes" things urgently, please look elsewhere. I'm quite happy with Lubuntu and the solution described by Dennis N works for me.

---

### Post by elpidiovaldez5 on 2014-08-18
Thanks for the information. 

The thread referred t by Dennis N seems to be about keyboard not responding, as opposed to the international keyboard problem, which is to do with incorrect keyboard layout.  Nonetheless they appear to have the same solution. I can only assume that most people find a satisfactory workaround fairly quickly or the problem would be more widely discussed.

---

