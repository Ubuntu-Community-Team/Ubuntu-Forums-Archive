---
title: "Change software sources command line ?"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by bonevg on 2010-06-09
Is there a complete mirror list you can choose from the command line.
There is good way doing it from Administration > Software Sources.
However.. if you don't have X.. is there an easy way to choose between different sources(mirrors) without editing the sources.lst manually, but choosing for example main mirror or some other faster one let's say in your region?

---

### Post by dino99 on 2010-06-09
choose the server into synaptic

---

### Post by bonevg on 2010-06-09
> **dino99 said:**
> choose the server into synaptic

synaptic uses X
```
apt-get install synaptic
```
advices me to install x11-common and whole bunch of other packets as dependencies

My question was if there is a way to do it without GUI but just from your shell.
Unless there is non-graphic kind with curses of synaptic ? Is it ?

---

### Post by oldos2er on 2010-06-09
> **bonevg said:**
> Unless there is non-graphic kind with curses of synaptic ? Is it ?

Yes, aptitude. Use the nano editor to modify repositories.

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/)

---

