---
title: "Fiesty Update not working"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by martinjh99 on 2007-08-22
Fresh Install of Kubuntu Feisty - aptitude dist-upgrade

Done dpkg --configure -a as mentioned.

How can I fix it?

```

 subprocess post-installation script returned error exit status 66
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-kde:
 openoffice.org-kde depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 2.2.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.2.0) | openoffice.org-core-experimental (>> 2.2.0); however:
  Package openoffice.org-core is not configured yet.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-crystal:
 openoffice.org-style-crystal depends on openoffice.org-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-crystal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-kde
 openoffice.org-math
 python-uno
 openoffice.org-writer
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-style-human
 openoffice.org-style-crystal
E: Sub-process /usr/bin/dpkg returned an error code 

```

---

### Post by bapoumba on 2007-08-22
Could you please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by martinjh99 on 2007-08-22
Never mind - It seems to have worked since I commented out the CDROM line!

Oh well...

---

### Post by bapoumba on 2007-08-22
No problem, it can help someone else ;)

---

### Post by slartibartfast42 on 2007-09-13
Hey, martinjh99,

I've encountered the same problem, here's how i solved it (in german):
[http://forum.ubuntuusers.de/topic/105199/#927822](http://forum.ubuntuusers.de/topic/105199/#927822)

And here's the translation (shortened a little bit):

After installing Feisty onto a test partition and starting an update I've encountered the same problems (including a slowdown when starting applications). I think the main problem is that Feisty believes the computer's internal clock works using UTC. 

So I simply changed the date in ubuntu (using right mouse click on the clock) by forwarding it one day. Then I was able to finalize the installation using "sudo apt-get upgrade". After that I reset local time to my actual time again.

Other solution: just wait for some hours (depending where you are living) then execute "sudo apt-get upgrade".

Bye,
Slartibartfast42

---

