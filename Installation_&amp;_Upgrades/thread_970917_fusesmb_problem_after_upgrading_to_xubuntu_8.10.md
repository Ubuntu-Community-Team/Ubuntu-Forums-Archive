---
title: "fusesmb problem after upgrading to xubuntu 8.10"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by benma on 2008-11-04
Hello.
After upgrading to 8.10 my samba mount crashes after several seconds. trying reaccess the mount gives: Transport endpoint is not connected.    umount and running fusesmb /home/.../network mounts again for several seconds and then crashes again. 

Please help!

p.s. i found similar problem at: [http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu&page=14](http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu&page=14)


Never had this problem in hardy.

running ls -l gives:

ls: cannot access network: **Transport endpoint is not connected**
total 48
.
.censored
.
d????????? ? ? ? ? ? network
.
.censored

while running sudo ls -l gives:

ls: cannot access network: **Permission denied**
total 48
.
.censored
.
d????????? ? ? ? ? ? network
.
.censored

---

### Post by benma on 2008-11-04
It seems it's a Thunar problem, because if i don't open Thunar and browse /media/network from CLI, nothing happens - fusesmb stays connected.

---

### Post by benma on 2008-11-04
It's an even Debian Lenny problem inherited by ubuntu in multiverse/uniberse.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572)


SOLUTION:
Untill fusesmb newest version is fixed:
In the manual don't use fusesmb. install smbnetfs package instead.
All the other directives are fine.

---

