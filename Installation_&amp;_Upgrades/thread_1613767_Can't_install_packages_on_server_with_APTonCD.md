---
title: "Can't install packages on server with APTonCD"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by Innuendo108 on 2010-11-04
I have a PC, that has no internet connection at all, (let's call it SERVER) and I need to install some packages on it.

I've made a guest Debian system in virtualbox, downloaded needed packages and made a CD from them with APTonCD tool.

(First I want to try with no real server, but with virtual too).
I create guest Debian server system in VirtualBox with no Desktop Environment.

I typed:
```

mount cdrom # it mounted (I can see it)
apt-cdrom add

```

Then I try to install something:
aptitude install make build-essential
and I get this:
[[IMG]http://img5.imagebanana.com/img/s6unvn07/thumb/ServerRunningOracleVMVirtualBox_001.jpeg[/IMG]](http://www.imagebanana.com/view/s6unvn07/ServerRunningOracleVMVirtualBox_001.jpeg)
What is virtual package?
I thought APTonCD wrote all dependencies to CD-image too.

How can I fix this?

---

