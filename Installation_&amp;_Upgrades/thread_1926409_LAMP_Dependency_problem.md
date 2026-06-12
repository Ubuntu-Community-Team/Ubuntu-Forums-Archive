---
title: "LAMP: Dependency problem"
date: 2012-02-16
forum: Installation &amp; Upgrades
---

### Post by aahk on 2012-02-16
i am installing LAMP. i have opened terminal and typed 
sudo apt-get install libapache2-mod-auth-mysql php5-mysql apache2 php5 libapache2-mod-php5 mysql-server

after this, i m getting this error...
The following packages have unmet dependencies:
  mysql-server: Depends: mysql-server-5.5 but it is not going to be installed
E: Broken packages

now tell me please that how will i fix this problem..thank you so much

Sincerely
A new user of ubuntu

---

### Post by jerrrys on 2012-02-16
I know nothing about LAMP so Im not going there, but to try to fix broken packages:

sudo apt-get install -f

---

### Post by mörgæs on 2012-02-16
Hi, welcome to the fora.

The safe approach is to install LAMP like this:
[http://ubuntuforums.org/showpost.php?p=11658107&postcount=4](http://ubuntuforums.org/showpost.php?p=11658107&postcount=4)

I would uninstall the packages you have already added and install through tasksel afterwards.

---

