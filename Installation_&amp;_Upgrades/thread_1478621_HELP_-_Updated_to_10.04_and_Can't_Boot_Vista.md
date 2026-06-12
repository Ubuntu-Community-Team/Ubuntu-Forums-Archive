---
title: "HELP - Updated to 10.04 and Can't Boot Vista"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by bluec10 on 2010-05-09
I've got a dual boot system with both Vista and Ubuntu.  After upgrading to 10.04 my Vista doesn't load anymore.  I select it in the Grub menu and the computer just hangs.

Are there any known fixes for this? Where do I start?  I'm an Ubuntu novice, but I'm an able computer fixer.

---

### Post by kansasnoob on 2010-05-09
We should see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It's very likely that it's this bug:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

If that is correct the fix is here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

But we can only be sure when we see the output requested.

---

