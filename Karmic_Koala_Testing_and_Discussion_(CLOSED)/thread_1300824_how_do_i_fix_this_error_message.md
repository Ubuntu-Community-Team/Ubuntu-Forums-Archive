---
title: "how do i fix this error message"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2009-10-25
note i need to fix because i cant open the spm

here is message
ray@ray-desktop ~ $ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package ubuntu-tweak needs to be reinstalled, but I can't find an archive for it.
ray@ray-desktop ~ $

---

### Post by Rinzwind on 2009-10-25
remove that package and then check if it was renamed.

---

### Post by rburkartjo on 2009-10-25
rin cant remove

---

### Post by ktp on 2009-10-25
maybe this will help

[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

---

### Post by dino99 on 2009-10-25
can you access it with software center ?
what's the return of find ? or install -f ?

---

### Post by vinutux on 2009-10-25
disable third party repos before update

---

### Post by rburkartjo on 2009-10-25
i cant access any repos

---

### Post by vinutux on 2009-10-25
sorry i mis understood a bit...

Your problem is you are installed ubuntu tweak and apt can't find a repo for new version of it...

Threre is two ways to fixing this 

1. un install ubuntu tweak

2. add a repo for ubuntu tweaks 

Here is ubuntu tweak ppa (repo) **[https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa]("https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa")**

add this ppa may helps you.....

---

### Post by rburkartjo on 2009-10-25
thank you all i sort of have this fixed i can access the spm which is what i want but when i click on tweak nothing happens. any ideas???

---

