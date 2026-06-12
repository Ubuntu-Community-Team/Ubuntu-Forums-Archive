---
title: "Midway through upgrade, computer locked up. Everything broken now."
date: 2008-07-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SomeGuyDude on 2008-07-03
Need help. Halfway through the upgrade process, the computer completely froze and required a hard reboot. Managed to recover somewhat, but now half of my packages aren't working and I can't use much of my software. I cannot find any way to easily "upgrade" again and would rather like to have all this fixed without a total reformatting. Help. I am insanely pissed off that the upgrade process couldn't finish without a complete and total lockup.

---

### Post by RAOF on 2008-07-03
```

sudo dpkg --configure -a

```
is a good start.  This should hopefully get you back to a state where the package management tools work normally.

If that doesn't work, we'll require some more information; like what exactly you've tried, and what the output of those trials have been.

---

### Post by Nullack on 2008-07-03
Thats what testing is for - its not fair to get upset,,,,,,,,,

Your issue may not even be repeatable - you probably dont have ECC ram it could have very well be a solar flare.

---

