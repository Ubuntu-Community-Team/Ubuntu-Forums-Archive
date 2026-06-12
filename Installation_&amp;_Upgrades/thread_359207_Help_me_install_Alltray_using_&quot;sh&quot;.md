---
title: "Help me install Alltray using &quot;sh&quot;"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by raffytaffy on 2007-02-11
Im tyring to install the program alltray. It comes as  alltray-0.69.x86.package

this is what the term is telling me

raf@Equinox:~$ sudo sh alltray-0.69.x86.package
alltray-0.69.x86.package: 29: Syntax error: "(" unexpected
raf@Equinox:~$ 


some info about my ubuntu. runing 6.10 - custom kernel
raf@Equinox:~$ uname -a
Linux Equinox 2.6.20 #1 SMP Sun Feb 11 17:01:31 EST 2007 i686 GNU/Linux

---

### Post by taurus on 2007-02-11
There is something wrong with line 29 of alltray-0.69.x86.package.  Look at it to see what's the problem.

```
more alltray-0.69.x86.package
```
Hit the space bar for the next 24 lines.

---

### Post by raffytaffy on 2007-02-11
the reason this scared me is bcse i think i have to install the nvidia driver next using the SH method since i just install custom kernel and imnot sure if synaptic or automatix will work installing the nvidia driver from ubuntu repositories

---

### Post by taurus on 2007-02-11
There is nothing to be scared.  Just follow the instructions and you should be fine.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by raffytaffy on 2007-02-11
im sorry for my stupid question...especially that i can do custom kernerl yet stuff like this perplexes me . ty for your quick response time

---

### Post by nalmeth on 2007-02-11
Alltray's website has a .deb for alltray. You should just use that to install it :)

---

### Post by jackrobinson on 2007-02-12
just do this:
```
wget http://asher256-repository.tuxfamily.org/dists/edgy/main/binary-i386/alltray_0.69-0ubuntu1_i386.deb
sudo dpkg -i alltray_0.69-0ubuntu1_i386.deb
```
if you see any errors, then do the following:
```
sudo apt-get -f install
```

---

