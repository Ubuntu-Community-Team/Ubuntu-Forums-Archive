---
title: "I nuked my Karmic!"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by chrismine on 2009-10-26
:redface: I was playing with Virtualbox installing Mythbuntu and Windows 7 in virtual machines, the PC froze I reset some message about fsck showed up and I decided to run fsck from the recovery console - bad things started to happen - lot's of errors. I booted with Live CD and found the filesystem to be corrupt.

Reloaded Jaunty from CD and now eagerly awaits Karmic release date so I can install again.

Will then wait for Lucid's toolchain to be uploded and start apt-getting again!

---

### Post by philinux on 2009-10-26
> **chrismine said:**
> :redface: I was playing with Virtualbox installing Mythbuntu and Windows 7 in virtual machines, the PC froze I reset some message about fsck showed up and I decided to run fsck from the recovery console - bad things started to happen - lot's of errors. I booted with Live CD and found the filesystem to be corrupt.

Reloaded Jaunty from CD and now eagerly awaits Karmic release date so I can install again.

Will then wait for Lucid's toolchain to be uploded and start apt-getting again!

Just run ```
fsck /dev/sdawhatever -vy
``` And let it fix them.

From livecd or from reboot to the shell it would drop you to if fsck finds errors

---

### Post by chrismine on 2009-10-26
Thanks for that - I'll make a note for the future. It happened late at night so I decided to install Jaunty so long - cannot live without my Ubuntu.

---

