---
title: "sudo apt-get"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by rob_b on 2008-04-11
Hi guys,
I am used to compile almost everything I put on my machine therefore I know exactly where every file goes.
What happens with apt-get? where are the files stored? is there a standard?
Thanks

---

### Post by David Robertson on 2008-04-11
Yeap,

You can check out: man apt-get

The thing installs packages, generally precompiled plus scripts to touch up. Once you have installed a package you can ask about the packages properties, this will include all the files it has dumped onto your system. Easy to see through the GUI once installed.

All the apt-get GUI stuff also works through a shell if you wish to be traditional..

The best thing about apt-get is it maintains a dependency database. It will pull in anything else required to run your package.

What's available is held in the repositories (mirrors elsewhere).

Useful for me:
apt-get update
   Reload the latest repositories and updates my dependency database
apt-get upgrade
  Download and install latest versions of whatever you have installed.

You can still download and compile, but apt-get won't know what you have changed - you get to sort out your own conflicts.

---

### Post by rob_b on 2008-04-11
Thanks David for your answer.
but where in the file system will apt-get drop the files it downloads

---

### Post by kellemes on 2008-04-11
/var/cache/apt/archives/

---

