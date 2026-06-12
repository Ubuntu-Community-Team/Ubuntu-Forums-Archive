---
title: "Marking packages to NOT auto-upgrade?"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by strm on 2007-06-08
Hi,
I use the command line apt-get manager over synaptic most of the time, and I have beryl version 0.2.0 installed since it is the more stable version, however 0.2.1 already exists in the universe and I dont want beryl packages to upgrade when I use "apt-get upgrade" command, how do I mark those packages to not auto-upgrade on that command?

ps. these are the packages I dont want to upgrade:
```
  beryl beryl-core beryl-manager beryl-plugins beryl-settings
  beryl-settings-bindings emerald emerald-themes libberyldecoration0
  libberylsettings0 libemeraldengine0
```

---

### Post by bapoumba on 2007-06-08
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html")
Look for the pin version in: 3.10 How to keep specific versions of packages installed (complex).

You can also lock a version from synaptic (> Package > Lock version).

---

### Post by strm on 2007-06-08
thanks for the reply, locking packages from synaptic did not work, however adding entries to /etc/apt/preferences solved the problem.

---

