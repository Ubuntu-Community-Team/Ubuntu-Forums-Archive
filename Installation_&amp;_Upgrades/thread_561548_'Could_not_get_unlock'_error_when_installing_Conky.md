---
title: "'Could not get unlock' error when installing Conky"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by toecutter on 2007-09-27
I'm trying to install Conky ([http://conky.sourceforge.net/](http://conky.sourceforge.net/)) but got this error:

```
frank@frank-linux:~$ sudo apt-get install conky
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  conky
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

What is this error, and how can I get around it?

---

### Post by Pumalite on 2007-09-27
Try this:

sudo chmod 777 /var/cache/apt/archives/lock

And then try again

---

### Post by toecutter on 2007-09-28
Excellent! That did it :)

Many thanks!

Now I just have to figure out these customization scripts... :D

---

### Post by Pumalite on 2007-09-28
You are welcome. Good luck.

---

