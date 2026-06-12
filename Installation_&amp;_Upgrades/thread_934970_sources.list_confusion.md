---
title: "sources.list confusion"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by talktorishav on 2008-10-01
Hi,

lets take an example of [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/)

If I check launchpad via [https://launchpad.net/ubuntu/+mirror/ubuntu.mirror.cambrium.nl-archive](https://launchpad.net/ubuntu/+mirror/ubuntu.mirror.cambrium.nl-archive)

it, lists only

deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy main
deb-src [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy main

to add to sources.list

But if you see the mirror then there is a lot more than that, like hardy-updates hardy-security hardy-backports and so on............

instead of using the two lines mentioned by launchpad don't we have to add 

deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy main universe multiverse restricted
deb-src [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy main universe multiverse restricted

deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy-universe main universe multiverse restricted
deb-src [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy-universe main universe multiverse restricted

and so on........................

:popcorn:

---

### Post by talktorishav on 2008-10-03
bump.

isnt' this an easy questioN?

---

### Post by zipperback on 2008-10-03
If for example the website you are referencing is instructing you to add the following to your sources list:

> 
deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy main
deb-src [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy main


Then that is exactly what you should add, providing of course, that it is for the correct version of your Linux installation, because that is what they are providing in their repository.

Others might provide something different, but in the example above. "hardy main" is what is available from them unless they specify otherwise.


- zipperback
:popcorn:

---

### Post by talktorishav on 2008-10-05
> **zipperback said:**
> If for example the website you are referencing is instructing you to add the following to your sources list:



Then that is exactly what you should add, providing of course, that it is for the correct version of your Linux installation, because that is what they are providing in their repository.

Others might provide something different, but in the example above. "hardy main" is what is available from them unless they specify otherwise.


- zipperback
:popcorn:

But if you open the mirror in your browser its maintaining all the other stuffs too.
and if i keep them though they havn't mentioned they works too.
What can be the reason?

---

### Post by talktorishav on 2008-10-12
bump!

Also if i put

deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy main universe multiverse restricted
deb-src [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy main universe multiverse restricted

deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy-universe main universe multiverse restricted
deb-src [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy-universe main universe multiverse restricted

and so on........................

it works.

Then why isn't it mentioned on launchpad?

---

