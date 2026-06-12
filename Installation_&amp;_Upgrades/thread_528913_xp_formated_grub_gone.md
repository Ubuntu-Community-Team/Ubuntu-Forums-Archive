---
title: "xp formated grub gone?"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by lazysloth on 2007-08-18
i just reformated my xp and now i cant boot ubuntu because grub doesnt show up so i can select ubuntu.
i heard that xp overrides grub or something like that why you want to install xp then grub..
is there a way to restore grub>?
also i dont have a live cd... i used wubi.

---

### Post by forestpixie on 2007-08-18
should be able to get your grub back with supergrub -

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

download and burn as a live cd apparently - never used it myself though.

---

### Post by Scunizi on 2007-08-18
Boot from a live CD and then go to the terminal.

Now type "sudo grub"
You'll get a grub prompt.

Type "find /boot/grub/stage1"
this will list boot partitions like (hd0,1) and/or (hd0,3)

Pick the first one and type "root (hd0,1)"
Now type "setup (hd0)

It'll buzz and whur a short time then say "succeeded".   Then later "Done".  Now you'll be back at the grub prompt.

Type "quit" then reboot without the live cd.

This was taken from [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

