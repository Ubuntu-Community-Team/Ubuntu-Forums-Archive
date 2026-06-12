---
title: "Downgrade installation from 11.10 to 11.04?"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by csete on 2012-01-04
I'm struggling with some known networking issues on 11.10 after an upgrade from 11.04 ([https://bugs.launchpad.net/linux/+bug/836250](https://bugs.launchpad.net/linux/+bug/836250)).  I'm interested in whether it is possible to downgrade from 11.10 to 11.04 without having to start over?  Unfortunately, I'm not sure why I didn't split my /home into a separate partition, so I would need to back that up... and of course get everything reinstalled.  It would be nice to back up to 11.04, although I'm guessing that isn't really possible.  Worth asking though.

Thanks,
Craig

---

### Post by tersogar on 2012-01-04
Clean install.

---

### Post by Mark Phelps on 2012-01-05
Unfortunately, unlike with MS Windows, Ubuntu doesn't provide the option to roll-back from a new Ubuntu install to the previous version.  You have to reinstall the old version from scratch.

To prevent this problem in the future, you should consider using Clonezilla to image off the current Ubuntu installation to an external drive.  Then, if the upgrade goes poorly, or you have problems afterward, or you just don't like the new version, you can restore the old "working" version in just a few minutes time.

---

### Post by csete on 2012-01-05
I think I already have a backup that I could revert to... unfortunately, I've changed enough things that that would be painful as well.  I think I will end up just sucking it up and waiting for the bugs to get fixed.

According to [http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2325](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2325) it sounds like this started in the 2.6 kernel line.  Is it possible to run Ubuntu 11.10 on top of a 2.6 kernel if I compiled it myself or are there dependencies that would be broken?

Thanks again,
Craig

---

