---
title: "3G USB Modem Issues"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by victor9098 on 2009-10-13
Hi All,

Some issues with my USB dongle have popped up on my Karmic Beta installation. Whenever I plug in (even if plugged in during boot up) I get the following error:

> Unable to mount Mobile_Connect
Error mounting: mount exited with exit code 32: mount: block device /dev/sr0 is write-protected, mounting read-only mount: /dev/sr0: can't read superblock

Is anyone else getting this or is there a fix? The dongle had been working fine up until the weekend then I just tried using today and this is what I keep getting. Sometime a slightly different error comes up but I have not had a chance to note the full text of it.

Any help would be great!

---

### Post by Sealbhach on 2009-10-13
I got that when I upgraded the kernel from 2.6.31-11 to 2.6.31-13. For the moment, I have gone back to 2.6.31-11 and locked the version in Synaptic. I don't see any bugs on Launchpad about this.

.

---

### Post by alexmurray on 2009-10-13
Probably related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

---

### Post by victor9098 on 2009-10-13
Added a comment to the bug report, let them know I am effected by this too.
Thanks for that

---

