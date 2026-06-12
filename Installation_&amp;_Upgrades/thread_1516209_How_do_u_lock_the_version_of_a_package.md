---
title: "How do u lock the version of a package"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by perro68 on 2010-06-23
WHEN U WANT TO UPGRADE THE ENTIRE DISTRO

I want to lock the version of Java i am using now

when i upgrade to 9.1 and than one to 10.04

I have an applet that only seems to properly work when 9.04 is loaded

if i do a clean install of lucid it does not work ...it only seems to work with Jaunty

how can i upgrade to 9.1 but keep everything associated with java the same?

---

### Post by dino99 on 2010-06-23
not so easy and will drop you into more troubles than this little applet (dependencies issues), better to search for an uptodated clone

but you can lock any package into synaptic selecting package menu

---

### Post by jeremyswalker on 2010-06-23
Which Java are you using? I find that 99.99% of any problems I have running applets comes from using the open-source version. A quick switch to the sun-java6* version fixes most of my issues.

---

### Post by dino99 on 2010-06-23
> **jeremyswalker said:**
> Which Java are you using? I find that 99.99% of any problems I have running applets comes from using the open-source version. A quick switch to the sun-java6* version fixes most of my issues.

you are right :p

---

### Post by perro68 on 2010-06-23
how do i ensure i am using the correct version of java u guys are suggesting

---

### Post by jeremyswalker on 2010-06-23
You should type ```
about:plugins
``` in the address bar of your browser. If you see anything relating to "IcedTea" or "openjdk", then you are using the open-source plugin.

---

