---
title: "Libreoffice-5.2.4 installation issue"
date: 2016-12-28
forum: Installation &amp; Upgrades
---

### Post by mammadshah on 2016-12-28
Hi,

I am trying to install Libre-Office-5.2.4 from source, and getting issue for Python. for this I have installed Python using source-code in  /opt/Python3.6  directory,  here is the outcome of /opt/Python3.6

```


$ ls -l /opt/Python3.6/
total 16
drwxr-xr-x 2 root root 4096 Dec 26 16:45 bin
drwxr-xr-x 3 root root 4096 Dec 26 16:24 include
drwxr-xr-x 4 root root 4096 Dec 26 16:45 lib
drwxr-xr-x 3 root root 4096 Dec 26 16:45 share


```


when i try to configure office for installation it fail to find Python.

```

libreoffice-5.2.4.2$ ./configure --with-python=/opt/Python3.6/
....
....
....
checking for a Python interpreter with version >= 2.6... python
checking for python... /usr/bin/python
checking for python version... 3.6
checking for python platform... linux
checking for python script directory... ${prefix}/lib/python3.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python3.6/site-packages
checking which Python to use for Pyuno... **checking for a Python interpreter with version >= 3.3... python**
[B]checking for python... /usr/bin/python
checking for python version... 3.6[/B]
checking for python platform... linux
checking for python script directory... ${prefix}/lib/python3.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python3.6/site-packages
system
[B]checking Python.h usability... no
checking Python.h presence... no
checking for Python.h... no[/B]
configure: error: Python headers not found. You probably want to set both the PYTHON_CFLAGS and PYTHON_LIBS environment variables

```

for the above error i have set the env variables

```

libreoffice-5.2.4.2$ echo $PYTHON_LIBS
/opt/Python3.6/include/python3.6m

libreoffice-5.2.4.2$ echo $PYTHON_CFLAGS
/opt/Python3.6/include/python3.6m

/libreoffice-5.2.4.2$ ls -l /opt/Python3.6/include/python3.6m/Python.h
-rw-r--r-- 1 root root 2928 Dec 26 16:24 /opt/Python3.6/include/python3.6m/Python.h


```

---

### Post by ajgreeny on 2016-12-28
Hello **mammadshah** and welcome to the forums.

Do you have a good reason for installing from source; you may just be doing so for the personal challenge and to learn about doing so, but you can get the full suite of LO 5.2.4 from [http://www.libreoffice.org/download/libreoffice-fresh/](http://www.libreoffice.org/download/libreoffice-fresh/) and then just install using terminal of gdebi if you want a GUI way.

There is also a PPA repository which will allow you to install Version: 5.2.3.2 in the usual way, which may suit you better if you are new to Ubuntu.
See [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa) for all info about that way of installing.

---

