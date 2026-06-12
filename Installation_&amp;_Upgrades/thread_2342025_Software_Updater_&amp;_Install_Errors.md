---
title: "Software Updater &amp; Install Errors"
date: 2016-11-03
forum: Installation &amp; Upgrades
---

### Post by ray42 on 2016-11-03
When using the software updater I get the following error.

[https://1drv.ms/i/s!Al9fZuCczxxShDiedUvzj_e_s_Bi](https://1drv.ms/i/s!Al9fZuCczxxShDiedUvzj_e_s_Bi)

It has happened so far on a flash, openjdk-8 policy tool updates. Also when using terminal to install: "[COLOR=#000000]*sudo apt-get install gconf-cleaner". This install failed with error *[/COLOR]E: Unable to locate package gconf-cleaner

---

### Post by howefield on 2016-11-03
> **ray42 said:**
> [https://1drv.ms/i/s!Al9fZuCczxxShDiedUvzj_e_s_Bi](https://1drv.ms/i/s!Al9fZuCczxxShDiedUvzj_e_s_Bi)

Best to use the paperclip icon to attached images to your post rather than send people to a third party site.

> It has happened so far on a flash, openjdk-8 policy tool updates. Also when using terminal to install: "*sudo apt-get install gconf-cleaner". This install failed with error *E: Unable to locate package gconf-cleaner

This means as the error said, there is no package called gconf-cleaner known to your system, either because the repositories need updating or there really is no package by that name.

What is the output of the terminal commands..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

and

```
cat /etc/*-release
```

---

### Post by ian-weisser on 2016-11-03
Terminal output can simply be copy/pasted, too. It's text.

Anyway, that's a warning, not an error. Your unattended-upgrades settings changed during your last release-upgrade.
The old settings are preserved in that file.
If you prefer the new settings, delete the old file.
If you prefer the old settings, restore the old file.
If you don't know, then leave it alone and live with the warning for a few months until you have a preference

---

### Post by ray42 on 2016-11-03
```
$ egrep -v '^#|^ *$' /etc/apt/sources.list
/etc/apt/sources.list.d/*/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial-security main restricted
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial-security universe
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial-security multiverse
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial-backports multiverse restricted universe main
/etc/apt/sources.list.d/opera-stable.list:deb https://deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/opera-stable.list.save:deb https://deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases)

```

```
$ cat /etc/*-releaseDISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
NAME="Ubuntu"
VERSION="16.04.1 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.1 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial

```

---

### Post by howefield on 2016-11-10
Please don't pm for support, keep it all in the thread.

You've had the answer to your query, what do you need clarifying ?

---

### Post by ray42 on 2016-11-11
Yes you are correct. Sorry I was looking at the wrong post :oops:

Oh yes and thank you. I do want to one day do all this for myself where do I start in gaining this knowledge?

---

### Post by ian-weisser on 2016-11-11
The same way you learn everything else in life: One step at a time.

The easiest way to begin: Look for threads in this forum that interest you. Ask questions.

In this particular case, read the warning message again slowly and carefully, and you'll quickly begin to understand what it is trying to say.
The next question is 'why', which is not in the message at all. That I merely happen to learn while helping other people in this forum troubleshoot unattended-upgrade problems.

---

