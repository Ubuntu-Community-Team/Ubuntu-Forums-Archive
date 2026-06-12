---
title: "how to get phpmyadmin working on ubuntu 12"
date: 2012-08-03
forum: Installation &amp; Upgrades
---

### Post by cpama on 2012-08-03
hi there. i'm an ubuntu newbie. just installed it as a vm. trying to follow instructions on installing phpmyadmin. ([http://www.distrogeeks.com/how-to-install-phpmyadmin-in-ubuntu-12-04/](http://www.distrogeeks.com/how-to-install-phpmyadmin-in-ubuntu-12-04/))
But when i try to go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)
it fails with:
**Not Found**
 
The requested URL /phpmyadmin was not found on this server.
 
 
I tried to see if i have it installed by typing the command: 
 
```
dpkg --get-selections | grep php 
```
 
and i do see phpmyadmin in the result set. 
i tried to restart apache but that didn't make a difference either.  (By the way, apache is working because i made a test php page and ran it and it works just fine...)
 
any suggestions? 
 
Thanks.

---

### Post by bart.a on 2012-10-09
Try to reconfigure apache2.. make sure the astrix (*) is placed at the [ ] apache2 by pressing enter (I made that mistake myself)

**sudo dpkg-reconfigure -plow phpmyadmin**

If that doesn't work check out [this]("http://help.ubuntu.com/community/phpMyAdmin") website or try a complete reïnstall of LAMP.

---

### Post by bart.a on 2012-10-17
> **bart.a said:**
> Try to reconfigure apache2.. make sure the astrix (*) is placed at the [ ] apache2 by pressing enter (I made that mistake myself)

**sudo dpkg-reconfigure -plow phpmyadmin**

If that doesn't work check out [this]("http://help.ubuntu.com/community/phpMyAdmin") website or try a complete reïnstall of LAMP.
I accidentally typed "by pressing enter" it should be "by pressing spacebar"

---

