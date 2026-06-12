---
title: "Ubuntu server lamp install script"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by aktxyz on 2007-05-16
At install time, Ubuntu server asks if you want to install a LAMP stack.

Does anyone know where this script is located on the CD (or in the source tree).

I'd like to be able to run the same LAMP script sometime after install time...

-- Thanks !

---

### Post by az on 2007-05-16
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server


If you are running Edgy or fiesty, run

sudo tasksel

and pick LAMP.

---

### Post by aktxyz on 2007-05-16
Yeah ! that's exactly what I was looking for 

sudo tasksel

Awesome and thanks !

---

