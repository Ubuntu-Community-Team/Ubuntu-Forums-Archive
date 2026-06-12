---
title: "harddrive upgrading advice requested"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by godfree2 on 2008-08-08
I'm a long time Linux user, but I'm not keen to replace my stuffed older hard drive with a new one since UUID has been forced upon us.

Should I go to fstab and sdaX all effected areas then clone the partitions?
What works or what doesn't?

---

### Post by coffeecat on 2008-08-08
> **godfree2 said:**
> Should I go to fstab and sdaX all effected areas then clone the partitions?

That should do nicely. :wink: I've cloned Ubuntu before and as long as you get your sdx references correct, it all works as it should. Don't forget that you'll also have to edit menu.lst. There are some UUIDs lurking in there too - time for the pest control people I think.

Talking of which.... I'm afraid you won't be able to avoid UUIDs completely, not if you want that nice usplash screen rather than a load of scrolling text. Changing your swap partition UUID wrecks usplash. (Don't ask. :() Have a look at my post in [this thread]("http://ubuntuforums.org/showthread.php?t=857565") where I've posted some links and detailed the fix.

---

