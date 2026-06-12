---
title: "Desktop and Server Install"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by Daedalus81 on 2006-09-27
I installed Ubuntu using the server version, but i'm really interested in having the desktop (Gnome/KDE) (for editing and misc) and LAMP running on the same machine.  Is this possible while still using Ubuntu's automatic config?  If so, how?  

Thanks!
-Newbie

---

### Post by cammj on 2006-09-27
Well, if you want to use it as a desktop you probably should have installed using the normal CD's? Then you could install the LAMP packages using the apt-get command or synaptic.

---

### Post by Daedalus81 on 2006-09-27
I'll give it a shot.  I was just worried about botching the LAMP install.

---

### Post by cammj on 2006-09-27
its quite simple, and everything fits together quite well..

i think these are the correct commands.. off the top of my head

apt-get install apache2
apt-get install php5
apt-get install mysql-server

then the best way to configure it would probably be using something like phpmyadmin.

enjoy!

---

### Post by Daedalus81 on 2006-09-27
> **cammj said:**
> its quite simple, and everything fits together quite well..

i think these are the correct commands.. off the top of my head

apt-get install apache2
apt-get install php5
apt-get install mysql-server

then the best way to configure it would probably be using something like phpmyadmin.

enjoy!

I'll give it a shot! Thanks guys. :)

---

