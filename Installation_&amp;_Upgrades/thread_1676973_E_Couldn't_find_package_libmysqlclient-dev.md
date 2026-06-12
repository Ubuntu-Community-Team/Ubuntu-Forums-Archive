---
title: "E: Couldn't find package libmysqlclient-dev"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by mechubu on 2011-01-28
@ubuntu:~/Downloads$ sudo apt-get install libmysqlclient16 libmysqlclient-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmysqlclient16 is already the newest version.
E: Couldn't find package libmysqlclient-dev

Somebody pls tell me wat to do

---

### Post by sikander3786 on 2011-01-28
Welcome to the forums :-)

Which version of Ubuntu is this?

Go to Software Center > Edit > Software Sources > Updates Tab and make sure Important Security Updates (lucid-security) and Recommended Updates (lucid-updates) are checked.

Now,

```
sudo apt-get update
```

```
sudo apt-get install libmysqlclient-dev
```

I think that is where these packages are coming from.

---

### Post by mechubu on 2011-02-01
Thank you so much :) that helped !

---

