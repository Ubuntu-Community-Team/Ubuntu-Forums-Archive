---
title: "can't install zlib1g-dev"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by hunham on 2005-10-13
After upgrading to breezy, I try to install zlib1g-dev and I get this message:

The following packages have unmet dependencies:
  zlib1g-dev: Depends: zlib1g (= 1:1.2.2-4ubuntu1.2) but 1:1.2.3-3ubuntu4 is to be installed
E: Broken packages

Help?
Thanks,
--Gabor
:confused:

---

### Post by minkin on 2006-05-06
I am seeing the same error.  I am trying to install zlib1g-dev for breezy 5.10.  I see the same error as above.  I need to install zlib1g-dev to be able to run ruby gems.

mike@ubuntu:~ $ sudo dpkg --install zlib1g-dev_1.2.3-11_i386.deb
Password:
Selecting previously deselected package zlib1g-dev.
(Reading database ... 85502 files and directories currently installed.)
Unpacking zlib1g-dev (from zlib1g-dev_1.2.3-11_i386.deb) ...
dpkg: dependency problems prevent configuration of zlib1g-dev:
 zlib1g-dev depends on zlib1g (= 1:1.2.3-11); however:
  Version of zlib1g on system is 1:1.2.3-3ubuntu4.
dpkg: error processing zlib1g-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 zlib1g-dev

---

### Post by minkin on 2006-05-06
well - I fixed my problem with ruby gems.  Had to install ruby-zlib and that fixed the issue.

[http://raa.ruby-lang.org/project/ruby-zlib](http://raa.ruby-lang.org/project/ruby-zlib)

---

