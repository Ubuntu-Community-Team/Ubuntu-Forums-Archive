---
title: "Lucid : No /etc/init.d/samba anymore"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Omni-Vi on 2010-03-26
Hi,

after upgrading to Lucid I found the file /etc/init.d/samba is missing.

Does that mean I have to start/stop/restart snbd/nmbd seperatly now? Does anyone know why that is? Seems pretty inconvenient to me.

Thanks

---

### Post by dukje on 2010-03-26
samba is a upstart service now, start with "sudo service smbd start " and stop with "sudo service smbd stop" and yes, they're separate, so analog with nmbd. although i still have a smbd file in /etc/init.d/, but there it says: Symlink target for initscripts that have been converted to Upstart.

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

### Post by Omni-Vi on 2010-03-26
Yes, but why are there two files now, instead of only one as before?

---

