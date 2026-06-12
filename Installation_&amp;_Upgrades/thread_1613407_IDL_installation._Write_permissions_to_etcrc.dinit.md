---
title: "IDL installation. Write permissions to /etc/rc.d/init.d"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by tetris11 on 2010-11-04
Hi there, Im trying to install IDL v7.1 onto Ubuntu 10.04.

The installation goes pretty smoothly right up to the point where it tries to write to /etc/rc.d/init.d
I understand that ubuntu uses /etc/init.d, but I dont how to change the installation to point there. 
Is it wrong to just create a /etc/rc/init.d and hope everything works?

Edit: I just tried doing that, and then did chmod a+rwx /etc/rc/init.d, but when I try to install again I still get the error "You do not have permission to write to /etc/rc/init.d"
Edit2: No wait. That solved it. *slaps self* I created a rc/init.d instead of rc.d/init.d. Idiot.

---

