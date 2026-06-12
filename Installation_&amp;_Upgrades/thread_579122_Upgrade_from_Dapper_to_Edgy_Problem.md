---
title: "Upgrade from Dapper to Edgy Problem"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by bayvista on 2007-10-18
I When I enter the command 

gksu "update-manager -c"

I just get a message " warnings.warn("apt API not stable yet", FutureWarning)" Nothing is updated.

Any ideas??

---

### Post by zvacet on 2007-10-18
> Ubuntu Dapper to edgy update error

If you try to run the update manager if you receive following error

gksudo update-manager

warnings.warn(&#8221;apt API not stable yet&#8221;, FutureWarning)
/usr/lib/python2.4/site-packages/UpdateManager/MetaRelease.py:171: DeprecationWarning: Class MetaRelease is already

GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
gobject.type_register(MetaRelease) extracting &#8216;/tmp/tmpw5fQ_q/dapper.tar.gz&#8217;
authenticate &#8216;/tmp/tmpw5fQ_q/dapper.tar.gz&#8217; against &#8216;/tmp/tmpw5fQ_q/dapper.tar.gz.gpg&#8217;
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet warnings.warn(&#8221;apt API not stable yet&#8221;, FutureWarning) can&#8217;t find DistUpgrade ViewGtk

Solution

Install this python component

apt-get install python-vte

I hope this will help.

---

### Post by Cannaregio on 2007-10-18
> Upgrade from Dapper to Edgy Problem

from dapper to edgy?

---

### Post by erginemr on 2007-10-18
Bayvista, are you planning to upgrade one by one from Dapper to Edgy and from Edgy to Feisty? And when it is out, from Feisty to Gutsy?

---

### Post by FictionPimp on 2007-10-18
I am actually looking to do just that. 

I have a development server that is not used for anything but a playground. We want to play with gutsy on it. So I'm looking for the best way to go from 6.06 to 7.10 without re-installing.

---

### Post by erginemr on 2007-10-18
Though job, I would say. Given the fact that upgrading even from two successive versions only is often very problematic; I cannot think of striding several steps.

I am afraid to say you will need to do a fresh install of Gutsy, otherwise the resulting after subsequent upgrades will look like Frankenstein.  

You may salvage many of your settings by backing up /home and /etc folders, but you will need to reinstall the extra programs, of course.

---

