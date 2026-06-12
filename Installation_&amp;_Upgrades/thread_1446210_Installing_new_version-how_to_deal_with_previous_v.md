---
title: "Installing new version-how to deal with previous version?"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by Paulgirardin on 2010-04-03
I have Karmic installed in its own partition,with a separate Home partition.

Should I delete the contents of the Karmic partition prior to installing Lucid.
Or will the installer deal with this automatically?

---

### Post by Naitsirhc Hsem on 2010-04-03
you have 2 options:

Upgrade via update manager which will update all of the debian packages, bringing you up to date with the newest version

OR

do a clean install, The installer should give you the option to reformat the entire drive.  I don't know how all of the application data in your home directory will do because of the version upgrade.  the applications such as firefox or chrome save temp data to hidden files in your home directory.  updating could cause conflicts or delete data.

For your situation I would recommend updating via the update manager.  That should preserve most of your preferences and applications.  I have done this many times before so if you have any questions please post them here.

Good Luck

---

### Post by Paulgirardin on 2010-04-03
Thanks.
I take it that you had few problems using the update option.

---

### Post by Naitsirhc Hsem on 2010-04-03
I only had problems when I upgraded in a restricted proxy environment.  in a normal environment it should upgrade fine.  something that I learned from messing with many distros and windows is that before you do anything major, backup backup backup!:p

---

### Post by quadproc on 2010-04-03
> **Paulgirardin said:**
> Thanks.
I take it that you had few problems using the update option.
I am not the previous poster but I have had some troubles when updating from one Ubuntu version to another.  Going from 8.10 to 9.04 was particularly difficult but 9.04 -> 9.10 was much better.

In my case, it seems that the ATI graphics driver is the main culprit.  Apparently, to be safe about things, you need to uninstall the ATI fglrx driver before you do the upgrade.  After the upgrade then you can reinstall the driver and things seem to be OK.  In my case I did not uninstall the driver first and this system started up with some X sever errors and used "low graphics mode".  Fortunately, the driver uninstall/reinstall seems to be all that was needed on the 9.04 to 9.10 upgrade.

quadproc

---

### Post by Naitsirhc Hsem on 2010-04-03
It all depends on your card, I was fine with a radeon 5770 and up to date drivers when I went from 9.10 to 10.04 beta 1

---

