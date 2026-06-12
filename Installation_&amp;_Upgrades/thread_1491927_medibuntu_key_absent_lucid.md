---
title: "medibuntu key absent lucid"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by jon zendatta on 2010-05-24
I'm having the following problem importing medibuntu key. Any idea's short of installing each package seperately.

[PHP]j@j-laptop:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2010-05-24 22:55:59--  http://www.medibuntu.org/sources.list.d/lucid.list
Resolving www.medibuntu.org... 1.0.0.0
Connecting to www.medibuntu.org|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--2010-05-24 22:56:21--  (try: 2)  http://www.medibuntu.org/sources.list.d/lucid.list
Connecting to www.medibuntu.org|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--2010-05-24 22:56:44--  (try: 3)  http://www.medibuntu.org/sources.list.d/lucid.list
Connecting to www.medibuntu.org|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--2010-05-24 22:57:08--  (try: 4)  http://www.medibuntu.org/sources.list.d/lucid.list
Connecting to www.medibuntu.org|1.0.0.0|:80... failed: Connection timed out.
Retrying.
[/PHP]

---

### Post by ajgreeny on 2010-05-24
Try:-
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```which seems a bit different to the commands you used.

This comes from the medibuntu website, itself.

---

### Post by dino99 on 2010-05-24
gksudo gedit /etc/apt/sources.list

choose one below:

mirror=http://packages.medibuntu.org
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

mirror=http://mirrors.ucr.ac.cr/medibuntu
deb [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free
deb-src [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free

mirror=http://mirror.oscc.org.my/medibuntu
deb [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) lucid free non-free
deb-src [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) lucid free non-free

mirror=ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu
deb [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free
deb-src [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free

key:
wget -q -O- mirror/medibuntu-key.gpg | sudo apt-key add -
where "mirror" is the one chosen

sudo aptitude update

---

### Post by jon zendatta on 2010-05-24
thanks got it sorted now:KS

---

