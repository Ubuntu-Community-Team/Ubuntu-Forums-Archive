---
title: "How to uninstall build-depend packages ?"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by bob23450 on 2008-07-07
Hi,
I installed a lot of build-depend packages in order to install from source some applications and now my system is bloated of packages I no longer need! I wonder :confused: how can I safely *auto*remove such things with no harm to the system.
Regards

---

### Post by sdennie on 2008-07-07
You can get list of all the -dev packages with something like this:

```

dpkg -l | grep '\-dev' | cut -f3 -d" "

```

However, when I ran the following to test the list:

```

sudo apt-get remove -s `dpkg -l | grep '\-dev' | cut -f3 -d" "`

```

It wanted to remove several meta-packages that I'd prefer it wouldn't.  You could always run that command (without the -s), note the packages that don't end in "-dev" and then reinstall them after you've uninstalled all the -dev packages.  Be sure you understand what you are removing before you remove it though.

---

### Post by bob23450 on 2008-07-08
Thank you vor, I tried the dry-run command but I noticed that it would have left the system... half naked! I searched for a less drastic solution and I found the command 'deborphan'. It tries to guess (!) which packages (mostly libraries) are likely not needed. I tried the following (repeat while more packages are removed):
```

sudo apt-get remove `deborphan --guess-dev`
sudo apt-get autoremove

```
It removed most of the -dev packages and their dependent (+ some libs), but left in place about ten of them, maybe the ones that would pull out half the world.
Since the heuristic nature of that command, your recommendations should be followed anyway.

In summary, it seems there is no way to determine exactly which packages were installed to satisfy the build dependencies (other than taking note of them when they were installed!).

---

