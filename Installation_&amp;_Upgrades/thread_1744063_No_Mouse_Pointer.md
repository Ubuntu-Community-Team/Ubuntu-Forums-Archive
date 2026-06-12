---
title: "No Mouse Pointer"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Krypto07 on 2011-04-30
I've looked around in the forum, but couldn't find anything related to my problem, so hopefully my post is a relevant one.

After upgrading to Ubuntu 11.04 from 10.10 yesterday, my mouse pointer is invisible, but otherwise working. Sometimes - depending on what opened window I move across - I can spot some random pixels where the pointer should be, so at first I thought it might be solvable by changing the pointer style - no luck!

Since it seems graphics related, I checked if my proprietary graphics driver - FGLRX-graphics driver for ATI/AMD - was activated, which it wasn't. This might be the problem, but trying to activate the driver caused a new problem. The driver gets downloaded, but can't be installed - in graphics mode the message says: "installArchives() failed".
Trying to install from the terminal gave a little more information: the driver depends on 'libqtcore4 (>=4:4.5.3)' and 'libqtgui4 (>=4:4.5.3)' but '4:4.7.2-0ubuntu6' is installed...

Anyone having an idea as to how I could solve this?

Regards
/Toby

---

### Post by VHans on 2011-05-01
I have the same problem and no wifi (IBM ThinkPad T42p)

---

