---
title: "Install clamav on ubuntu server withour ethernet"
date: 2017-01-01
forum: Installation &amp; Upgrades
---

### Post by sed_faster on 2017-01-01
Hello folks,

I intend install clamav on ubuntu server (headless) without ethernet! I know which I should install the main software (apt-get install clamav) and after this I should install all this packages:

```

user@user~$ sudo apt-cache search clamav
[sudo] password for user: 
clamav - anti-virus utility for Unix - command-line interface
clamav-base - anti-virus utility for Unix - base package
clamav-daemon - anti-virus utility for Unix - scanner daemon
clamav-dbg - debug symbols for ClamAV
clamav-docs - anti-virus utility for Unix - documentation
clamav-freshclam - anti-virus utility for Unix - virus database update utility
clamdscan - anti-virus utility for Unix - scanner client
libclamav-dev - anti-virus utility for Unix - development files
libclamav7 - anti-virus utility for Unix - library
clamav-testfiles - anti-virus utility for Unix - test files
clamav-unofficial-sigs - update script for 3rd-party clamav signatures
clamfs - user-space anti-virus protected file system

```

Is It necessary install all this package?
How can I downloaded all this packages and install on pc (headless) without ethernet?

Maybe I should after install all this stuff run command "apt-get update" - "apt-get upgrade". But on this pc, as been without ethernet, this isn't very logical. How can I do this?
thanks

---

