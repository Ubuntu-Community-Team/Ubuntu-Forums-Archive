---
title: "2 distro's remove/replace 1"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by dontgetshocked on 2010-05-13
Can I safely remove 1 distro without screwing up the other?
I have Linuxmint as secondary and ubuntu as the last.I want to replace ubuntu.If I just delete the partitions/format and install my other os which is OpenSuse 10.03 will this work.will opensuse see linuxmint and make grub understand?

---

### Post by quixote on 2010-05-15
You can certainly reformat the ubuntu partition and put suse on it without affecting your linuxmint partition.  Make sure that partition is NOT ticked to be formatted, and it won't be.  

What it will do to your grub, I don't know.  I suspect you'll need to reinstall grub using  a Live CD and whatever method one of your two OSes uses.

---

