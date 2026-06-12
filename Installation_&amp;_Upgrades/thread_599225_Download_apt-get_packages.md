---
title: "Download apt-get packages"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by rpjanaka on 2007-11-01
hi all,

i don't have network facilities for my home computer. so i could not install some packages easily like when it use "apt-get install".
although i get downloaded the required source file, they ask for many dependencies when it is going to install. but such a problem does not occurs when it use "apt-get install"

so i think it may done by the apt automatically. 

how this automatically dependency handling method is working.

---

### Post by ofb on 2007-11-01
I don't think I understand your question yet.

Are you asking: Does 'apt-get install' handle dependancies automatically? Yes, it does.

Perhaps this is helpful:
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)

---

### Post by rpjanaka on 2007-11-08
> **ofb said:**
> I don't think I understand your question yet.

Are you asking: Does 'apt-get install' handle dependancies automatically? Yes, it does.

Perhaps this is helpful:
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)


i want to install camorama package. this can be done with "sudo apt-get install camorama" if i am online

but i want to install this package off line. so i just got download camorama package and try to make install it. but it ask for several dependency packages.

i have face to this problem not only at this time. so i want to know a way to get download the required package with its dependency packages.

"apt-get source camorama" can be used to get the source of this package only not the dependencies

so please help me to do this....

---

### Post by zvacet on 2007-11-08
You can try this(it will show you link to all packages you need)

[http://www.ubuntu-hr.org/proba.php]("http://www.ubuntu-hr.org/proba.php")

or 

[http://nonetdebs.homeip.net/]("http://nonetdebs.homeip.net/")

---

