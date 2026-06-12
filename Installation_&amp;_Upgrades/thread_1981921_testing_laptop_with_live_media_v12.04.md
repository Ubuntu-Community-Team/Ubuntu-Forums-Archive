---
title: "testing laptop with live media v12.04"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2012-05-17
I want to use the live boot media for Ubuntu v12.04 to test against features of my laptop.  It seems that I will need to add a group of packages to what is loaded by default.  Is there some way to get some persistence in my testing?

One approach would implement a persistent store (key drive or similar) to hold some scripting.  The scripting could then add the packages using command line apt-get after each boot.

Is there some other way to get packages to load during the use of the live media distro? Someone mentioned a tool that would let me tinker the contents of the ISO file.  I don't think that I'm not skilled enough to do that without breaking the distro.  If the tool let me tinker the distro saying, "I want package X, Y, Z ..." and the right things happen, that might work fine for my tests.

Thanks in advance,
~~~ 0;-Dan

---

### Post by kc1di on 2012-05-17
take a look at this page it may be of help to you.
[https://help.ubuntu.com/community/LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization")

---

### Post by SaintDanBert on 2012-05-18
KC1DI de  KI4MQ  QSL

That approach is the "some way to alter live media packages" that I spoke of in my original post.  I understand all of the instructions, but it seems a very heavy weight approach for what I'm trying to do.

Consider that I'm testing the various ways to suspend a laptop.
Reboot is a constant part of that testing. Before I know which
packages to make persistent, I likely will need to reboot several times. Otherwise, it is an effort to alter, make new media, reboot
... repeat.

73,
de KI4MQ
K

---

