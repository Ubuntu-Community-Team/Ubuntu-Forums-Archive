---
title: "How do i install an old MYSQL on my Ubuntu server?"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by Mr-Heier on 2007-05-15
I know the command 'sudo apt-get install  mysql-server' but that install 5.0. I need to install 4.0.

Any ideas?

Marius

---

### Post by caffienefree on 2007-05-15
You can download 4.1 packages from here.

[http://dev.mysql.com/downloads/mysql/4.1.html](http://dev.mysql.com/downloads/mysql/4.1.html)

---

### Post by Mr-Heier on 2007-05-15
> **caffienefree said:**
> You can download 4.1 packages from here.

[http://dev.mysql.com/downloads/mysql/4.1.html](http://dev.mysql.com/downloads/mysql/4.1.html)

Thanks! But..

What package do i use?

Marius

---

### Post by caffienefree on 2007-05-15
Download the source (tar.gz), then review this process. ([http://community.unixcities.com/node/2](http://community.unixcities.com/node/2))

You'll need to replace the package in the how to mysql-3.23-51.tar.gz, with whatever the name/location of your new source package is.

---

