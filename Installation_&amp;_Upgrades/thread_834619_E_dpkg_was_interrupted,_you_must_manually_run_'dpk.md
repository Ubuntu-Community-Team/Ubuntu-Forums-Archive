---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by KEE on 2008-06-19
ok i want to go in to synaptic manager but this keeps happening 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." 

and i cant access to synaptic manager or remove/download any programs...any ideas or suggestions ?

---

### Post by jimbob on 2008-06-19
Open a terminal and enter sudo dpkg --configure -a and let us know what happens.

---

### Post by KEE on 2008-06-19
> **jimbob said:**
> Open a terminal and enter sudo dpkg --configure -a and let us know what happens.

mmhmm looks like that did something =) thanks anything to get back synaptic manager is good news to me =D

---

### Post by vs8 on 2008-06-22
I got the same prob. I was trying to get more Compiz Fusion plugins from this tutorial:[http://mundogeek.net/archivos/2007/11/23/plugins-compiz-fusion/](http://mundogeek.net/archivos/2007/11/23/plugins-compiz-fusion/) But what I didn't know is that, that tutorial was made [COLOR="Red"]only[/COLOR] for Gutsy, and I'm running Hardy. I have some packages with unmet dependencies now. That command gave me this:

melvin@melvin-desktop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of dpkg-dev:
 dpkg-dev depends on libtimedate-perl; however:
  Package libtimedate-perl is not installed.
 dpkg-dev depends on patch (>= 2.2-1); however:
  Package patch is not installed.
dpkg: error processing dpkg-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.2 (>= 4.2.3-1); however:
  Package g++-4.2 is not installed.
dpkg: error processing g++ (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dpkg-dev
 g++

---

### Post by Midwest-Linux on 2008-06-22
> **KEE said:**
> ok i want to go in to synaptic manager but this keeps happening 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." 

and i cant access to synaptic manager or remove/download any programs...any ideas or suggestions ?

 Just out of curiosity, did you do any updates before this happened? I tried to add some programs today and had the same problems. Yesterday I did a update and it killed my wireless and I had to restore it. I wonder if these updates are responsible.

---

### Post by KEE on 2008-07-24
> **Midwest-Linux said:**
> Just out of curiosity, did you do any updates before this happened? I tried to add some programs today and had the same problems. Yesterday I did a update and it killed my wireless and I had to restore it. I wonder if these updates are responsible.
yeah i do... at the time i am not totally sure but i solved it with that code line thanks 4 your help =D

---

