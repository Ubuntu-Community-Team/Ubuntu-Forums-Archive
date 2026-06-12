---
title: "Synpatic and APT do never connect!"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by gtheus on 2007-03-03
Hi,
I'm going  mad: I installed ubuntu 6.10 without further problems, lan and wlan was configured and I'm using Firefox right now. Fine, but...
Synaptic and apt are my problems: I did not manage to have them work! They do not connect to the repository servers. With Firefox I can download the packages from the same address within seconds, but not with synaptic! I get a timeout error all the time. What's wrong with synaptic (and apt)?

---

### Post by zvacet on 2007-03-03
Did you open repositories?Did you try local server?Main if the local doesn´t work?

---

### Post by gtheus on 2007-03-03
Yes - changed from local server to main server - no success. Tried also with "apt-get update", but all I get is a timeout error!

---

### Post by gtheus on 2007-03-03
I have to correct my posting: MEanwhile I managed to have connection - but only for a short time. Are the ubuntu servers completely overloaded?

---

### Post by Kateikyoushi on 2007-03-03
You need to edit the sources list change the http to ftp then try to update again.

---

### Post by gtheus on 2007-03-03
Sorry - cahnging to "ftp" does not change the behaviour of Synaptic. No connection.

---

### Post by gtheus on 2007-03-03
Problem-update: I was able to download some packages with apt-get, now. I changed server address in /etc/apt/sources.list to "http://in.archive.ubuntu.com/" (instead of "ch.archive..."). But after two downloaded and installed packages, apt refuses now again any connection. At same time I surf the web with Firefox, so I don't think that a local network problem is causing my troubles.

---

### Post by bapoumba on 2007-03-03
> **gtheus said:**
> At same time I surf the web with Firefox, so I don't think that a local network problem is causing my troubles.
Yes and no. Just to make sure, are you behind a proxy ?
And could you please post the complete error message to **sudo aptitude update** and your source.list (**cat /etc/apt/sources.list**) ?

---

