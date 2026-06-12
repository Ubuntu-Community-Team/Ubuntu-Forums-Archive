---
title: "local repository for apt-get"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by Mr.Jkate on 2008-07-02
Hello,
I've one server and clinet machine running Ubuntu 7.1.
I've developed few applications like sip client etc...and packaged as rpms and installed on client. Now I want to setup repository of rpms related with the applications I've developed so that If I run apt-get and it should download latest rpms from server and install on client.
all downloads for rpms should be via ftp.
Plz advise

---

### Post by scragar on 2008-07-02
[http://mediakey.dk/~cc/howto-create-your-own-debian-or-ubuntu-package-repository/](http://mediakey.dk/~cc/howto-create-your-own-debian-or-ubuntu-package-repository/)

That's a pretty good guide, although it's missing a few points(such as how to make them FTP, how ever as long as everything is done via FTP there's no problem), but it's a fantastic guide to start.


P.S. ubuntu doesn't use RPMs, it uses .DEB files.

---

