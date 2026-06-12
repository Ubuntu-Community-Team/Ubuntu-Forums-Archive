---
title: "Upgrading Empathy in Lucid?"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by varanasi on 2010-10-20
When will an updated version of Empathy be available for Lucid?  Or is there an easy way to install the Meerkat version?

I intend to continue using Lucid for a couple years, but the version of Empathy available in Lucid has some issues with logging chats -- there's no way to disable chats from being logged and there's no easy way to delete chat logs.  The current version allows one to disable logging but it's not available in Lucid, only Meerkat.

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/664460](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/664460)

---

### Post by lemming465 on 2010-10-21
You could try downloading the Meerkat package and running *sudo dpkg -i* against it.  That probably will fail due to changes in dependencies.  Next easiest option: download the Meerkat *source* package, install the *build-essentials* and *dpkg-dev* metapackages, and then try *dpkg-buildpackage -b -us -uc -rfakeroot* in the unpacked source directory, followed by *sudo dpkg -i* on the binary package one level up.
The fanciest option is to add some Meerkat repositories at lower pin priorities than your Lucid ones, then change the priority of just the Empathy package and its dependencies.

---

### Post by varanasi on 2010-10-21
Thanks for the ideas.  I've never thought of doing something like the last one.  Is there more info on it somewhere?

---

### Post by lemming465 on 2010-10-22
There is a [Pinning Howto]("https://help.ubuntu.com/community/PinningHowto") that can help get you started.

---

