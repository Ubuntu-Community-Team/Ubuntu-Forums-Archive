---
title: "reinstall Ubuntu and backup deb packages"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by manward on 2010-05-21
hi

after my[ laptop sound issue]("http://ubuntuforums.org/showthread.php?t=1489352") , i decide reinstalling ubuntu 10.04 ,but i have many 

packages

installed on it and can't download these packages again.can i backup my deb packages and 

import into fresh ubuntu ? 


should i backup var/cache/apt/archives folder ? this solution work on Ubuntu 10.04 ?

plz help me 

thanks in advance

---

### Post by ninjageek on 2010-06-03
yep, just paste your old archives folder into the new and use these commandsn to reinstall everything:

cd /var/cache/apt/archives/
sudo dpkg --install *deb

---

### Post by masque7 on 2010-07-12
If you did that, how is it going to know what packages to install first? i.e. dependencies

---

### Post by Ratul Saha on 2010-08-28
Check it out, if you are still interested.
[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

---

