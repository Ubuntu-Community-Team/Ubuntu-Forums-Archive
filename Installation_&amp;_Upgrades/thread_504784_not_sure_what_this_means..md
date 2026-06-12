---
title: "not sure what this means."
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by rohizzle121 on 2007-07-19
ok so i was trying to add the universal resp. and i get this > E: Type '-e' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


---

### Post by Rui Pais on 2007-07-19
hi,
your sources.list had a bad line.
Delete line 1, or better post it here, for we can check syntax.

---

### Post by rohizzle121 on 2007-07-19
how do i post it.

---

### Post by Waappu on 2007-07-19
Hi

Open terminal and type```
gedit /etc/apt/sources.list
```then copy content and paste it here

---

### Post by rohizzle121 on 2007-07-19
-e deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

---

### Post by Rui Pais on 2007-07-19
hi, 
a little confuse... 

To edit the file you will need:
```
gksudo gedit /etc/apt/sources.list
```
delete the "-e" from 1st line and delete the line:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main
i assume you are using Ubuntu Dapper. 
Don't mix repos (that line is from Feisty) or you will hit problems sooner or later.

Save and should be ok :)

---

### Post by rohizzle121 on 2007-07-19
i am using feisty, so what should i change?

---

### Post by Rui Pais on 2007-07-19
> **rohizzle121 said:**
> i am using feisty, so what should i change?

well, then you need to change all the words 'dapper' to 'feisty' :)

You can use this site to generate a sources.list complete and optimized for your location:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

hth

---

