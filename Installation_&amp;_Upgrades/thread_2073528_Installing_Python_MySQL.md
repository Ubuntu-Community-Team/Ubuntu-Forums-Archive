---
title: "Installing Python MySQL"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by bencouve on 2012-10-19
Hello !!!

I am trying to install Python MySQL

Followed instructions from this site
[http://crucial-systems.com/installing-mysqldb-ubuntu-mysql-python](http://crucial-systems.com/installing-mysqldb-ubuntu-mysql-python)

and get as far as this
python setup.py build

when I get this error
start of build
---------------------------------------------------------------------------------------------------------------
python setup.py build
running build
running build_py
copying MySQLdb/release.py -> build/lib.linux-x86_64-2.7/MySQLdb
running build_ext
building '_mysql' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -Dversion_info=(1,2,4,'beta',4) -D__version__=1.2.4b4 -I/usr/include/mysql -I/usr/include/python2.7 -c _mysql.c -o build/temp.linux-x86_64-2.7/_mysql.o -DBIG_JOINS=1 -fno-strict-aliasing -g
_mysql.c:29:20: fatal error: Python.h: No such file or directory
compilation terminated.
error: command 'gcc' failed with exit status 1

------------------------------------------------------------------------------------------------------------------------------
End of build

Can anyone advise on this. The error appear to be generated from 
_mysql.c:29:20: fatal error: Python.h: No such file or directory
but not sure what is causing it.

---

### Post by Cheesemill on 2012-10-19
The information on that page is outdated and not needed anymore.
To install the Python MySQL bindings on current versions of Ubuntu you can just do:
```
sudo apt-get install python-mysqldb
```

---

### Post by bencouve on 2012-10-20
Thanks for your help cheesemill, it is much appreciated. That has worked, as you suspected it would ...:guitar:

---

