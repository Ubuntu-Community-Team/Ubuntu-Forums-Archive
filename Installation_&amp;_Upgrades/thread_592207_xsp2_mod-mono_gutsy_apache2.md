---
title: "xsp2 mod-mono gutsy apache2"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by funkgui on 2007-10-26
Hi there,

I've spend two days tring to install mod-mono for apache2 with no success!

I've tried on a clean installed ubuntu gutsy installing from apt all the packages (apache2, mono-apache-server, mono-apache-server2), then tried compiling from source apache (2.2 and 2.0 versio) and xsp and mod-mono... no success 

apache still say mod-mono installed but no asp pages are served...

I solved many error catched from apache logs and when I finally get no errors I got service unavailable or site down etc...

then I tried on a new clean installed ubuntu gutsy

apt-get install mono-xsp2 asp.net2-examples

and [http://localhost:8082/samples](http://localhost:8082/samples) remain loading but no example are displayed...

DOES ANYONE HAVE SUCCESS with GUTSY-XSP2 or (better) GUTSY-APACHE2-MOD-MONO?

Please Help me...

p.s.  
I tried on a new clean installed ubuntu feisty
apt-get install mono-xsp2 asp.net2-examples
and it works...
alse mod-mono and apache2 works great!

funkgui

---

### Post by ikus060 on 2007-11-30
Did you solve your problem ?? Because, I have similar problem.

---

### Post by liorwohl on 2007-12-08
> **ikus060 said:**
> Did you solve your problem ?? Because, I have similar problem.

+1

---

### Post by funkgui on 2008-01-24
not yet...

I'm still trying to solve it but I've spent a lot of time without success...

Now I think I'm doing the right things but seems the system does not do what I ask :-(

stay tuned I will inform on update...

---

### Post by byjg on 2008-02-05
I dont know why, but you need specify the path for asp.net samples in gutsy:

xsp2 --applications /:/usr/share/asp.net2-demos

and [http://localhost:8080/](http://localhost:8080/) works... But the system look for a index2.aspx, but i cant found! 

I used to install:
sudo aptitude install mono-gmcs mono-apache-server2  asp.net2-examples mono-xsp2

---

