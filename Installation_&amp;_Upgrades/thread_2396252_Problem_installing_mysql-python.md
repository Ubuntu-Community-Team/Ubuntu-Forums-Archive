---
title: "Problem installing mysql-python"
date: 2018-07-12
forum: Installation &amp; Upgrades
---

### Post by rayrenz on 2018-07-12
I've recently switched to Ubuntu18.04 from Debian 9 and I've been trying to pip install mysql-python but it's failing. I've searched many forums and tried all solutions but I never got a working solution. I already have installed build-essential, python-dev, and many others I can't remember.

Collecting mysql-python
  Cache entry deserialization failed, entry ignored
  Cache entry deserialization failed, entry ignored
  Downloading [https://files.pythonhosted.org/packages/a5/e9/51b544da85a36a68debe7a7091f068d802fc515a3a202652828c73453cad/MySQL-python-1.2.5.zip](https://files.pythonhosted.org/packages/a5/e9/51b544da85a36a68debe7a7091f068d802fc515a3a202652828c73453cad/MySQL-python-1.2.5.zip) (108kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 112kB 397kB/s 
Building wheels for collected packages: mysql-python
  Running setup.py bdist_wheel for mysql-python ... error
  Complete output from command /usr/bin/python -u -c "import setuptools, tokenize;__file__='/tmp/pip-build-MSo8Sf/mysql-python/setup.py';f=getattr(tokenize, 'open', open)(__file__);code=f.read().replace('\r\n', '\n');f.close();exec(compile(code, __file__, 'exec'))" bdist_wheel -d /tmp/tmp1vCURcpip-wheel- --python-tag cp27:
  running bdist_wheel
  running build
  running build_py
  creating build
  creating build/lib.linux-x86_64-2.7
  copying _mysql_exceptions.py -> build/lib.linux-x86_64-2.7
  creating build/lib.linux-x86_64-2.7/MySQLdb
  copying MySQLdb/__init__.py -> build/lib.linux-x86_64-2.7/MySQLdb
  copying MySQLdb/converters.py -> build/lib.linux-x86_64-2.7/MySQLdb
  copying MySQLdb/connections.py -> build/lib.linux-x86_64-2.7/MySQLdb
  copying MySQLdb/cursors.py -> build/lib.linux-x86_64-2.7/MySQLdb
  copying MySQLdb/release.py -> build/lib.linux-x86_64-2.7/MySQLdb
  copying MySQLdb/times.py -> build/lib.linux-x86_64-2.7/MySQLdb
  creating build/lib.linux-x86_64-2.7/MySQLdb/constants
  copying MySQLdb/constants/__init__.py -> build/lib.linux-x86_64-2.7/MySQLdb/constants
  copying MySQLdb/constants/CR.py -> build/lib.linux-x86_64-2.7/MySQLdb/constants
  copying MySQLdb/constants/FIELD_TYPE.py -> build/lib.linux-x86_64-2.7/MySQLdb/constants
  copying MySQLdb/constants/ER.py -> build/lib.linux-x86_64-2.7/MySQLdb/constants
  copying MySQLdb/constants/FLAG.py -> build/lib.linux-x86_64-2.7/MySQLdb/constants
  copying MySQLdb/constants/REFRESH.py -> build/lib.linux-x86_64-2.7/MySQLdb/constants
  copying MySQLdb/constants/CLIENT.py -> build/lib.linux-x86_64-2.7/MySQLdb/constants
  running build_ext
  building '_mysql' extension
  creating build/temp.linux-x86_64-2.7
  x86_64-linux-gnu-gcc -pthread -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fno-strict-aliasing -Wdate-time -D_FORTIFY_SOURCE=2 -g -fdebug-prefix-map=/build/python2.7-nbjU53/python2.7-2.7.15~rc1=. -fstack-protector-strong -Wformat -Werror=format-security -fPIC -Dversion_info=(1,2,5,'final',1) -D__version__=1.2.5 -I/usr/include/mysql -I/usr/include/python2.7 -c _mysql.c -o build/temp.linux-x86_64-2.7/_mysql.o
  _mysql.c:44:10: fatal error: my_config.h: No such file or directory
   #include "my_config.h"
            ^~~~~~~~~~~~~
  compilation terminated.
  error: command 'x86_64-linux-gnu-gcc' failed with exit status 1
  
  ----------------------------------------
  Failed building wheel for mysql-python
  Running setup.py clean for mysql-python
Failed to build mysql-python
Installing collected packages: mysql-python
  Running setup.py install for mysql-python ... error
    Complete output from command /usr/bin/python -u -c "import setuptools, tokenize;__file__='/tmp/pip-build-MSo8Sf/mysql-python/setup.py';f=getattr(tokenize, 'open', open)(__file__);code=f.read().replace('\r\n', '\n');f.close();exec(compile(code, __file__, 'exec'))" install --record /tmp/pip-reOHsy-record/install-record.txt --single-version-externally-managed --compile --user --prefix=:
    running install
    running build
    running build_py
    creating build
    creating build/lib.linux-x86_64-2.7
    copying _mysql_exceptions.py -> build/lib.linux-x86_64-2.7
    creating build/lib.linux-x86_64-2.7/MySQLdb
    copying MySQLdb/__init__.py -> build/lib.linux-x86_64-2.7/MySQLdb
    copying MySQLdb/converters.py -> build/lib.linux-x86_64-2.7/MySQLdb
    copying MySQLdb/connections.py -> build/lib.linux-x86_64-2.7/MySQLdb
    copying MySQLdb/cursors.py -> build/lib.linux-x86_64-2.7/MySQLdb
    copying MySQLdb/release.py -> build/lib.linux-x86_64-2.7/MySQLdb
    copying MySQLdb/times.py -> build/lib.linux-x86_64-2.7/MySQLdb
    creating build/lib.linux-x86_64-2.7/MySQLdb/constants
    copying MySQLdb/constants/__init__.py -> build/lib.linux-x86_64-2.7/MySQLdb/constants
    copying MySQLdb/constants/CR.py -> build/lib.linux-x86_64-2.7/MySQLdb/constants
    copying MySQLdb/constants/FIELD_TYPE.py -> build/lib.linux-x86_64-2.7/MySQLdb/constants
    copying MySQLdb/constants/ER.py -> build/lib.linux-x86_64-2.7/MySQLdb/constants
    copying MySQLdb/constants/FLAG.py -> build/lib.linux-x86_64-2.7/MySQLdb/constants
    copying MySQLdb/constants/REFRESH.py -> build/lib.linux-x86_64-2.7/MySQLdb/constants
    copying MySQLdb/constants/CLIENT.py -> build/lib.linux-x86_64-2.7/MySQLdb/constants
    running build_ext
    building '_mysql' extension
    creating build/temp.linux-x86_64-2.7
    x86_64-linux-gnu-gcc -pthread -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fno-strict-aliasing -Wdate-time -D_FORTIFY_SOURCE=2 -g -fdebug-prefix-map=/build/python2.7-nbjU53/python2.7-2.7.15~rc1=. -fstack-protector-strong -Wformat -Werror=format-security -fPIC -Dversion_info=(1,2,5,'final',1) -D__version__=1.2.5 -I/usr/include/mysql -I/usr/include/python2.7 -c _mysql.c -o build/temp.linux-x86_64-2.7/_mysql.o
    _mysql.c:44:10: fatal error: my_config.h: No such file or directory
     #include "my_config.h"
              ^~~~~~~~~~~~~
    compilation terminated.
    error: command 'x86_64-linux-gnu-gcc' failed with exit status 1
    
    ----------------------------------------
Command "/usr/bin/python -u -c "import setuptools, tokenize;__file__='/tmp/pip-build-MSo8Sf/mysql-python/setup.py';f=getattr(tokenize, 'open', open)(__file__);code=f.read().replace('\r\n', '\n');f.close();exec(compile(code, __file__, 'exec'))" install --record /tmp/pip-reOHsy-record/install-record.txt --single-version-externally-managed --compile --user --prefix=" failed with error code 1 in /tmp/pip-build-MSo8Sf/mysql-python/

---

