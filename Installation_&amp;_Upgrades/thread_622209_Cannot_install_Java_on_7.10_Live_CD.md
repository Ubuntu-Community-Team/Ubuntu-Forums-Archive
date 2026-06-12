---
title: "Cannot install Java on 7.10 Live CD"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by purifyyourmind on 2007-11-24
I've been wanting to switch over to Linux, but there are still a couple of things keeping me on Windows. On of them is that I'd like to run this program:

[http://www.gokgs.com/download.xhtml](http://www.gokgs.com/download.xhtml)

...but I can't get Java installed. At least not on the Live CD (but I've seen people with regular installs have problems too).

Please see the attached screenshots for details on the problem. Note that I've enabled all repositories, so that's not the issue. I've tried uninstalling, reinstalling, etc. including the library that is mentioned in the errors. I have read a number of threads here and elsewhere about people having this problem.

Thanks!

---

### Post by Pumalite on 2007-11-24
You cannot install java in the Live CD. Somebody correct me if I'm wrong. Once installed it should be no problem.

---

### Post by prodezigner on 2007-11-24
He's right. You can't really 'install' anything to a Live CD, cause well... it's a CD, not a hard drive.

JAVA works fine on my machines on HDDs.

When you do make the leap make sure to edit your /etc/apt/sources.list exclude the CD-ROM repo at the top, and enable all the others commented out.

JRE should be in one of the repos using apt-get.

---

