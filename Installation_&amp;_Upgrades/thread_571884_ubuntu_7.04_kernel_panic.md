---
title: "ubuntu 7.04 kernel panic"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by sidyom on 2007-10-09
hi
i had downloaded the 7.04 live cd a while back, and i have been trying to fix this problem for some time.
when i get to the live cd splash screen, i would just hit enter. it would take me to a blank screen and just hang there.
so i changed the boot command line to just read "boot: live"
and then it o/ps what is happening:

Kernel panic VFS: unable to sync vfs: unable to mount root at an uknown block (104,1)

or something along those lines.

what is happening? is there a problem with GRUB not pointing to my hdd?

thanks in advance

---

### Post by ryanVickers on 2007-10-09
Could you check the drive?  If there is a bad block that could be a problem, but maybe that's not what this is...

---

### Post by sidyom on 2007-10-09
im afraid i dont understand what you mean...
i've done a memtest,
and i'm using the drive right now for windows. freshly defragmented and error checked by windows.
but should i be getting that error just booting from a CD?

---

