---
title: "unmet dependency when trying to install php5-intl"
date: 2016-07-22
forum: Installation &amp; Upgrades
---

### Post by mpiii on 2016-07-22
This is my first post here, please forgive any formatting errors.

I'm trying to install php5-intl on my Ubuntu 14.04 LTS. This as a prerequisite of another package (owncloud 9).

I however get the following:
```
The following packages have unmet dependencies:
 php5-intl : Depends: php5-common (= 5.5.9+dfsg-1ubuntu4) but 5.5.9+dfsg-1ubuntu4.17 is to be installed
```

investigating the policy (apt-cache policy php5-intl php5-common) gives

```
php5-intl:
  Installed: (none)
  Candidate: 5.5.9+dfsg-1ubuntu4
  Version table:
     5.5.9+dfsg-1ubuntu4 0
        500 http://nl.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
php5-common:
  Installed: 5.5.9+dfsg-1ubuntu4.17
  Candidate: 5.5.9+dfsg-1ubuntu4.17
  Version table:
 *** 5.5.9+dfsg-1ubuntu4.17 0
        500 http://nl.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.5.9+dfsg-1ubuntu4 0
        500 http://nl.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

The contents of my /etc/apt/sources.list
```

eb http://nl.archive.ubuntu.com/ubuntu/ trusty main restricted
deb http://nl.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb http://nl.archive.ubuntu.com/ubuntu trusty universe
deb http://nl.archive.ubuntu.com/ubuntu trusty multiverse
deb http://security.ubuntu.com/ubuntu trusty-security main restricted
# deb-src http://nl.archive.ubuntu.com/ubuntu trusty universe
# deb-src http://nl.archive.ubuntu.com/ubuntu trusty multiverse

```

problem to me seems to be that the 4.17 version of php5-intl is not being recognized as being present.
my interpretation of [https://launchpad.net/ubuntu/trusty/amd64/php5-intl/5.5.9+dfsg-1ubuntu4.17](https://launchpad.net/ubuntu/trusty/amd64/php5-intl/5.5.9+dfsg-1ubuntu4.17) is that this version should be present in the universe repository
```


php5-intl 5.5.9+dfsg-1ubuntu4.17 (amd64 binary) in ubuntu trusty

    Trusty (14.04) amd64 php5-intl 5.5.9+dfsg-1ubuntu4.17 

 This package provides a module to ease internationalisation of PHP scripts.
 .
 PHP (recursive acronym for PHP: Hypertext Preprocessor) is a widely-used
 open source general-purpose scripting language that is especially suited
 for web development and can be embedded into HTML.
Details

Package version:
    5.5.9+dfsg-1ubuntu4.17

Source:
    php5 5.5.9+dfsg-1ubuntu4.17 source package in Ubuntu

Status:
    Published

Component:
    universe

Priority:
    Optional

Downloadable files
amd64 build of php5 5.5.9+dfsg-1ubuntu4.17 in ubuntu trusty RELEASE produced these files:

    php5-intl_5.5.9+dfsg-1ubuntu4.17_amd64.deb (106.3 KiB)


```

Am I missing something? How can I install php5-intl, preferably the latest 4.17 version and future (security) updates?
I guess I can somehow manually install the downloadable file mentioned, but I'm not sure thats the way to go.

Help is appreciated.

---

