---
title: "Ubuntu 10.10 always boots kernel 2.6.32.24-generic"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by mbobak on 2011-01-08
I just noticed I'm not running with the latest kernel.

This box was originally installed as Ubuntu 10.04, then upgraded to 10.10.

I just recently noticed that, even though kernel 2.6.35-24-generic is installed, this box seems to insist on booting up with 2.6.32-24-generic.

Looking at /boot/menu.lst, it looks ok.  (default is 0, and first kernel in list is 2.6.35-24.  2.5.32-24 is the *last* one in the list!)

Can anyone help me understand what's going on here?

-Mark

---

### Post by mbobak on 2011-01-09
I tried commenting out the 'hiddenmenu' directive in /boot/grub/menu.lst, but I still don't see a grub menu at boot time.  Seems like changes to menu.lst don't actually have any effect.

Has the way Ubuntu boots changed radically in 10.10?

-Mark

---

### Post by slooksterpsv on 2011-01-09
2 Things:

1. Before your computer tries to boot Linux, hold SHIFT until you get the Grub menu

2. After you modified /etc/default/grub - did you run update-grub afterwards to apply the changes you made?

---

### Post by mbobak on 2011-01-09
Thanks for the tip about holding shift.

This is resolved.  I upgraded to grub2, and the issue was resolved.

-Mark

---

