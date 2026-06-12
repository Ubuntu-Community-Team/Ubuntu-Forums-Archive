---
title: "Which PPA is broken?"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by bobpaul on 2010-09-02
I like PPAs. They're great. I have dozens I use. Sometimes they go down or even get deleted, and then I'm sad. Even worse, I can't figure out a straight forward way to know which one has gone down or been deleted. They all show up in *aptitude update*'s output as *"http://ppa.launchpad.net lucid/main Packages"*. For example:

```
~$ sudo aptitude update
[snip]...
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid-proposed/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-proposed/universe Sources
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Fetched 5,942B in 2s (2,692B/s)

```

I know one of my PPAs is gone, but not which one. I poked around in /var/log and couldn't find a log that elaborated on *aptitude update*'s errors. 

To fix it, I finally did the following:

```

~$ cd /etc/apt/sources.list.d/
/etc/apt/sources.list.d$ for i in *; do \
   sudo mv $i $i.disabled; \
   sudo aptitude update > /dev/null; \
   if [ $? -eq 0 ]; then \
      echo "$i is broken"; \
      break; \
   fi; \
   sudo mv $i.disabled $i; \
done

```

In a nutshell, this disables each PPA one by one and tries to update. When aptitude update finally succeeds (returns 0 on exit), the name of the broken sources.list file is printed to the screen. This works, but it doesn't seem like I should have to go to these lengths.

Is there any way to get aptitude to report more than "one of your many ppa.launchpad.net repo's is bad, see if you can guess which one?"

---

### Post by anystupidname1 on 2010-12-20
Thanks, I found this too:
[http://ubuntuforums.org/showthread.php?t=1594757](http://ubuntuforums.org/showthread.php?t=1594757)
or
[http://bazaar.launchpad.net/~davidc3/%2Bjunk/repostory/download/10/repostory-20101013102037-6h2vdberf2f0u2p7-1/repostory](http://bazaar.launchpad.net/~davidc3/%2Bjunk/repostory/download/10/repostory-20101013102037-6h2vdberf2f0u2p7-1/repostory)

---

