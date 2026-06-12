---
title: "Upgrading from 10.04 to 12.04 gives a lot of dependency problems"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by georgesgiralt on 2012-09-18
Hello !
I own a laptop which ran fine in the old LTS version for a while.
Yesterday I launched the upgrade from the running version (10.04.x I can't remember the x value) to 12.04.1 LTS.
During the install I had a lot of "package not installed dependency problems" pop-up messages.
Among the list are initramfs, initscripts, and some minor one like ffmpeg.
So I suspect my new system won't reboot.
Question :
What could I do to circumvent the problem BEFORE rebooting ? (and don't tell me a fresh install...)
Many thanks in advance for your help.

---

### Post by zvacet on 2012-09-25
```
sudo dpkg --configure -a
```

or

```
apt-get -f install
```

---

### Post by Frogs Hair on 2012-09-25
If you have any PPAS from 10.04 they may not be compatible.

---

