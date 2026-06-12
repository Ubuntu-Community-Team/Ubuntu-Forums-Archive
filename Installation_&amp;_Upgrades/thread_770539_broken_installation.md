---
title: "broken installation"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by joel@parke.ods.org on 2008-04-27
Hi all,

Thanks for the help!  I have upgraded from 7.04 yesterday and the good news is that the desktop is up.  The bad news is that I have a  dpkg dependency problem that I can't solve.  I am too new!

Problem root message:
2008-04-27 01:16:23,151 INFO cache.commit()
2008-04-27 01:33:09,466 ERROR got an error from dpkg for pkg: '/var/cache/apt/archives/xulrunner-1.9_1.9~b5+nobinonly-0ubuntu3_amd64.deb': 'conflicting packages - not installing xulrunner-1.9
'
2008-04-27 01:33:09,466 DEBUG running apport_pkgfailure() xulrunner-1.9: conflicting packages - not installing xulrunner-1.9

**Now attempted installation using Synaptic Package Manager shows:**
xulrunner-1.9 conflicts with j2re1.4 

I have attempted to remove j2re1.4 which is j2se/1.4 in all the ways I can think of, but I don't know much - so any help would be greatly appreciated! :)

Thanks,
Joel Parke

---

### Post by joel@parke.ods.org on 2008-04-27
I should have labeled this an an upgrade - sorry!
Please help - how do I remove this dependency problem?
Thanks,
Joel

---

### Post by Martin Witte on 2008-04-27
> **joel@parke.ods.org said:**
> I have attempted to remove j2re1.4 which is j2se/1.4 in all the ways I can think of

did you try ```
sudo apt-get remove --purge j2re1.4
```

---

### Post by joel@parke.ods.org on 2008-04-27
> **Martin Witte said:**
> did you try ```
sudo apt-get remove --purge j2re1.4
```

I just tried that - thanks so much for the suggestion, but now it says:
Package j2re1.4 is not installed, so not removed

So this is catch 22 - any other ideas?

Thanks,
Joel

---

### Post by joel@parke.ods.org on 2008-04-27
I looked around a bit more and found that the v1.9 update of xulrunner was changed in part because of a conflict with j2re1.4 which was in a plugin - so perhaps there is a plugin (not the mozilla-plugin) that I need to remove?  How do I do that and is this the right direction?

Thanks,
Joel

---

### Post by joel@parke.ods.org on 2008-04-27
Hi all,

I was able to finally remove this package by finally doing dpkg -P j2re1.4 which worked and I am now functional again.

Thanks for all the help.

Note -I did have one thought!  Could the upgrade task, test to see if these sorts of conflicts exist before the upgrade.  This would be much easier on the nerves -- thanks.
Joel

---

