---
title: "lamp server pkg"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by rpatmullin on 2012-04-14
I am running 11.10 and would like to install apache2, php, mysql, .....    

sudo apt-get install [??????}

Can anyone fill in the blank here for me?

Thanks in advance for any input.

RPM

---

### Post by newbie-user on 2012-04-14
To see possible packages for installation:

apt-cache search php
apt-cache search apache
apt-cache search mysql

then

sudo apt-get install php5 apache2 mysql-server-5.1

or whatever packages you decide to install

You could also use tasksel: tasksel install lamp-server

---

### Post by rpatmullin on 2012-04-14
apt-cache search

that is what i needed.

Thanks

---

### Post by CharlesA on 2012-04-14
> **newbie-user said:**
> 
You could also use tasksel: tasksel install lamp-server

That's what I use, but if I remember right, tasksel isn't installed by default in 11.10.

---

### Post by agillator on 2012-04-14
No, you have to install tasksel first and then lamp-server. All very simple, though, and the best way to do it in my opinion.

---

