---
title: "clone package set from current to new release"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2011-05-19
I have a laptop running Ubuntu 10.04. I have a ton of installed packages -- some from synaptic, some from Software Center, some from downloaded *.deb files. I want to update to Ubuntu 11.04 by clean install.

After I spin the installer and run the initial update, what is the most effective way to make sure that my new install has all of my favorite packages?

I know that I can use **--get-selections** and **--set-selections** from dpkg. I'm worried that the package list from the older(10.04) release will confuse things when I apply them to the new (11.04) release.

Thanks in advance,
~~~ 0;-Dan

---

### Post by jerrrys on 2011-05-20
> **SaintDanBert said:**
> I'm worried that the package list from the older(10.04) release will confuse things when I apply them to the new (11.04) release.

i have done this; any packages that cannot be loaded in 11o4 should just error out

as for how

[http://www.ubuntugeek.com/backup-installed-packages-on-ubuntu.html](http://www.ubuntugeek.com/backup-installed-packages-on-ubuntu.html)
[http://ubuntuforums.org/showthread.php?t=819396&page=6](http://ubuntuforums.org/showthread.php?t=819396&page=6)
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)
[http://www.unixtutorial.org/2008/09/list-installed-packages-on-your-ubuntu-linux/#more-80](http://www.unixtutorial.org/2008/09/list-installed-packages-on-your-ubuntu-linux/#more-80)
[http://ubuntuforums.org/showthread.php?t=201524](http://ubuntuforums.org/showthread.php?t=201524)
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

