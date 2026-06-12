---
title: "Installing Mysql-server-4.1"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by just1122 on 2008-04-03
Hi, 

I'll start off by saying I'm new with Linux and I'm not that good with it. 

I need to install and older version of MySQL server (server 4.1). I attempt to install it using sudo apt-get install but the packagage cannot be found likely because its to old. 

I'm likely not capable of installing MySQl from source is there a simplier way that I can find and install the package possibly with snaptic or something?

Any help would be great. Thanks!

---

### Post by Fire_Chief on 2008-04-03
You could download the RPM version from MySQL.com then convert it using alien (converts RPMs to DEB files that can be natively installed).

Here's the MySQL package [http://dev.mysql.com/get/Downloads/MySQL-4.1/MySQL-server-4.1.22-0.glibc23.i386.rpm/from/pick#mirrors]("http://dev.mysql.com/get/Downloads/MySQL-4.1/MySQL-server-4.1.22-0.glibc23.i386.rpm/from/pick#mirrors")

And then install alien```
sudo apt-get install alien
```

Then convert the MySQL package```
alien --to-deb package.rpm
```
Then double click on the new .deb package to install (if opening through the GUI). 

Otherwise type ```
sudo gdebi MySQL-server-4.1.22-0.glibc23.i386.deb
```

Cheers!

---

