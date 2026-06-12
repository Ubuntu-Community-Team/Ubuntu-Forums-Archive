---
title: "apt-get install not working on Ubuntu 7.10"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by tejasrsuthar on 2007-12-04
hi, friends (Ubuntu 7.10)

after installing when i update it with sudo apt-get update it gives me this kind of situation.

 sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Reading package lists... Done

and when i use sudo apt-get install apache2 then i got,

sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2

what should be the problem with my system.????:(
thanks in advance...for your rply... ist urgent plzzzzz.

---

### Post by jbt on 2007-12-04
> **tejasrsuthar said:**
> hi, friends (Ubuntu 7.10)

after installing when i update it with sudo apt-get update it gives me this kind of situation.

 and when i use sudo apt-get install apache2 then i got,

sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2



Odd.
Are you sure you have got the standard software sources installed ?
Did you install from CD ?
Do you have the right CD in the drive ?

You could always download it  and install manually using dpkg
[http://packages.ubuntu.com/gutsy/web/apache2](http://packages.ubuntu.com/gutsy/web/apache2)

Regards
JohnT

---

### Post by tejasrsuthar on 2007-12-04
i 've install it from original shipped Ubuntu7.10 cd from Netherlands.

---

### Post by psusi on 2007-12-04
You don't appear to have any repositories enabled except the cd.  Did you clobber your /etc/apt/sources.list?

---

