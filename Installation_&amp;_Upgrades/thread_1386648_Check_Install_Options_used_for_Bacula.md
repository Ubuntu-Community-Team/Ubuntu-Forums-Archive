---
title: "Check Install Options used for Bacula"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by ross_gailer on 2010-01-20
I am running Ubuntu Server 9.10. I have installed MySQL 5.1 using apt-get, then installed Bacula using apt-get. The version of Bacula supplied via this method is 2.4.4. I need to use the Exchange plugin for Bacula and this only comes with 3.0.0 or above, preferably 3.0.3. Is it possible to get a listing from somewhere that will list the config options used for the Bacula install so that I can try an upgrade? Options that I really need include the sbindir, sysconfigdir, mandir (I think this is /usr/doc/bacula), pid-dir (/var/run/bacula?), subsys-dir, and working-dir.

Any assistance greatly appreciated.

---

### Post by ross_gailer on 2010-03-31
I have been able to sucessfully upgrade my Bacula install to 5.1 and it is working well, including the Exchange plugin.

Thanks

---

