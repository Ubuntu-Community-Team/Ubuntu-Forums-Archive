---
title: "PHP5 on 7.04 with apache2"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by jesusrocksmyfaceoff on 2007-05-26
trying to install php5 on ubuntu 7.04 running apache.  Install goes fine, I also install libapache-mod-php5 and that seems to go well too.. only problem is that php5 isn't an available (or enabled) module for apache.  I installed using the apt-get install command from the terminal and using synaptic package manager, neither option worked.  Also tried reinstalling apache(2) to no avail.  I can't figure out what's going on!!  This wouldn't be much of a problem really, if I could figure out how to get the server to parse the PHP code.. Firefox prompts me to save the file when i try to load it..  I have tried modifying httpd.conf(or apache2.conf in this case), and that doesn't work... please help!!!  (also installed other necessary php5 items.. like php5-common, etc).

---

### Post by blacksadness on 2007-05-28
hey,
you probably missed some options, in synaptic do: edit -> select packages by task and select a lamp server

---

