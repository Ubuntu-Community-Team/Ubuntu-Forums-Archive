---
title: "Compiling kernel 2.6.14.3"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by Catch-me-if-you-Can on 2005-12-05
Can someone give me a full list of steps so I can compile kernel 2.6.14.3 ?
I've been googling for a lot of time but I didn't find anything clear... I've had lots of kernel-panics before... I've been using Ubuntu for 4 days only (Ubuntu 5.10)

Any and every help will be appeciated.
Thanks.

---

### Post by xxMEL0Nxx on 2005-12-05
[http://www.ubuntuforums.org/showthread.php?t=85064&highlight=kernel+newbies](http://www.ubuntuforums.org/showthread.php?t=85064&highlight=kernel+newbies)

---

### Post by kentborg on 2005-12-07
I can get 2.4.16.3 to compile, and everything seems to be ok, but for one: the CD-ROM isn't found.

For a .config file I started with /boot/config-2.6.12-10-686, and for all the make oldconfig questions I took the default answers.

I later tried a build where I turned on BLK_DEV_IDEPNP, because it seemed related and maybe could help.  It didn't help.

Looking in /var/log/messages I only see the cheery "Dec  5 18:51:01 localhost kernel: [4294694.167000] Uniform CD-ROM driver Revision: 3.20"-message when I boot the stock kernel.

Suggestions?

Thanks,

-kb

---

