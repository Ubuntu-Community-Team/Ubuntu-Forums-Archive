---
title: "Safe way to increase size of a WUBI installation?"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by hyperation on 2011-02-27
Hello,

Recently, I installed Ubuntu 10.10 with WUBI.  I didn't have much free space on my hard drive then, so I only allocated 6 GB for it.  Now, my virtual disk (I think that's what it is called, I'm new with Linux) is running low on space.  I was wondering if there is a quick and safe way to bump the 5 GB to maybe 10 GB or something?

I read that there is the [LVPM]("https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?"), but it says it does not work for 10.04 (which I guess won't work for 10.10 either).

P.S. There isn't much stuff on it, just some Ruby on Rails, so no customization at all.

Thanks
:)

---

### Post by bcbc on 2011-02-27
If there's not much on it, it's easiest to reinstall and allocate a bigger virtual disk (backup all data beforehand as reinstalling will wipe the old virtual disk).

There is a resize script here (this is similar to LVPM but avoids the dependency problem LVPM has which can uninstall grub2): [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

Note that it's not a resize - it creates a new, larger virtual disk and then copies the old one over. (Which means that you need more space to do it than if you just reinstalled).
It's safe because it doesn't modify your current virtual disk - and you can make sure the new one works before getting rid of the old one.

---

