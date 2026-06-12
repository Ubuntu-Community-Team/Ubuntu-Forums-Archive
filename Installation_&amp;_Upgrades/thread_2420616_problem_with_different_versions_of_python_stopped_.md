---
title: "problem with different versions of python stopped system from upgrading"
date: 2019-06-07
forum: Installation &amp; Upgrades
---

### Post by babakflame on 2019-06-07
Fellows,

I believe so many pythons being installed on my system has brought errors while trying to do the command:
```

sudo apt-get upgrade

```  

It gives me the following errors:
```

SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-apt_0.9.3.5ubuntu3_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ModuleNotFoundError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-ldb_1%3a1.1.24-0ubuntu0.14.04.2_amd64.deb
 /var/cache/apt/archives/python-crypto_2.6.1-4ubuntu0.3_amd64.deb
 /var/cache/apt/archives/python-samba_2%3a4.3.11+dfsg-0ubuntu0.14.04.20_amd64.deb

```

Can Some body hint me how can I fix this issue?
My operating system is Ubuntu 14.04.6.

Thank You

---

### Post by deadflowr on 2019-06-07
Regular support for 14.04 has ended.
It has now reached ESM support state:
[https://blog.ubuntu.com/2019/05/07/ubuntu-14-04-esm-support]("https://blog.ubuntu.com/2019/05/07/ubuntu-14-04-esm-support")

Probably best to do a clean install of 16.04 or 18.04.

---

