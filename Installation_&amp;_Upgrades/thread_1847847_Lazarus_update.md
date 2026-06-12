---
title: "Lazarus update"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by DrIainAnderson on 2011-09-21
I like to use Lazarus as development environment. My major problem is that my current installation of Ubuntu (11.04) insists that the newest available version is 0.9.28 and nothing that I do can change its mind, while when I use a live version synaptic offers me 0.9.30. I have tried complete removal. Purge with apt-get followed by autoclean and using the testing repository at [www.hu.freepascal.org]("http://www.hu.freepascal.org"). Everything offers 0.9.28. So how can I upgrade?

---

### Post by ajgreeny on 2011-09-21
Try this ppa which has the 0.9.30 version available.
[https://launchpad.net/~jtaylor/+archive/jtaylor](https://launchpad.net/~jtaylor/+archive/jtaylor)

---

### Post by DrIainAnderson on 2011-09-23
So far so good... Now I have 0.9.30 (many thanks to jtaylor) but with a load of missing packages and the usual Can't find unit interfaces message. When I try to download lcl-gtk2 I follow a list of missing dependencies to fp-units-misc require fpc-2.4.0 but fpc-2.4.2 is selected. This is what I found when I tried to use the SVN version. I thought Synaptic et al are supposed to protect us poor users from this sort of thing.
Giving up for now and going sailing but will try again next week. Thanks again for the link.

---

