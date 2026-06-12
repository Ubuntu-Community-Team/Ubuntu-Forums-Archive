---
title: "how to gdm stop lucid"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by turbos4 on 2010-05-01
I have installed Ubuntu 10.04 lucid.

I'm trying to install nvidia drivers from nvidia.com. And I need to stop gdm and use text interface.
When I try

#sudo /etc/init.d/gdm stop

It turn off gdm, but i can't get to login.

Someone know how to?

---

### Post by NoxDeleo on 2010-05-04
This had me stumped/slightly worried too :)

In case you haven't already figured it out:
[http://ubuntuforums.org/showthread.php?t=127861](http://ubuntuforums.org/showthread.php?t=127861)

Also, here's a couple of useful threads to do with nvidia driver installs on Ubuntu:

If you were tired of your graphics getting trashed after kernel updates: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573) (should work fine for 10.04 but I haven't had chance to make sure yet).

If (as I did) you encounter an installation error along the lines of "ERROR: Unable to load the kernel module ‘nvidia.ko’...": [http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074)

That last one unfortunately didn't fix the problem for me, but it seems to have done it for some, so i'm linking it anyway.

Good luck!

---

