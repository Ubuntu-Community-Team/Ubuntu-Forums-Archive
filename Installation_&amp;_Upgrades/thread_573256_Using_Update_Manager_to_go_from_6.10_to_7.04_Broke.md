---
title: "Using Update Manager to go from 6.10 to 7.04 Broke my System!!!"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by RChickenMan on 2007-10-11
Hey guys,

I've been using Ubuntu for over a year now as my primary OS (no windows partition to speak of).  I decided I may as well check out 7.10, as I'm back in the days of 6.10.  I wanted to do an incremental upgrade (since this is the only officially supported method) so I used the Update Manager to upgrade the distro from version 6.10 to 7.04.  It got almost all the way through, to the "cleaning up" phase, and then the damn thing froze.  I let it sit overnight, but alas, in the morning, the entire system was forzen (including the ability to alt+ctrl+fX into a console)!  So I had to force it to reboot, and lo and behold, my system won't boot...

First of all, it messed up which partition is supposed to be root in GRUB.  I had no problems correcting this.  I booted it up without the splash screen, and at some point (around when it loads the cdrom driver) it just freezes.  I let it sit for a while, and it drops me into some kind of emergency terminal (something about a ramfs?).

Has anyone had a similar problem, or is otherwise able to help me out?  I'm an undergrad engineering student, so being without my computer is kind of a big deal!


**PS:  I have already begun the process of getting ready to wipe out the partition and install Gutsy from scratch.  I have posted a thread in the Gutsy forum due to the headache I'm having with the live CD.  I'm only somewhat into the internet forum culture, so I hope this doesn't count as "cross posting"!!!

---

### Post by cmnorton on 2007-10-11
This is interesting. After getting some help in these forums concerning having the 6.06 --> 6.10 update hang, that eventual upgrade and the following 7.04 upgrade all worked well. Then the upgrade to Feisty left my system in a kind of shake and bake mode, with hal errors, clicking grun icons literally freezing the system. The only thing I found and a question for which I could find no answer is the modules.conf seemed to be loading modules from different versions of the kernel.

In the end, I backed everything up, and did a clean install of Feisty.

---

