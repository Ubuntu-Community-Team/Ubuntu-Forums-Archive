---
title: "Problem installing php5-imap"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by friism on 2006-07-13
Hi

I've installed SugarCRM and it's working great - except retrieving emails from external accounts isn't working. This feature needs IMAP support, so I want to install the php5-imap package. Trying yields this:
```
friism@young:~$ sudo apt-get install php5-imap
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-imap: Depends: libc-client2002edebian but it is not going to be installed

             Depends: libkrb53 (>= 1.4.2) but 1.3.6-4 is to be installed
             Depends: libssl0.9.8 (>= 0.9.8a-1) but it is not installable
             Depends: phpapi-20051025 but it is not installable
E: Broken packages
friism@young:~$
```

Any ideas?

sources.list:
```
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted univer\
se multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted un\
iverse multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiver\
se restricted

deb http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://us.archive.ubuntu.com/ubuntu dapper universe

#deb http://packages.dotdeb.org/ stable all

deb http://cobain.matteomoro.net/debian unstable/

```

I've tried to convince apt-get to install the package without the  correct dependencies, but to no avail. Any help will be greatly appreciated.

---

### Post by friism on 2006-07-13
Great, got it working. I just removed some of the more exotic repositories, and the problem went away.

---

