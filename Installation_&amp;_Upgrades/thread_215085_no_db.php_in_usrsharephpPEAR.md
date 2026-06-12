---
title: "no db.php in //usr/share/php/PEAR ?"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by fredanthony on 2006-07-13
Hey guys I am having a small issue with some software, I keeping getting an issue with db.php, 

> Failed opening 'DB.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear')

When I look there is no db.php in /usr/share/php and I have no /usr/share/pear. I have done apt-get install php-pear and nothing changes. Any ideas? Thanks.

---

### Post by fredanthony on 2006-07-13
Ok, I got it to work. I found in the software there was a DB.php so I copied it over..

---

### Post by jjf on 2006-07-14
I'm having similar trouble, but don't have a copy of DB.php in the software I'm trying to install.

I've installed the **php-pear** package.

phpinfo() tells me that the include paths are /usr/share/pear and /usr/share/php, but like fredanthony, I don't have a /usr/share/pear directory.  I **do** have a /usr/share/php/PEAR.  Problem is, *it* doesn't have a DB.php file in it either.

Any help would be greatly appreciated.

---

### Post by vkeven on 2006-07-28
I found the problem

apt-get install php-db

---

### Post by Compactman on 2008-02-24
okay I have tried everything in this article but I still don't have a /usr/share/pear  directory

My phpinfo says its setup for it but I don't know what to apt-get so that the directory is created and populated.

---

