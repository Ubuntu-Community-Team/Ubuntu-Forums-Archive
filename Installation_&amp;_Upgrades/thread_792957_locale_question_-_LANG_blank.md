---
title: "locale question - LANG blank"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by kohudson on 2008-05-13
When setting up my new gutsy slice I entered the following two commands:

sudo locale-gen en_US.UTF-8
sudo /usr/sbin/update-locale LANG=en_US.UTF-8

If I do a locale command the output looks like this:

LANG=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=

Is this correct? Why doesn't "LANG" have a value?

Thanks, Ken

---

