---
title: "Install mailutils without installing mysql-common"
date: 2015-01-10
forum: Installation &amp; Upgrades
---

### Post by Larry_Irwin on 2015-01-10
Hi All,

This post is a band-aid to get around a dependency issue in the mailutils package.

MySQL 5.5.40 in the Ubuntu 14.04.1 and Debian distributions was causing innodb corruption when we ran our weekly update script that implements about a hundred ALTER TABLE commands. It was intermittent, so I could not log a bug report, since I could not show how to replicate it reliably.

I removed all mysql 5.5.40 packages and installed the 5.6 binary from mysql instead - using the standard installation in /usr/local... That fixed the problem. the ALTER TABLE scripts worked fine... But...

To my surprise, under Ubuntu, the package "mailutils" was removed!
(this did not happen on Debian 7, just Ubuntu 14.04.1)
And when I went to re-install it, the dependencies wanted to install mysql-common, which has more than libs, it has executables as well... Arrgghh.
I didn't want any pieces of mysql 5.5.40 anywhere on my servers!

So - here is how to get /usr/bin/mail operational again with the minimum dependencies required to make it work:

==Code==
#!/bin/bash
# On Ubuntu 14.04.1 LTS, uninstalling mysql removes mailutils...
# Installing mailutils will install dependencies that include mysql-common-5.5...
# So, here we install mailutils using only those dependencies that are
# absolutely required by the executable /usr/bin/mail
# First - don't do this if /usr/bin/mail already exists... (like in the Debian versions vs. Ubuntu...)
# For some reason, removing mysql 5.5 from Debian 7 doesn't remove mailutils...
[ -x /usr/bin/mail ] || {
  rm -r ./mailtmp >/dev/null 2>&1
  mkdir ./mailtmp
  cd ./mailtmp
  apt-get download libmysqlclient18
  apt-get download libmailutils4
  apt-get download mailutils
  dpkg --force-all -i libmysqlclient18*.deb
  dpkg --force-all -i libmailutils4*.deb
  dpkg --force-all -i mailutils*.deb
  cd ..
  rm -r ./mailtmp
}
==End Code==

Enjoy!
Larry Irwin

---

