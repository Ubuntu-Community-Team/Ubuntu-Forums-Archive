---
title: "How to install libgcal from Karmic on Jaunty"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mukul_s on 2009-08-18
Hi,

I am running Kubuntu Jaunty.
I want to get the latest libgcal and akonadi-resource-googledata which are available in Karmic's repositories.
How can I safely install these packages on my jaunty?

Ref: [https://bugs.launchpad.net/ubuntu/+bug/380245](https://bugs.launchpad.net/ubuntu/+bug/380245)
Ref: [https://bugs.launchpad.net/ubuntu/+source/libgcal/+bug/411679](https://bugs.launchpad.net/ubuntu/+source/libgcal/+bug/411679)

---

### Post by mc4man on 2009-08-18
The best way would be to take karmic's source, apply the .diff and build a debian package on your jaunty.

While libgcal only has 3 dependencies, for 2 of them you'd need to upgrade to the karmic version number which in this case would be a poor idea. (**if trying to install the karmic package**
 Both of the libraries are of the type that typically get security updates and by updating to karmic versions you'll never receive any.

If you've built any packages before this build is extremely easy, only 2 build-deps for libgcal, (other than the basic build tool packages.

(( just did on hardy and had to make no changes at all to either my install or the control or rules file, took about 2 min.

Because it's so easy and clean, so to speak, you may find it showing up in a ppa sooner than later if you've no desire to build

---

### Post by mukul_s on 2009-08-18
What if I replace "jaunty" by "karmic" in my repos, reload the packages, select libgcal & akonadi-resource-googledata and install it??
Will this won't work?

---

### Post by mc4man on 2009-08-18
> What if I replace "jaunty" by "karmic" in my repos, reload the packages, select libgcal & akonadi-resource-googledata and install it??
Will this won't work? 

Well of course it would work and your free to do as you please. If you only installed those 2 apps and returned immediately to jaunty sources you'd limit the possible/probable damage now and later.

I think it's a very poor idea.

Here are the install depends and version, note that several in the 2nd group will require additional karmic packages, you'd be well advised to follow the dependency path first and see where it leads

> Package: libgcal0
Source: libgcal
Version: 0.9.2-1~ppa~lure1
Architecture: i386
Maintainer: Michael Banck <mbanck@debian.org>
Installed-Size: 116
Depends: libc6 (>= 2.4), libcurl3-gnutls (>= 7.16.2-1), libxml2 (>= 2.6.27)

> Package: akonadi-kde-resource-googledata
Source: akonadi-googledata
Version: 1.0-0ubuntu1~ppa~lure1
Architecture: i386
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Installed-Size: 480
Depends: kdebase-runtime (>= 4:4.3.0), kdelibs5 (>= 4:4.3.0), kdepimlibs5 (>= 4:4.3.0), libc6 (>= 2.1.3), libgcal0 (>= 0.9.2), libgcc1 (>= 1:4.1.1), libqt4-dbus (>= 4.5.1), libqt4-svg (>= 4.5.1), libqtcore4 (>= 4.5.1), libqtgui4 (>= 4.5.1), libstdc++6 (>= 4.1.1)

---

### Post by s1300045 on 2009-09-04
> **mc4man said:**
> The best way would be to take karmic's source, apply the .diff and build a debian package on your jaunty.


Would someone like to give some hints on that? I'd really love to learn more on compiling packages. I just don't know where to start!

---

### Post by lemming465 on 2009-09-06
I've got some [generic advice on building stuff from source]("https://mywebspace.wisc.edu/jeleinwe/web/BTS/"), but it doesn't really get into the issues with backports.

---

