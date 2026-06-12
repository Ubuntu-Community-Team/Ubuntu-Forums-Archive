---
title: "Possible to install or upgrade to Karmic with a non-default kernel?"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by t0mppa on 2009-12-11
Ok, I originally tried to install Karmic on my netbook, but [that didn't really work out]("http://ubuntuforums.org/showthread.php?t=1337154"), because it failed to boot the 2.6.31-14-generic kernel. UNR live session worked, install didn't. Pure Ubuntu didn't even work on a live session.

Today I installed Jaunty on it instead, which works without any problems. So, I was wondering if there's a way to upgrade to or do a clean install of Karmic with a kernel other than the default one given? Or should I just wait for Lucid instead before moving away from Jaunty, hoping that it works better?

---

### Post by lemming465 on 2009-12-12
If you do an upgrade, you will install the latest Karmic kernel rather than the default one, so your results might be better.  However, if that doesn't work, you have no easy way to downgrade short of reinstalling jaunty, so if you try it, be sure you have good backups and configuration notes before you take the plunge.  If your reinstall tolerance is low, waiting for Lucid might be a better option.  I'd start trying live Lucid CD's in a few months around alpha-4 or beta-1, and report any boot bugs in launchpad to increase the odds of a good final result.

---

### Post by t0mppa on 2009-12-13
No settings to lose, since it's a fresh install, so I guess I'll give upgrading a try. The only annoying part about re-installing is that since I didn't find an image for Jaunty UNR anymore, have to use the minimal CD image and download all the same files again on every install. The mini image installer also fails to install any boot loader on MBR for some reason, but since the Karmic installs earlier already put GRUB2 there, that isn't really a problem.

---

