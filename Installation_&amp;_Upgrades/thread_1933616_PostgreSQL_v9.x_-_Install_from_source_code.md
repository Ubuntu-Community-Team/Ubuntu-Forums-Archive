---
title: "PostgreSQL v9.x - Install from source code"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by alex.mobigo on 2012-02-29
I think is wrong forum, i will try some development forum, dont know how to switch this to the correct forum.

I need to compile and install postgresql from source code in a fresh install, no use of **apt-ge**t or **dpkg** and no postgres user created yet.
Compiling and installing is already done, i need those script to start and stop the postgresql service and the creating of postgres user the exactly same way ubuntu does. Please not a adduser command to add a postgres user.
I downloaded the 8.4 sources from ubuntu but did not find any of those pre installation or post installation scripts apt-get run during a normal apt-get install.
Does any one knows how can i add the postgres user the same way apt-get does on install and the services to start and stop and also run from boot? Or where to find it?

---

### Post by alex.mobigo on 2012-03-01
argh, the scripts needed are in **postgresql-common** !!

---

