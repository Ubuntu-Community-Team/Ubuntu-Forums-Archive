---
title: "Opera stopped working. And other install troubles"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by Alex N on 2007-04-27
It looks like my Edgy installation begins to degrade. Things goes from bad to worse. 
I still can not bring LAMP to work (and nobody can help me), meanwhile Opera stopped working.

It crushes instantly, so I decided to reinstall it. This attempt caused a deadlock. I have .deb package
of opera 9.10 on my HDD. Trying to install it ends with the message :

... conflicts with package opera. 

Yes, after removal of the opera package. It seems to conflict with itself.
There is opera 9.20 in Synaptic (but no 9.10) which does not install. It says that library dependencies could not be satisfied.

Finally something wrong happens to Synaptic itself. I tried to manually add repositories, but they
do not appear in the list. However I suspect that they are somewhere, because I am getting new
messages about unreadable packages (those messages never appeared before I tried to add
repositories).

The whole system looks very unstable.:confused: 

What to do ? I am thinking about finishing the Linux experiment. I am spending too much time
doing too simple things.:mad:

---

### Post by zvacet on 2007-04-28
```
gksudo gedit /etc/apt/sources.list
```

Delete repositories that you add manualy or comment them(put # sign in front of the line).

Download Opera from here

[http://www.opera.com/download/]("http://www.opera.com/download/")


and just double click on package

Sorry,I can not help you with LAMP.Best I can tell you is to search the forum.I don´t belive that is nothing there.

---

