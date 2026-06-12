---
title: "Custom Ubuntu installation"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by maxmin on 2005-10-25
I'm in need to perform large deployment of Ubuntu on >100 workstations. Hardware wise they're the same. They need to be on the same network, have Internet access but nothing else. Hardware is cheap and therefore not powerful at all- 5XX PIII machines. I've installed Ubuntu desktop but default installation puts/starts a lot of unnessesary services, like inet superserver, exim MTA to name a few. So my problems:
1. Get rid of unnessesary services at installation time
2. Simplify overall installation using the fact that hardware is going to be the same.
3. Possibly have ability to perform automated update in the future.

---

### Post by munkymonkjr on 2005-10-25
isn't there some kind of program that lets you build a custom debian disk? i am sure it can be extanded to ubuntu in some way.

---

### Post by bacc on 2005-10-26
This would be great, anyone know how to do something like this? Specifically, I'm also looking for something that would let you configure ubuntu with lots of control over what gets installed.

---

### Post by UbuWu on 2005-10-26
[https://wiki.ubuntu.com/InstallCDCustomizationHowTo](https://wiki.ubuntu.com/InstallCDCustomizationHowTo)

---

### Post by UbuWu on 2005-10-26
Also interesting: automatic installation:

[http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s06.html](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s06.html)

You could specify a postinstall script using kickstart to disable those services.

---

### Post by TOM_C_A_T on 2008-06-15
UbuWu's second link

archive.ubuntu

ate 404 !

:(

---

