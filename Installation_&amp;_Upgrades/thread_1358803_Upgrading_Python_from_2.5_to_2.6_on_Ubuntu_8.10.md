---
title: "Upgrading Python from 2.5 to 2.6 on Ubuntu 8.10"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by dbarthel on 2009-12-18
Didn't find any definitive posts on upgrading from Python 2.5 to 2.6 on Ubuntu 8.10 so I though I'd post the steps here (pieces from different postings):

(As root :eek:, use sudo if that's your preference)
wget [http://www.python.org/ftp/python/2.6/Python-2.6.tgz](http://www.python.org/ftp/python/2.6/Python-2.6.tgz)
tar zxvf Python-2.6.tgz
cd Python-2.6
./configure --prefix=/usr
make
make install

---

### Post by dbarthel on 2009-12-19
Ok, *NOT* 'SOLVED'. When I try to install something (like 'apt-get install python-setuptools') I get this error:

ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.5

I searched for solutions but none worked for me so I've gone back to Pythion 2.5 with:

rm /usr/bin/python && ln -s python2.5 /usr/bin/python

<sigh>

If anyone knows of a way to *properly* upgrade the Python version on Ubuntu 8.10 from 2.5 to 2.6, please reply to this message.

---

