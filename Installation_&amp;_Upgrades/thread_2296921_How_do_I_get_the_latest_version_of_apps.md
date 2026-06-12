---
title: "How do I get the latest version of apps?"
date: 2015-09-29
forum: Installation &amp; Upgrades
---

### Post by dr01tspc on 2015-09-29
I wanted certain features in gparted (HFS+ creation) that I understand to be in the later versions of gparted. 

The version installed in ubuntu 14.04 is/was 0.19 . . .  While the latest version is 0.23 . . ..

That was one of the reasons I upgraded from 14.04 to 15.04 (via 14.10, to upgrade in place). 

But when I went to get gparted for 15.04, the ubuntu software center provided 0.19 . . . again.

Is there a reliable way to get the newest (or newer) versions such software?

---

### Post by oldos2er on 2015-09-29
I think the easiest way to get the latest version of gparted would be to go to [http://gparted.org/livecd.php](http://gparted.org/livecd.php), download the *.iso you want and burn it to a CD, DVD or USB, as you prefer; then boot from your gparted live medium.

---

### Post by ian-weisser on 2015-09-29
> **dr01tspc said:**
> That was one of the reasons I upgraded from 14.04 to 15.04 (via 14.10, to upgrade in place). 

You can easily check before upgrading at [http://packages.ubuntu.com...or](http://packages.ubuntu.com...or) using shell.

Here is what is currently in Ubuntu.
```
$ rmadison gparted
 gparted | 0.11.0-2          | precise          | source, amd64, armel, armhf, i386, powerpc
 gparted | 0.11.0-2ubuntu0.1 | precise-security | source, amd64, armel, armhf, i386, powerpc
 gparted | 0.11.0-2ubuntu0.1 | precise-updates  | source, amd64, armel, armhf, i386, powerpc
 gparted | 0.18.0-1          | trusty           | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 gparted | 0.19.0-2          | vivid            | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 gparted | 0.19.0-3build1    | wily             | source, amd64, arm64, armhf, i386, powerpc, ppc64el
```

And here is what is currently in Debian:
```
$ rmadison -u debian gparted
 gparted | 0.7.0-1     | squeeze         | source, amd64, armel, i386, ia64, kfreebsd-amd64, kfreebsd-i386, mips, mipsel, powerpc, s390, sparc
 gparted | 0.12.1-2    | wheezy          | source, armel, armhf, i386, ia64, kfreebsd-amd64, kfreebsd-i386, mips, mipsel, powerpc, s390, s390x, sparc
 gparted | 0.12.1-2+b1 | wheezy          | amd64
 gparted | 0.19.0-2    | jessie-kfreebsd | source, kfreebsd-amd64, kfreebsd-i386
 gparted | 0.19.0-2    | jessie          | source, amd64, arm64, armel, armhf, i386, mips, mipsel, powerpc, ppc64el, s390x
 gparted | 0.19.0-3    | stretch         | source
 gparted | 0.19.0-3    | sid             | source, kfreebsd-amd64, kfreebsd-i386, mips64el
 gparted | 0.19.0-3+b2 | stretch         | amd64, arm64, armel, armhf, i386, mips, mipsel, powerpc, ppc64el, s390x
 gparted | 0.19.0-3+b2 | sid             | amd64, arm64, armel, armhf, hurd-i386, i386, mips, mipsel, powerpc, ppc64el, s390x
```



> **dr01tspc said:**
> Is there a reliable way to get the newest (or newer) versions such software?

Debian relies upon community volunteers (not upstream developers nor paid staff) to package and test software. You can see above that nobody has bothered to package gparted since 0.19.0, released 11 June 2014. Most packages in Debian sync to Ubuntu every six months.

So you can get the latest gparted by compiling it yourself, or by packaging it for Debian, or by helping volunteer Debian packagers and maintainers.

If your organization has a mission-critical need for a package, it may be sensible to employ the packager/maintainer directly. Canonical, for example, does this for several packages it considers critical to Ubuntu's quality.

---

