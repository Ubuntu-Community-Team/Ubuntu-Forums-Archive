---
title: "luasql error while giving 'make' command"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by uptime_guy on 2010-07-09
root@jaz-laptop:~/Downloads/luasql-2.1.1# make
gcc -O2 -Wall -Wmissing-prototypes -Wmissing-declarations -ansi -pedantic -I../compat/src -DUNIXODBC -I/usr/local/include -I/usr/local/include    -c -o src/ls_odbc.o src/ls_odbc.c
src/ls_odbc.c:21:17: [COLOR="Red"]**error: sql.h: No such file or directory**[/COLOR]
src/ls_odbc.c:22:22: **[COLOR="red"]error: sqltypes.h: No such file or directory[/COLOR]**

**I am getting this above error while trying to install luasql. I have already installed sql( sudo apt-get install mysql-server mysql-admin)**

---

