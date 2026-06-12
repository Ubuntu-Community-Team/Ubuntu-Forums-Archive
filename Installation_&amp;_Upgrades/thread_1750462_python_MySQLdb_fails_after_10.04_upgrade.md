---
title: "python MySQLdb fails after 10.04 upgrade"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by dsa42 on 2011-05-05
I just upgraded 9.10 (karmic) to 10.04 (lucid).  This is 64 bit server edition.  

After the upgrade, python 2.5 is failing when using MySQLdb:

> 
> uname -m
x86_64
> python2.5
Python 2.5.4 (r254:67916, Jan 20 2010, 21:43:02)
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
[COLOR=#550055]>>> import MySQLdb
Traceback (most recent call last):
 File "<stdin>", line 1, in <module>
ImportError: No module named MySQLdb
[/COLOR]>>>
I _think_ that 2.6 was installed new in this upgrade.  It also fails:

> 
> python2.6
Python 2.6.4 (r264:75706, Dec  6 2009, 18:07:25)
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
[COLOR=#550055]>>> import MySQLdb
Traceback (most recent call last):
 File "<stdin>", line 1, in <module>
[/COLOR][COLOR=#550055]  File "build/bdist.linux-i686/egg/MySQLdb/__init__.py", line 19, in <module>
 File "build/bdist.linux-i686/egg/_mysql.py", line 7, in <module>
[/COLOR]  File "build/bdist.linux-i686/egg/_mysql.py", line 6, in __bootstrap__
ImportError: /root/.python-eggs/MySQL_python-1.2.3c1-py2.6-linux-i686.egg-tmp/_mysql.so:
wrong ELF class: ELFCLASS32
>>>
I found a note somewhere that this means the MySQLdb is 32 bit whereas python2.6 is 64 bit.  So I uninstalled and reinstalled

> 
apt-get remove python-mysqldb
apt-get install python-mysqldb
Now, I'm getting an error to which I can't find an answer:

> 
> python
Python 2.6.4 (r264:75706, Dec  6 2009, 18:07:25) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import MySQLdb
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "build/bdist.linux-i686/egg/MySQLdb/__init__.py", line 19, in <module>
  File "build/bdist.linux-i686/egg/_mysql.py", line 7, in <module>
  File "build/bdist.linux-i686/egg/_mysql.py", line 3, in __bootstrap__
  File "/usr/local/lib/python2.6/site-packages/setuptools-0.6c11-py2.6.egg/pkg_resources.py", line 2594, in <module>
  File "/usr/local/lib/python2.6/site-packages/setuptools-0.6c11-py2.6.egg/pkg_resources.py", line 425, in __init__
  File "/usr/local/lib/python2.6/site-packages/setuptools-0.6c11-py2.6.egg/pkg_resources.py", line 440, in add_entry
  File "/usr/local/lib/python2.6/site-packages/setuptools-0.6c11-py2.6.egg/pkg_resources.py", line 1688, in find_on_path
  File "/usr/local/lib/python2.6/site-packages/setuptools-0.6c11-py2.6.egg/pkg_resources.py", line 1835, in _normalize_cached
  File "/usr/local/lib/python2.6/site-packages/setuptools-0.6c11-py2.6.egg/pkg_resources.py", line 1829, in normalize_path
  File "/usr/local/lib/python2.6/posixpath.py", line 365, in realpath
    return abspath(filename)
  File "/usr/local/lib/python2.6/posixpath.py", line 338, in abspath
    path = join(os.getcwd(), path)
OSError: [Errno 2] No such file or directory
>>> 


---

