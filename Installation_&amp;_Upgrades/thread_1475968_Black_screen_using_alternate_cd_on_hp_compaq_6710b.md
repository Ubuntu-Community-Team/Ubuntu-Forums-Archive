---
title: "Black screen using alternate cd on hp compaq 6710b (INTEL Mobile GM965/960)"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by tim__b on 2010-05-07
When trying to install Lucid on my HP Compaq 6710b (INTEL Mobile GM965/960 graphic controller) using the alternate i386cd with an usb pen i (re-)experiencing (known from the Jaunty installation) the following problem:[LIST]
[*]Boot from USB (works)
[*]Select language (works)
[*]Choose to install ubuntu (works)
[*]Removing quit from the boot options, hit enter, see some output (works)
[*]Starting the installation interface (fail)
[/LIST]The screen wents to black, but system seems not froozen. What i've tried to fix this issue:[LIST]
[*]fb=false as bootoption (worked in jaunty, does not work with lucid)
[*]frambuffer=false
[*]fb=off
[*]debian-installer/framebuffer=false
[*]vga=123, tried all of the offered modes
[*]vga=771 (get some screwed up output on the screen, which i guess from that the system/machine is not frozen)
[*]i915.modeset=1
[*]i915.modeset=0
[*]xforcevesa etc
[/LIST]Anyone managed to install Lucids with INTEL graphics + the alternate cd?

PS: I need the alternate cd to setup an encrypted system.
PPS: Just tested the desktop i386 image which works flawlessly.

---

### Post by oraerk on 2010-05-09
the same problem there with just the same HP 6710b. Also tried all this options and most of their combinations. No luck.

---

### Post by Catharsis on 2010-05-09
Try removing "splash" from the boot options.

---

### Post by tim__b on 2010-05-10
Catharsis, thanks for your help. Forgot to mention that I removed splash as well as quite without luck.

---

### Post by Catharsis on 2010-05-10
Have you tried booting into Recovery Mode? If "boot normally" doesn't work, you can try "failsafeX".

Also, don't know if it's pertinent, but since you mentioned encrypted drives:
[http://www.ubuntu.com/getubuntu/releasenotes/1004#Encrypted%20partitions%20must%20be%20listed%20in%20/etc/fstab](http://www.ubuntu.com/getubuntu/releasenotes/1004#Encrypted%20partitions%20must%20be%20listed%20in%20/etc/fstab)

---

### Post by user2037 on 2013-02-06
Ran into this as well, but it worked *before* installing a desktop environment. Strangely though it was blank until I pressed Ctrl + Alt + F1, F2, F3, etc. (F7?).

After desktop install the blank screen would not go away except when booting into recovery.

Apparently this may not be limited to Ubuntu: [http://www.linlap.com/hp-compaq_6710b](http://www.linlap.com/hp-compaq_6710b) . Though it is odd that the Desktop install works.

---

### Post by wildmanne39 on 2013-02-06
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

