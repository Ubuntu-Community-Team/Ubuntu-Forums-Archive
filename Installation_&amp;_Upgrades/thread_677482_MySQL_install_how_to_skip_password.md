---
title: "MySQL install how to skip password"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by nemo7467 on 2008-01-24
Hello, I'm using Slicehost for my hosting and they have a preinstalled image of Ubuntu 7.10 that I use.

To get to the point, I created a shell script that automatically installs a bunch of packages.  When I run this command, it stops my (automatic) installation and asks for MySQL's root user password (in some weird blue screen):

sudo apt-get install -y mysql-server libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common mysql-server-5.0

is there some way to skip that screen?

---

### Post by ciciliati on 2008-03-13
Quick & Dirty:

Before invoking "apt-get install mysql-server", execute:

```
echo "mysql-server mysql-server/root_password select" | sudo debconf-set-selections 

```

---

