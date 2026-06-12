---
title: "Upgrading interrupted and apt-get got broken, how to fix it?"
date: 2016-11-03
forum: Installation &amp; Upgrades
---

### Post by i2000s2 on 2016-11-03
> **ian-weisser said:**
> Boot from a LiveUSB.
Use the LiveUSB environment to back up your data to an external device (not to the LiveUSB, which is read-only).
Install 16.04 fresh from the LiveUSB.

A crash in the middle of an upgrade from one release to another is super difficult to recover from, and requires lots of skill and time.
It's generally not worthwhile to fix that kind of (very rare) failure, but to simply wipe and start over.

I got almost the same problem and screenshot as OP, and found the `**apt-get**` was simply broken (see details on [my AskUbuntu question]("http://askubuntu.com/questions/844967/upgrading-interrupted-and-apt-get-got-broken-how-to-fix-it")). Is there is any thought on fixing it? I can have a try.

If not, could you point out what part of data should I backup foremost? I don't have a big spare disk to store all my home and root directory while having a lot of software installed which I don't want to install them by hand one by one again if possible. If you have some tools to help ease the reinstallation process by backing up the minimal data, that would be nice!

Thanks!

---

### Post by ian-weisser on 2016-11-03
> **i2000s2 said:**
> I got almost the same problem and screenshot as OP, and found the `**apt-get**` was simply broken

'Almost the same problem' usually means an entirely different problem in this forum.
Please open a different thread so the Original Poster's problem doesn't get confused with your problem.

The amount of detail you have provided on your problem is inadequate. If you really want to fix the problem, we need to know the exact error message. Details matter.
Fixing your problem requires experience using a chroot and a good understanding of package management.
If you have those skills, and an internet connection, you can probably fix your system in an afternoon.
If you want us to guide you through a chroot (in a different thread), it will take several days, perhaps a week.

> **i2000s2 said:**
> If not, could you point out what part of data should I backup foremost? I don't have a big spare disk to store all my home and root directory while having a lot of software installed which I don't want to install them by hand one by one again if possible.
It is unwise to install all applications 'by hand one by one' in a Linux package management environment. Use the packages instead.
Not sure why you would want to back up your root directory...users with a lot in their root directory tend to misuse root, which is unwise.
We cannot assign a value to the data in your /home. It's yours. Only you can place a value on your documents, mail, browser bookmarks, etc.

---

### Post by howefield on 2016-11-03
Posts moved to own thread.

---

