---
title: "lookin for info on installing packets"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by terahl on 2008-06-13
hey there, i'm new to ubuntu, have tried it before but never for a long period of time, however now I have a computer completely dedicated to running ubuntu and I'd like to learn how to install packets/packages using the terminal / shell (dunno the diff).

I'd like to know what format should I use, how it works etc...

thanks in advance!

---

### Post by argail1980 on 2008-06-13
the tool is aptitude.. some examples:

look up if a package (i.e. firefox)is available or installed

```
sudo aptitude search firefox
```
or
```
sudo apt-cache search firefox
```

install package

```
sudo apt-get install firefox
```

update the system

```
sudo apt-get update
sudo apt-get upgrade
```

update reads the most recent package lists, upgrade installs updates.

do 

```
man apt-get
``` for documentation

---

### Post by kellemes on 2008-06-13
> **terahl said:**
> hey there, i'm new to ubuntu, have tried it before but never for a long period of time, however now I have a computer completely dedicated to running ubuntu and I'd like to learn how to install packets/packages using the terminal / shell (dunno the diff).

I'd like to know what format should I use, how it works etc...

thanks in advance!

Couple of links..
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")
[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by Pumalite on 2008-06-13
Tutorials for Linux/Ubuntu:
[http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)
[http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html](http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html)
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

---

### Post by terahl on 2008-06-13
thanks I'll put'em to good use.

---

