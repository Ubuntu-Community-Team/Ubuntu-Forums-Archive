---
title: "Python upgrade to 3.4"
date: 2014-10-05
forum: Installation &amp; Upgrades
---

### Post by yahia3 on 2014-10-05
Hi All,

Once I tried make the default python version to 3.4 on ubuntu 14.04, I am unable to open software-center, it displays the following error message:

```
File "/usr/bin/software-center", line 140
    print time.time()
             ^
SyntaxError: invalid syntax

```
Moreover, I am unable to install anything. For example, when I am trying to run ```
sudo apt-get install -f

```, the following exception is thrown:

```
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  python-colorama python-distlib python-requests
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 91 not upgraded.
43 not fully installed or removed.
Need to get 0 B/129 kB of archives.
After this operation, 0 B of additional disk space will be used.
Setting up python-decorator (3.4.0-2build1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-decorator (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-simplegeneric (0.8.1-1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-simplegeneric (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ipython:
 ipython depends on python-decorator; however:
  Package python-decorator is not configured yet.
 ipython depends on python-simplegeneric; however:
  Package python-simplegeneric is not configured yet.


dpkg: error processing package ipython (--configure):
 dependency problems - leaving unconfigured
Setting up python-markupsafe (0.18-1build2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-markupsafe (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-jinj
dpkg: error processing package python-jinja2 (--configure):
 dependency problems - leaving unconfigured
Setting up python-tornado (3.1.1-1ubuntu2) ...
No apport report written because MaxReports is reached already
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-tornado (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-zmq (14.0.1-1build2) ...
 is reached already
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-zmq (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of ipython-notebook:
 ipython-notebook depends on ipython (= 1.2.1-2); however:
  Package ipython is not configured yet.
 ipython-notebook depends on python-jinja2; however:
  Package python-jinja2 is not configured yet.
 ipython-notebook depends on python-tornado (>= 2.1.0); however:
  Package python-tornado is not configured yet.
 ipython-notebook depends on python-zmq (>= 2.1.11); however:
  Package python-zmq is not configured yet.


dpkg: error processing package ipython-notebook (--configure):
 dependency problems - leaving unconfigured
Setting up python-antlr (2.7.7+dfsg-5) ...
No apport report written because MaxReports is reached already
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-antlr (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-bs4 (4.2.1-1ubuntu2) ...
 is reached already
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-bs4 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached alreadySetting up python-colorama (0.2.5-0.1ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-colorama (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-cvxopt (1.1.4-1.2) ...


Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-cvxopt (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-dateutil (1.5+dfsg-1ubuntu1) ...
hed already
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-dateutil (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-distlib (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached alreadySetting up python-html5lib (0.999-2) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-html5lib (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-joblib (0.8.3-1~nd14.04+1) ...
No apport report written because MaxReports is reached already
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-joblib (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-pyparsing (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached alreadySetting up python-tz (2012c-1build1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-tz (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-numpy (1:1.8.2-0ubuntu0.1) ...
ached already
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-numpy (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
dpkg: error processing package python-matplotlib (--configure):
 dependency problems - leaving unconfigured
Setting up python-mysqldb (1.2.3-2ubuntu1) ...
No apport report written because MaxReports is reached already
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-mysqldb (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-nose (1.3.1-2) ...


Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-nose (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of python-numexpr:
 python-numexpr depends on python-numpy (>= 1:1.8.0); however:
  Package python-numpy is not configured yet.
 python-numexpr depends on python-numpy-abi9; however:
  Package python-numpy-abi9 is not installed.
  Package python-numpy which provides python-numpy-abi9 is not configured yet.


dpkg: error processing package python-numexpr (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached alreadydpkg: dependency problems prevent configuration of python-pandas-lib:
 python-pandas-lib depends on python-numpy (>= 1:1.8.0); however:
  Package python-numpy is not configured yet.
 python-pandas-lib depends on python-numpy-abi9; however:
  Package python-numpy-abi9 is not installed.
  Package python-numpy which provides python-numpy-abi9 is not configured yet.


dpkg: error processing package python-pandas-lib (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of python-pandas:
 python-pandas depends on python-dateutil; however:
  Package python-dateutil is not configured yet.
 python-pandas depends on python-tz; however:
  Package python-tz is not configured yet.
 python-pandas depends on python-numpy (>= 1:1.6~); however:
  Package python-numpy is not configured yet.
 python-pandas depends on python-pandas-lib (>= 0.14.1-1~nd14.04+1); however:
  Package python-pandas-lib is not configured yet.


dpkg: error processing package python-pandas (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: error processing package python-patsy (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-urllib3 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached alreadydpkg: dependency problems prevent configuration of python-requests:
 python-requests depends on python-urllib3 (>= 1.7.1); however:
  Package python-urllib3 is not configured yet.


dpkg: error processing package python-requests (--configure):
 dependency problems - leaving unconfigured
Setting up python-setuptools (3.3-1ubuntu1) ...
No apport report written because MaxReports is reached already
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-setuptools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-simplejson (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of python-sklearn-lib:
 python-sklearn-lib depends on python-numpy (>= 1:1.8.0); however:
  Package python-numpy is not configured yet.
 python-sklearn-lib depends on python-numpy-abi9; however:
  Package python-numpy-abi9 is not installed.
  Package python-numpy which provides python-numpy-abi9 is not configured yet.


dpkg: error processing package python-sklearn-lib (--configure):
 dependency problems - leaving unconfigured
Setting up python-sympy (0.7.4.1-1) ...
No apport report written because MaxReports is reached already
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-sympy (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached alreadyes-lib:
 python-tables-lib depends on python-numpy (>= 1:1.8.0); however:
  Package python-numpy is not configured yet.
 python-tables-lib depends on python-numpy-abi9; however:
  Package python-numpy-abi9 is not installed.
  Package python-numpy which provides python-numpy-abi9 is not configured yet.


dpkg: error processing package python-tables-lib (--configure):
 dependency problems - leaving unconfigured


No apport report written because MaxReports is reached alreadydpkg: error processing package python-tables (--configure):
 dependency problems - leaving unconfigured
Setting up python-xlrd (0.9.2-1) ...
No apport report written because MaxReports is reached already
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-xlrd (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
dpkg: error processing package python-xlwt (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached alreadydpkg: error processing package python-aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptd
dpkg: error processing package python-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached alreadydpkg: error processing package software-center (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of python-scipy:
 python-scipy depends on python-decorator; however:
  Package python-decorator is not configured yet.
 python-scipy depends on python-numpy (>= 1:1.8.0); however:
  Package python-numpy is not configured yet.
 python-scipy depends on python-numpy-abi9; however:
  Package python-numpy-abi9 is not installed.
  Package python-numpy which provides python-numpy-abi9 is not configured yet.


dpkg: error processing package python-scipy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-statsmodels-lib:
 python-statsmodels-lib depends on python-numpy (>= 1:1.8.0); however:
  Package python-numpy is not configured yet.
 python-statsmodels-lib depends on python-numpy-abi9; however:
  Package python-numpy-abi9 is not installed.
  Package python-numpy which provides python-numpy-abi9 is not configured yet.


dpkg: error processing package python-statsmodels-lib (--confi
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of python-statsmodels:
 python-statsmodels depends on python-numpy; however:
  Package python-numpy is not configured yet.
 python-statsmodels depends on python-scipy; however:
  Package python-scipy is not configured yet.
 python-statsmodels depends on python-statsmodels-lib (>= 0.5.0+git13-g8e07d34-1ubuntu2); however:
  Package python-statsmodels-lib is not configured yet.
 python-statsmodels depends on python-patsy; however:
  Package python-patsy is not configured yet.


dpkg: error processing package python-statsmodels (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 python-decorator
 python-simplegeneric
 ipython
 python-markupsafe
 python-jinja2
 python-tornado
 python-zmq
 ipython-notebook
 python-antlr
 python-bs4
 python-colorama
 python-cvxopt
 python-dateutil
 python-debian
 python-distlib
 python-html5lib
 python-joblib
 python-pyparsing
 python-tz
 python-numpy
 python-matplotlib
 python-mysqldb
 python-nose
 python-numexpr
 python-pandas-lib
 python-pandas
 python-patsy
 python-urllib3
 python-requests
 python-setuptools
 python-simplejson
 python-sklearn-lib
 python-sympy
 python-tables-lib
 python-tables
 python-xlrd
 python-xlwt
 python-aptdaemon
 python-aptdaemon.gtk3widgets
 software-center
 python-scipy
 python-statsmodels-lib
 python-statsmodels
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
Your help is really appreciated.

---

### Post by ian-weisser on 2014-10-05
Oh, dear.

The 'python' interpreter in 14.04 should be Python 2.7 . Many applications still depend upon /usr/bin/python linking to 2.7 .
The 'python3' interpreter in 14.04 already links to Python 3.4, which is already installed in 14.04 . Python3 applications should use /usr/bin/python3 .

Do you know how to undo the changes you have wrought?
Do you remember _exactly_ how you wrought those changes?

---

