---
title: "NOTHING Will Install On Ubuntu 11.10"
date: 2012-04-01
forum: Installation &amp; Upgrades
---

### Post by dinosaursrun on 2012-04-01
Today, every time I try to install something it gives me an error blah blah blah the update manager can repair it.

I click repair and authenticate it. It goes about halfway then it stops, I click details and this shows up:

installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 143592 files and directories currently installed.)
Preparing to replace libc6:i386 2.13-20ubuntu5 (using .../libc6_2.13-20ubuntu5.1_i386.deb) ...

A copy of the C library was found in an unexpected directory:
  '/lib/i386-linux-gnu/ld-2.13.so.dpkg-tmp'
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library or get it out of
'/lib/i386-linux-gnu' and try again.

dpkg: error processing /var/cache/apt/archives/libc6_2.13-20ubuntu5.1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.13-20ubuntu5.1_i386.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
dpkg: dependency problems prevent configuration of flashplugin-downloader:i386:
 flashplugin-downloader:i386 depends on libc6; however:
  Package libc6:i386 is not installed.
dpkg: error processing flashplugin-downloader:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however:
  Package flashplugin-downloader is not installed.
  Package flashplugin-downloader:i386 is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing libc6 (--configure):
 libc6:amd64 2.13-20ubuntu5.1 cannot be configured because libc6:i386 is in a different version (2.13-20ubuntu5)
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.13-20ubuntu5.1); however:
  Package libc6 is not configured yet.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc-dev-bin:
 libc-dev-bin depends on libc6 (>> 2.13~); however:
  Package libc6 is not configured yet.
 libc-dev-bin depends on libc6 (<< 2.14); however:
  Package libc6 is not configured yet.
dpkg: error processing libc-dev-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-i386:
 libc6-i386 depends on libc6 (= 2.13-20ubuntu5.1); however:
  Package libc6 is not configured yet.
dpkg: error processing libc6-i386 (--configure):
 dependency problems - leaving unconfigured


I am becoming highly frustrated and would like this to stop. Could anyone help me?

---

### Post by zvacet on 2012-04-02
Try with 

```
sudo dpkg --configure -a
```

---

### Post by jerrrys on 2012-04-02
A copy of the C library was found in an unexpected directory:
  '/lib/i386-linux-gnu/ld-2.13.so.dpkg-tmp'
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library or get it out of
'/lib/i386-linux-gnu' and try again.

And you did this?  If not [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal") and enter:

mv ld-2.13.so.dpkg-tmp ld-2.13.so.dpkg-tmp-XXX

This command will rename the file (XXX).  Follow that with:

sudo apt-get update

And please post any update errors that you may get.

---

