---
title: "problem with apt API -- can't upgrade"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by dpoyesac on 2008-05-26
I'm having a heck of a time upgrading from 6.06 to 8.04, even with Dapper fully updated. The problem I'm having is the same as in [this]("http://ubuntuforums.org/showthread.php?t=802466&highlight=apt+API") thread: when I try to run (in the Terminal):

[FONT="Courier New"]gksu "update-manager -d"[/FONT]

I get the following message 

[FONT="Courier New"]/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
[/FONT]

One solution (from [this]("http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html") thread) was to run [FONT="Courier New"]apt-get install python-vte[/FONT], but I have the current version. 

Without fixing this API problem I can't upgrade to 8.04. (I don't have a CD burner so doing an install from a burned CD will be a problem.) 

Any suggestions? Thanks!

---

### Post by Pumalite on 2008-05-26
unetbootin:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

