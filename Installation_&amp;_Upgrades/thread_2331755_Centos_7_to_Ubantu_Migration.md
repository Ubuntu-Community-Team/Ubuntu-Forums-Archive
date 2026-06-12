---
title: "Centos 7 to Ubantu Migration"
date: 2016-07-25
forum: Installation &amp; Upgrades
---

### Post by samundri on 2016-07-25
[COLOR=#000000]One of our client wants us to migrate his business rating website from centos 7 to ubantu.
We are the company who developed this website for him, our company mostly works on centos and debian, we do not have much expertise in ubuntu.
I am here to know if any one can guide me of known hurdles in migration.
Here is websites technological detail. Server: Nginx, php-fpm 5 Database: mariadb domain name: 3ci.in cms: joomla 3
It will be helpful if i can get some compatibility matrix and some migration guide.[/COLOR]

---

### Post by SeijiSensei on 2016-07-25
Ubuntu runs all the same software you mention.  Migration would require dumping the database and recreating it on the Ubuntu box, then installing the software you need.  If you are comfortable with Debian, you shouldn't see much difference between it and Ubuntu, since the latter is a Debian derivative.

Personally I'd tell the client that RedHat and CentOS are the dominant professional choices for Linux servers.  I only run Ubuntu on desktops; I run CentOS on servers.

---

