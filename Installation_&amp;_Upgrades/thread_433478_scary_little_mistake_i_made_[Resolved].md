---
title: "scary little mistake i made [Resolved]"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by StormJosh on 2007-05-05
I made a scary little mistake. I know its fixable, somehow.

I installed 7.04 on my 2nd hard drive, which I completely formatted. On my first hard drive was my copy of Windows XP. Now, whenever I boot up my computer, it automatically boots up into Ubuntu.

I'm totally new to this, so is there anyone who knows of a guide that will show me to set up GRUB, or something similar, after the fact?

---

### Post by aysiu on 2007-05-05
Try this:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by StormJosh on 2007-05-05
Perfect solution. I now get a boot menu and everything. Thanks a lot for your help, I appreciate it.

A note to anyone attempting to use this solution as well, the first kernel/operating system is 1, not 0. So if you have 3 things listed, the 3rd item is actually number 3, not 2.

---

### Post by aysiu on 2007-05-05
Uh, no... that's actually not true.

The first is 0. The second is 1 and so forth.

You have to count any entry that starts with the word *title*. Trust me. I've done and seen this many times.

Glad it worked out for you, though.

---

