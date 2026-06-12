---
title: "Apache + bad user name ${APACHE_RUN_USER}"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by Vexiphne on 2010-07-05
I've just installed LAMP, but when I try to restart apache I get 
bad user name ${APACHE_RUN_USER}.

Tried to find a solution to it, but nothing worked for me. Could someone please help :)

---

### Post by phillw on 2010-07-05
Hi, how are you attempting to restart apache? Try ```
sudo /etc/init.d/apache2 restart
``` The error you are seeing can be caused by not using sudo, if that does not solve it, please post back.

Regards,

Phill.

---

