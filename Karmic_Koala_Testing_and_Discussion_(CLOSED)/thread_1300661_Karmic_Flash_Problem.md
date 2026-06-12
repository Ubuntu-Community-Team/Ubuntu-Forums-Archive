---
title: "Karmic Flash Problem"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Monotoko on 2009-10-25
Hiya Guys :)

Im having a flash problem in Karmic, i downloaded the "ubuntu-restricted-extras" package from the repos.

When i load a flash applet, it will load and work, the only problem is i cannot click anything.

Take the play button on youtube for example, it will change colour as it should when i hover over it, it will change colour again when ivv pressed it, so i know its getting the signals, it just will not recognise that it has been pressed...help?

---

### Post by RTrev on 2009-10-25
Same thing is happening here, on my desktop.  On my netbook, with the UNR netbook remix, it's not happening.  64-bit versus 32-bit might be the key?  Are you running 64-bit?

---

### Post by MelDJ on 2009-10-25
tried looking here for solutions? [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by RTrev on 2009-10-25
> **MelDJ said:**
> tried looking here for solutions? [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

Bingo!  In my case, for some reason, flashplugin-nonfree was not installed.  So when I hit the recommendation to remove and then reinstall it, it couldn't remove it.  Installing it fixed the problem.

Thank you!

---

