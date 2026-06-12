---
title: "Can't update or install any program anymore"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by erichbuhler on 2013-03-30
Hi guys,
when I try to update or install a program, I get the following error:

Package: /var/cache/apt/archives/libreoffice-common_1%3a4.0.2~rc1-0ubuntu1~precise2_all.deb
Error: trying to overwrite '/usr/lib/libreoffice/program/officehelper.py', which is also in package libreoffice-emailmerge 1:4.0.1~rc2-0ubuntu1~precise1~ppa1

Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise

Can anyone help me please?

Thanks in advance,
Erich.

---

### Post by carl4926 on 2013-03-30
Try
```

sudo apt-get clean all
```

---

### Post by erichbuhler on 2013-03-30
> **carl4926 said:**
> Try
```

sudo apt-get clean all
```

Thanks for your reply,
I have tried running it on the terminal but apart from asking me the administrator's password, it does not do anything after it.
I run the software update one more time and got the following error:

Any idea?

installArchives() failed: Error in function: 
Setting up libreoffice-style-human (1:4.0.2~rc1-0ubuntu1~precise2) ...
Setting up libxml2 (2.7.8.dfsg-5.1ubuntu4.4) ...
Setting up libssl1.0.0 (1.0.1-4ubuntu5.8) ...
Setting up libreoffice-style-tango (1:4.0.2~rc1-0ubuntu1~precise2) ...
Setting up libneon27-gnutls (0.29.6-1ubuntu1) ...
Setting up fonts-opensymbol (2:102.2+LibO4.0.2~rc1-0ubuntu1~precise2) ...
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on libreoffice-common (>> 1:4.0.2~rc1); however:
  Version of libreoffice-common on system is 1:4.0.1~rc2-0ubuntu1~precise1~ppa1.
dpkg: error processing libreoffice-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:4.0.2~rc1-0ubuntu1~precise2); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-impress:
 libreoffice-impress depends on libreoffice-core (= 1:4.0.2~rc1-0ubuntu1~precise2); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-writer:
 libreoffice-writer depends on libreoffice-core (= 1:4.0.2~rc1-0ubuntu1~precise2); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base-core:
 libreoffice-base-core depends on libreoffice-core (= 1:4.0.2~rc1-0ubuntu1~precise2); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on libreoffice-core (= 1:4.0.2~rc1-0ubuntu1~precise2); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-kde:
 libreoffice-kde depends on libreoffice-core (= 1:4.0.2~rc1-0ubuntu1~precise2); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gtk:
 libreoffice-gtk depends on libreoffice-core (= 1:4.0.2~rc1-0ubuntu1~precise2); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on libreoffice-core (= 1:4.0.2~rc1-0ubuntu1~precise2); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-draw:
 libreoffice-draw depends on libreoffice-core (= 1:4.0.2~rc1-0ubuntu1~precise2); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-calc:
 libreoffice-calc depends on libreoffice-base-core (= 1:4.0.2~rc1-0ubuntu1~precise2); however:
  Package libreoffice-base-core is not configured yet.
 libreoffice-calc depends on libreoffice-core (= 1:4.0.2~rc1-0ubuntu1~precise2); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-calc (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by carl4926 on 2013-03-30
Maybe you are using a PPA for LO?
Prol not a good idea

---

### Post by dabl on 2013-03-30
First, completely remove libreoffice:

```
sudo apt-get purge libreoffice
```


Then let us see what version is available from your repos:

```
sudo apt-get update && sudo apt-cache policy libreoffice
```


Then we can probably install a version that will work.

---

### Post by schragge on 2013-03-30
Please don't open second thread about [thread=2130011]the same problem[/thread]

---

### Post by erichbuhler on 2013-03-30
> **schragge said:**
> Please don't open second thread about [thread=2130011]the same problem[/thread]

Sorry about it, couldn't find my previous thread :-(

The solution is as described:


dpkg --get-selections libreoffice\*|sed 's/\<install$/deinstall/'|sudo dpkg --set-selectionssudo dpkg -rasudo apt-get -f installThanks for your time guys, really appreciate it!!!

---

