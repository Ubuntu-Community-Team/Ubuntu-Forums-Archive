---
title: "New to Ubuntu"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by fredanthony on 2006-07-11
Hey guys, thanks in advance. I am not gonna act like I am an expert on any of this lol, I am new to Ubuntu (was all Windows) and so I am trying to get use to all this. Very nice stuff, got the web server and vsftpd setup and working. One thing I am trying to setup a mail server, when I run: 
> $apt-get install courier-authmysql

I get:
> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package courier-authmysql

Any clues on this?? Thanks.

Fred.

---

### Post by bojzi on 2006-07-11
As I see in Synaptic that package is located in the Universe repository.
Do you have the Universe and Multiverse repositories enabled?
If not, here ([https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)) is a great guide on how to enable them.

---

### Post by aysiu on 2006-07-11
You need the Universe repository for that package.

1. [Enable extra repositories](http://www.psychocats.net/ubuntu/sources).

2. ```
sudo aptitude update
sudo aptitude install courier-authmysql
```

---

### Post by fredanthony on 2006-07-11
wow that was fast! If I could, could you explain the diffence with apt-get and aptitude? Thanks.

---

### Post by aysiu on 2006-07-11
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

