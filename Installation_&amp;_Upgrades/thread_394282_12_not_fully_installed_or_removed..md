---
title: "12 not fully installed or removed."
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by foxiness on 2007-03-26
1-sudo apt-get dist-upgrade
2-show me this :"12 not fully installed or removed."
3- yes or no "Do you want to continue [Y/n]? "
4-long errro url: [http://pastebin.ca/411303](http://pastebin.ca/411303)

summery of the errro:

Errors were encountered while processing:
 compiz-plugins
 compiz-gtk
 compiz-gnome
 compiz
 evolution
 evolution-plugins
 gnome-games-data
 gnome-games
 gnome-session
 gthumb
 gwget
 libgksu2-0
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zvacet on 2007-03-26
```
sudo aptitude update
```
```
sudo aptitude upgrade
```

---

### Post by foxiness on 2007-03-26
thanks for help,but not fix the problem of this 12 package

you can found here a full output of aptitude [http://pastebin.ca/411350](http://pastebin.ca/411350)

what apt-get dist-upgrade try to do?

$ sudo apt-get dist-upgrade -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Conf compiz-plugins (1:0.3.6-1ubuntu9 Ubuntu:7.04/feisty)
Conf compiz-gtk (1:0.3.6-1ubuntu9 Ubuntu:7.04/feisty)
Conf compiz-gnome (1:0.3.6-1ubuntu9 Ubuntu:7.04/feisty)
Conf compiz (1:0.3.6-1ubuntu9 Ubuntu:7.04/feisty)
Conf evolution (2.10.0-0ubuntu2 Ubuntu:7.04/feisty)
Conf evolution-plugins (2.10.0-0ubuntu2 Ubuntu:7.04/feisty)
Conf gnome-games-data (1:2.18.0.1-0ubuntu1 Ubuntu:7.04/feisty)
Conf gnome-games (1:2.18.0.1-0ubuntu1 Ubuntu:7.04/feisty)
Conf gnome-session (2.18.0-0ubuntu2 Ubuntu:7.04/feisty)
Conf gthumb (3:2.10.0-0ubuntu1 Ubuntu:7.04/feisty)
Conf gwget (0.98.1-2ubuntu1 Ubuntu:7.04/feisty)
Conf libgksu2-0 (2.0.3-3ubuntu5 Ubuntu:7.04/feisty)

---

### Post by foxiness on 2007-03-27
you can use 
```

sudo apt-get remove --purge package 

```

and i found it will fix on short term the problem but it will come up with another package to me.

---

