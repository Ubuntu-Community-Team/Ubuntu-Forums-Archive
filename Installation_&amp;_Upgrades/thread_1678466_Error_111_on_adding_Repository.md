---
title: "Error 111 on adding Repository"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by vigs on 2011-01-30
Whenever I try to add ANY repository using a command like this:-
```
sudo add-apt-repository ppa:libreoffice/ppa
```
I get an error like this:-
```
Error reading [https://launchpad.net/api/1.0/~libreoffice/+archive/ppa:](https://launchpad.net/api/1.0/~libreoffice/+archive/ppa:) <urlopen error [Errno 111] Connection refused>
```
What is the reason for this and what is the solution?
Note that I am behind the Institute Proxy server. update's and upgrade's run fine.

---

### Post by dino99 on 2011-01-30
dont use sudo, you need to open synaptic repo tab to add:

ppa:libreoffice/ppa

that it

---

### Post by vigs on 2011-01-30
> **dino99 said:**
> dont use sudo, you need to open synaptic repo tab to add:

ppa:libreoffice/ppa

that it
Could you describe in more detail please?
If u want me to go to Synaptic Package Manager->Settings->Repositories->Other SOftware->Add
then shouldn't the line look something like:-
deb [http://.](http://.).... maverick main

---

### Post by dino99 on 2011-01-30
> **vigs said:**
> Could you describe in more detail please?
If u want me to go to Synaptic Package Manager->Settings->Repositories->Other SOftware->Add
then shouldn't the line look something like:-
deb [http://.](http://.).... maverick main

simply do it as said, no need headache ;)

---

### Post by vigs on 2011-01-30
Thanks...solved

---

