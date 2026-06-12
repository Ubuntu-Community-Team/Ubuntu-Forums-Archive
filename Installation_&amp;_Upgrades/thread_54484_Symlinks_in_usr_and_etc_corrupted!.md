---
title: "Symlinks in /usr and /etc corrupted!"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by __jw on 2005-08-04
Today, the power went out in my apartment, so my Ubuntu (which had been working fine), got abruptly shut down.  After the power came back on, I turned my computer back on, and when Ubuntu began to boot, I got a TON of errors, the first of which being that /etc/init.d/rcS cannot be executed.

So, I boot into safe mode, and look around.  This is terrible.  Nearly every single symlink in /usr and /etc is nothing but gobbledegook!  Example:

# ls -l /etc/init.d/

...

rcS -> -uqr-s`il/pmt-tap

...

No wonder it can't run that crap!

Now what the heck has happened here?  Does an abrupt shutdown really ruin Linux/Debian/Ubuntu this much?  Talk about instability ... I don't want to have to reinstall my OS every time the power goes out (which seems to be quite often around here).

Help me at least understand the problem!

---

### Post by __jw on 2005-08-04
Here's something else funny ... apparently /usr/bin is no longer a folder ... it's an executable now!  Now THAT'S what you call bin!

---

### Post by tomchuk on 2005-08-05
What filesystem?

---

