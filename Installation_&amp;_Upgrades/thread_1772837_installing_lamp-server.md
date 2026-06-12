---
title: "installing lamp-server"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by Freakyjay on 2011-06-01
Hi people, care to admit am still new to ubuntu(9.04). i want to use OpenEMR 3.2. but am advised to install lamp-server 1st. 

       i used the following comands

               root@secunets-desktop:/#  apt-get install lamp-server


and i get this


                 E: couldn't find package lamp-server

i've tried installing phpmyadmin and other modules but get almost the same error.

i have installed mysq, apache2, and drupal, the apache is running but that is all i get. please if anyone knows what i should do please help.


index of /

_Name_ _Last_ _Modified_ _Size_ _Description_

_______________________________
_______________________________

Apache/2.2.11 (Ubuntu) Server at localhost Port 80

that is all i get when i go to [http://localhost/phpMyadmin?scripts/setup.php](http://localhost/phpMyadmin?scripts/setup.php)

thanx in advance

-jeff

---

### Post by mörgæs on 2011-06-01
Hi, welcome to the fora. 

First I would recommend a fresh install of Ubuntu 10.04 or 10.10. Your present release has not received bug fixes for more than half a year.
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)



After this, here is how to do:
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)


Don't create a root account; just use your normal user.

---

