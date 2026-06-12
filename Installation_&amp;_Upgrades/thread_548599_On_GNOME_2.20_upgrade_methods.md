---
title: "On GNOME 2.20 upgrade methods"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by pdavit on 2007-09-11
Just a question guys on how this works.

Ok, so Ubuntu v7.10 is the upcoming release. It will include GNOME 2.20.

But GNOME 2.20 is released prior to v7.10 of Ubuntu. 

Will the upgrade to GNOME 2.20 be automatically available via the Update Manager
or do we have to wait for the official and final release of Ubuntu v7.10?

I'm not asking here if it's technically possible to have it beforehand but if this
is done "officially" by the Update Manager without coupling it with a Tribe, Beta 
or final release of an upcoming distro upgrade.

---

### Post by kenji-san on 2007-09-11
> **pdavit said:**
> ...But GNOME 2.20 is released prior to v7.10 of Ubuntu. ...
That is intentional.  See the wikipedia [article on Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution)").

From the 'development process' section:
> Ubuntu's first release was on October 20, 2004, which began by making a temporary fork of the Debian GNU/Linux project. This was done so that a new version of Ubuntu could be released every six months, resulting in a more frequently updated system. Ubuntu releases always include the most recent GNOME release, and are scheduled to be released about a month after GNOME.

I will defer your question to someone with more experience with GNOME. :)

---

### Post by pdavit on 2007-09-11
Yes, yes I know that this is done intentionally.

My question is if I could "officially" have Ubuntu v7.04 running GNOME 2.20 or 
do I have to wait for the next distro release?

---

### Post by rsambuca on 2007-09-11
Basically any opensource software written for use with linux can be compiled to run on ubuntu.  Just download it from the website and compile it.

---

### Post by kenji-san on 2007-09-11
> **pdavit said:**
> Yes, yes I know that this is done intentionally.

My question is if I could "officially" have Ubuntu v7.04 running GNOME 2.20 or 
do I have to wait for the next distro release?
I would say no, but I could be wrong.  So many of Fiesty's tools are built for 2.18 GNOME libraries that they would most likely break if you ran them against the 2.20 libraries.  Not to mention all the rest of the software repository that depends on GNOME.  This would basically require a distro upgrade to stay 'official'.  Backward compatability is easy but forward compatability is much harder to achieve.

Hope that is of some help.

---

