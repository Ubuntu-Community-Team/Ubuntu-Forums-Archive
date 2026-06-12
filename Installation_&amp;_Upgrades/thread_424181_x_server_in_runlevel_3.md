---
title: "x server in runlevel 3"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by m-productions on 2007-04-26
ok  we are trying to install drivers for our e0geforce 7600 card... we have the linux drivers, however it says that x server can not be running.  so i type this in

sudo init 1

bang works fine i then run the file

sh /home/deportment/Desktop/driver.run

opens up and I get an error saying that it needs to be un runlevel 3 not runlevel 1 and it tells me to do  telinit 3, well i do this, but it makes the x server turn back on... any help please, we are linux noobs.

---

### Post by zvacet on 2007-04-26
```
sudo init 3
```

---

### Post by m-productions on 2007-04-26
This was the first thing i tried to do, however this does not disable x server like init 1 does ...in fact, init 3 does nothing at all when I do it in the noraml terminal, however if I type init 1 then let it go into the black screen, then type init 3, it load ubuntu back up to normal.....

---

### Post by zvacet on 2007-04-27
What are you doing in run level 1 anyway?I think default run level is 2 and if you have problem with xserver 

[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

