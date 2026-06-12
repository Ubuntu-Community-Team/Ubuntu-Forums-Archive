---
title: "Non System Disk Error"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by Hoofinasia on 2008-01-03
Upon installing Xubuntu alt (successfully) on a dedicated machine (as in, no windows or dual boots in sight) I reboot, then receive an error saying "non-system or disk error, replace and strike any key.." etc. I have tried multiple file system formats, auto and manual. And yes, I took the CD out of the drive, smartypants.

 I've bugged my "linux guidance counselor" ( my current CS professor) I've bugged other forums (and yes, I did multiple searches, and read most of the beginner stuff) but nobody has helped me so far.  I've come to the point that I realize I should just get it over with and post on these forums.

Other distros I've tried, with varying degrees of failure: Xubuntu, Ubunutu, Ubuntu alt, Ubuntu Server.
I really just want *some*thing to work.

So here I am.  The linux-based CLI drives me crazy, since I'm completely inexperienced. But the real issue is *getting *to the command line.  I've heard terrible things about the initial learning curve (nay-sayers need not apply), but this installation trouble is unexpected.  I know for a fact that I meet the min reqs for any of the above installs.  So, where do I start?

FYI:  out of town for a week, so I can't reply until the 18th.  Hopefully this thread doesn't sit fallow like the one over at linuxforums.org

---

### Post by torgrot on 2008-01-03
First thing I would try is getting Gparted and burn it to a CD.  Then boot of of it, and have a look at the Hard disk.  See if there is a file system there.

torgrot

---

### Post by pietjanjaap on 2008-01-03
non-system or disk error, replace and strike any key

This means that de pc does not find a operating system or cd where he can boot from.

You have choosen the wrong harddisk to boot from, check your bios.
Or your harddisk is not made bootable , check with gparted bootcd,
Or no grub installed, reinstall with supergrub (bootable cd)

---

