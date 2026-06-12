---
title: "How do I back up and restore settings &amp; configurations after a fresh install?"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by Elludium_Q-36 on 2011-05-03
I made the mistake of adding, from a CD, 10.04 packages to an 8.04 system.  So, as far as I know, I need to do a fresh install of 8.04 if I want any hope of keeping my settings & configurations.  Only then, as far as I know, can I use an alt CD with the cdromupgrade script.  Again, this is to keep my settings & configurations.

How do I back them up and restore them?

I have backed up the /home/ and /etc/ directories.

Of course, in /etc/ are the sources and sources.d files.

I also backed up my keys:
```
sudo apt-key exportall > /media/disk/Kubuntu2/repositories.key
```

I have installed debconf-utils since I have read elsewhere that using debconf-get-selections can back up some settings & configurations.  However, typing debconf-get-selections --help is of no use nor does typing debconf-utils --help or debconf --help yield much useful info...

Could someone with actual hands on, useful info please offer some pertinent assistance please?

---

