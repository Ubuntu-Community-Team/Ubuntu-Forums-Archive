---
title: "Help me understand how the decision is made."
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by PadreSol on 2008-08-07
I am new to Ubuntu and still having trouble understanding how versions are selected for inclusion into a release.  For example Xorg has updates that seem important since Sept. 5 2007.  But apparently not important enough.  Does anyone know why this version was chosen?
I can't believe stability is the reason as this Xorg is marked a 
"This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way."




Xorg -version

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)

---

### Post by steveneddy on 2008-08-07
Ah, the beauty of a Linux LTS release.

---

### Post by tommcd on 2008-08-07
Ubuntu is based on Debian unstable (sid). When a new version of Ubuntu is under development a snapshot of Debian sid and all of it's packages are chosen as a starting base. New versions of programs are added during a development release, until a final freeze is made and bugs are worked out before the final release of the finished version of Ubuntu. 
As with Debian, packages can be held back if they are not deemed stable enough by the developers, or if they require updating too many other dependencies that may introduce instablility to the system.
Ubuntu aims for cutting edge development, although the LTS releases do aim a bit for for stability as Steveneddy said . Other distros like Debian and Slackware aim for stability, and forgo the latest and greatest until those packages are deemed stable enough.
In short, it is the devs philosophy and choices that determine this stuff.

---

### Post by PadreSol on 2008-08-07
I think some increased pro-activeness is what's needed. Xorg has some security fixes.  It seems that we're in a reactive model instead of pro-active.

---

### Post by cariboo on 2008-08-08
There is a new version of xorg coming in September for inclusion in Intrepid Ibex. The alpha 3 veriosn of intrepid is available, but is not really suitable for every day usage as there a lot of bugs.

Jim

---

