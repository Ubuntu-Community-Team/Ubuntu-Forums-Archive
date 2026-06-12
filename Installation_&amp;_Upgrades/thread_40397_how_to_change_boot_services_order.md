---
title: "how to change boot services order ?"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by xtrm on 2005-06-08
hi,
this is my fist post here. After a succesfull install everythings seems to work perfect. Nice job.
The only problem (at the moment ? :wink: ) i have is i've install the eagle-usb* for my dsl-modem. I asked to start it at boot. It works but it's launched after ntpdate in the boot process so ntpdate failed :-| . I'd like to know how to start adsl before ntpdate (or ntpdate after adsl :wink:
Thx.

---

### Post by defkewl on 2005-06-08
Install rcconf using apt-get:
$ apt-get install rcconf

Then run rcconf from the command line:
$ rcconf

Just checklist the service you want to run

---

