---
title: "Server wanted aswell"
date: 2005-10-31
forum: Installation &amp; Upgrades
---

### Post by ctcecil on 2005-10-31
At the beginning of the install I chose a regular install because I figured server wouldn't install gnome and xorg and everything else; is there anyway to install everything (apache, mysql, php support) without having to reinstall ubuntu?

---

### Post by Beggar on 2005-10-31
*edit* nm, answered the wrong question, apache is installed by default (apache2), sql can be installed with ```
sudo apt-get install mysql-server
``` and as far as php, try [this?]("http://ubuntuforums.org/showthread.php?t=44082&highlight=howto+php")

---

### Post by ctcecil on 2005-10-31
[QUOTE=Beggar]*edit* nm, answered the wrong question, apache is installed by default (apache2), sql can be installed with ```
sudo apt-get install mysql-server
``` and as far as php, try [this?]("http://ubuntuforums.org/showthread.php?t=44082&highlight=howto+php")[/QUOTE]

*edit* --
For all the searchers reading this:
Apache 2 is not installed by default.

This helped me out with everything I needed:
[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

