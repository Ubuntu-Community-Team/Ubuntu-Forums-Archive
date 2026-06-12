---
title: "Installing irssi 1.4.5"
date: 2024-01-16
forum: Installation &amp; Upgrades
---

### Post by stevenxl on 2024-01-16
When I search for **irssi** using **apt search irssi**, I only see version 1.2.3 listed as an installation option.

However, I see under the **Noble** tag on this page ([https://launchpad.net/ubuntu/+source/irssi](https://launchpad.net/ubuntu/+source/irssi)) that **1.4.5 **exists.

How can I install version 1.4.5?

---

### Post by guiverc on 2024-01-16
Ubuntu is a *stable release* system, which in effect means software stays the same version it releases, with security fixes only back-ported to the *stable* release.

You've not provided any release, but I see

```

guiverc@d7050-next:~$   rmadison irssi
 irssi | 0.8.15-5ubuntu3   | trusty          | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 irssi | 0.8.15-5ubuntu3.6 | trusty-security | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 irssi | 0.8.15-5ubuntu3.6 | trusty-updates  | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 irssi | 0.8.19-1ubuntu1   | xenial          | source, amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
 irssi | 0.8.19-1ubuntu1.9 | xenial-security | source, amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
 irssi | 0.8.19-1ubuntu1.9 | xenial-updates  | source, amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
 irssi | 1.0.5-1ubuntu4    | bionic          | source, amd64, arm64, armhf, i386, ppc64el, s390x
 irssi | 1.0.5-1ubuntu4.2  | bionic-security | source, amd64, arm64, armhf, i386, ppc64el, s390x
 irssi | 1.0.5-1ubuntu4.2  | bionic-updates  | source, amd64, arm64, armhf, i386, ppc64el, s390x
 irssi | 1.2.2-1ubuntu1    | focal           | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 irssi | 1.2.2-1ubuntu1.1  | focal-updates   | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 irssi | 1.2.3-1ubuntu4    | jammy           | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 irssi | 1.4.3-2ubuntu1    | lunar           | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 irssi | 1.4.4-2ubuntu1    | mantic          | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 irssi | 1.4.5-1ubuntu1    | noble           | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 irssi | 1.4.5-1ubuntu2    | noble-proposed  | source, amd64, arm64, armhf, ppc64el, riscv64, s390x

```

so you're possibly on *jammy* or 22.04.  Packages are built for specific releases, and if using *noble* you can use the default 1.4.5

```

guiverc@d7050-next:~$   apt-cache policy irssi
irssi:
  Installed: (none)
  Candidate: 1.4.5-1ubuntu1
  Version table:
     1.4.5-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages

```

Alternative package types are an easy way to get newer software, eg.

```

guiverc@d7050-next:~$   snap search irssi
Name   Version  Publisher      Notes  Summary
irssi  1.4.5    snapcrafters&#10026;  -      The IRC client of the future

```

ie. a `snap install irssi` will achieve a 1.4.5 install.

If you want a *deb* package, you'll need to find PPA or 3rd party source that provides the package for your *unstated* but I suspect *jammy* system (*don't forget deb packages are built for specific releases; unless they're suitable for all, such as if they only have wallpapers or other pictures that work on any system inside*).

FYI:  You can see the *noble* package requirements using sites like [https://packages.ubuntu.com/noble/irssi](https://packages.ubuntu.com/noble/irssi) and contrast with what your system has, and thus what risk of *'dependency hell*' you risk creating by installing onto your *unstated *release, but it's not a good strategy moving forward if you value your system. Snap & other solutions are safer.

---

### Post by stevenxl on 2024-01-16
Thank you for such a thorough reply. I actually did have `irssi` installed via snap, but it could not make use of `perl` when I tried to load a script. And yes, I am on jammy!

---

