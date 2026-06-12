---
title: "aptitude cmd-line keeps back packages, while aptitude UI upgrades them"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by neel on 2007-06-06
Hi,

I am seeing a different behavior between aptitude command-line and aptitude UI when upgrading my system.

I have several Edgy server installations done via an 6.10-alternate-iso CD. When I go to upgrade the packages, on the command-line, I get:
sudo aptitude update
sudo aptitude upgrade
The following packages have been kept back:
  linux-image-generic
28 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded
and it does not get the latest kernel: linux-image-2.6.17-11-generic

I can subsequently say `sudo aptitude install linux-image-2.6.17-11-generic`, to get the latest kernel. And follow that up with another `sudo aptitude upgrade` to upgrade the linux-image-generic package as well.

Whereas, if I go into the aptitude UI and hit the following key-strokes:
u
U
g
g
I get all the 28 packages above, plus the new kernel linux-image-2.6.17-11-generic, plus the linux-image-generic is upgraded, all in one shot.

I am a newbie to Ubuntu, but would expect that the UI would eventually call the aptitude cmd-line behind the scenes. So, either I am missing something on the command-line, or this is an unusual behavior. Please let me know what's going wrong here.

Thanks.

-Neel

---

### Post by NeoLithium on 2007-06-06
```

sudo aptitude dist-upgrade

```
Will install the held back packages when you use the command line :)

---

### Post by neel on 2007-06-06
Agreed, but I am reading in many posts here that I shouldn't, normally, need to do a dist-upgrade. Not to mention, that the man page itself warns you against it.

Moreover, do you mean to say that from the UI if I do 'u U g g', that is equivalent to doing a dist-upgrade? That would be strange too...

-Neel

---

### Post by NeoLithium on 2007-06-06
I haven't had any issues with a dist-upgrade, but then again, I could be wrong about that. Come to think of it, does ```
 sudo aptitude -f upgrade
``` force the held back packages to be upgraded? Hmmm, food for thought. I usually just click on the update notifier...

---

