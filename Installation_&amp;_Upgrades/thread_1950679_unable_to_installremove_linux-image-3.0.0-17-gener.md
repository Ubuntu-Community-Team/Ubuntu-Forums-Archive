---
title: "unable to install/remove linux-image-3.0.0-17-generic"
date: 2012-04-01
forum: Installation &amp; Upgrades
---

### Post by cw1035 on 2012-04-01
After running update manager today I had several errors. The cause seems to be a broken installation of linux-image-3.0.0-17-generic. Synaptic can't fix the broken package (attachment). Both "apt-get -f remove" and "apt-get -f install" fail (attached). I have also tried apt-get check, clean, autoclean, autoremove, update, & upgrade without any success. I am running Ubuntu 11.10 3.0.0-16-generic on a 64 bit quad processor. Any help will be greatly appreciated.
Craig

---

### Post by qunungnauraq on 2012-04-07
I'm having the same problem with ubuntu 11.10 64 bit gnome shell on a 2008 mac pro.

---

### Post by cw1035 on 2012-04-11
:pSorry for the late reply, but it took me a while to verify that the problem had been solved. I followed the advice at this link: [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure]("https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure"). The results of this advice is posted at this link: [https://answers.launchpad.net/ubuntu/+source/apt/+question/192359]("https://answers.launchpad.net/ubuntu/+source/apt/+question/192359"). Don't know exactly at what step the package was cleared, but it is gone now.
I eventually tracked down the source of the problem to a broken "perl" link at /usr/bin/perl. Hope this helps.
Craig

---

