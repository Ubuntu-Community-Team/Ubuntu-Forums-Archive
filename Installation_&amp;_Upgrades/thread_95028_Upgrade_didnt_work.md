---
title: "Upgrade didnt work?"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by Devinci on 2005-11-25
Hi, I had warty on cd, so i installed warty, then edited sources for breezy.

```

 deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

 deb http://us.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe


```

Did  an apt-get update, then an apt-get dist-upgrade.

It removed ubuntu-desktop or so it said, and downloaded about 30meg of stuff such as Nautilus and openoffice.

Now, it still says I'm on Warty?

I also tried apt-get install ubuntu-base ubuntu-desktop:

```
devinci@ubuntu:~ $ sudo apt-get install ubuntu-base ubuntu-desktop
Reading Package Lists... Done
Building Dependency Tree... Done
ubuntu-base is already the newest version.
Package ubuntu-desktop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-desktop has no installation candidate
devinci@ubuntu:~ $

```

What else can I do to upgrade properly?

---

### Post by taurus on 2005-11-25
Did you reboot after upgrading???  :rolleyes:

---

### Post by Devinci on 2005-11-25
Yes i had!  But nevermind, I solved it, I guess I was missing a source, now it's downloading 400M rather than 30!

---

