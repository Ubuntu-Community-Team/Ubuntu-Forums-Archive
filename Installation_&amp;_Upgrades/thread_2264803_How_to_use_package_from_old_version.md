---
title: "How to use package from old version?"
date: 2015-02-09
forum: Installation &amp; Upgrades
---

### Post by Tom_Peters on 2015-02-09
Hi,
I started using a XUbuntu workstation, "trusty" release 14.04, and am trying to compile an old but indispensible X11/Motif application written in C (XInvest) that I have been dragging along for decades.
It requires, among other things, the PrintShell extensions to Motif (Xm/Print.h).  These come in libmotif-dev and dependencies.
[http://packages.ubuntu.com/trusty/libmotif-dev](http://packages.ubuntu.com/trusty/libmotif-dev)
The Print.h from that package dates from 1996.  However the XInvest program uses some constructions that, interpreting from what I see on another system, were available in Lesstif from 2004.  But the lesstif2-dev package existed within Ubuntu up to "precise" but not in "trusty" anymore.
[http://packages.ubuntu.com/precise/lesstif2-dev](http://packages.ubuntu.com/precise/lesstif2-dev)

So how do I go about installing Lesstif on "trusty"?

It has been 10 years since I had a Linux workstation so I am not familiar with the do's and don'ts in modern package management with Ubuntu.

Thanx for any advise,
Tom

---

### Post by Tom_Peters on 2015-02-10
Hi,
I installed XUbuntu 14.04 "trusty".
Now for compiling some old X11/Motif C program I need the Motif libs as wel as the development header files.
Trusty offers libmotif-dev ([[COLOR=#dd4814]http://packages.ubuntu.com/trusty/libmotif-dev[/COLOR]]("http://packages.ubuntu.com/trusty/libmotif-dev")).  However the Xm/Print.h is very old (1996) and obsolete.
On my previous computer I used Lesstif, with a header file dating from 2004 that worked there.
But Lesstif is not in trusty.  It used to be in "precise" ([[COLOR=#dd4814]http://packages.ubuntu.com/precise/lesstif2-dev[/COLOR]]("http://packages.ubuntu.com/precise/lesstif2-dev")).

So my question:
Can I install packages from "precise" on my "trusty" system?
How? [http://ubuntuforums.org/showthread.php?t=2223607](http://ubuntuforums.org/showthread.php?t=2223607) suggests that it is difficult or impossible to downgrade a package to a previous version.
Also I foresee complications.  I suppose I'll have to remove libmotif - but that might force removing any application packages that depend on it.  But if I try install lesstif2-dev next to libmotif then it will overwrite the files (like Xm/Print.h) that are also in the libmotif packages.

---

### Post by bapoumba on 2015-02-10
I have merged your two threads. Have you had any success with the suggestion there ?
[https://answers.launchpad.net/ubuntu/+source/motif/+question/261920](https://answers.launchpad.net/ubuntu/+source/motif/+question/261920)

---

