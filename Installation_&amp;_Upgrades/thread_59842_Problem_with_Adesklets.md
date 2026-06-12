---
title: "Problem with Adesklets"
date: 2005-08-25
forum: Installation &amp; Upgrades
---

### Post by nozey on 2005-08-25
I can't find a adesklets package for ubuntu, so i tried to install it from source. But i get a error on configure:


```
**$ ./configure**

checking for a Python interpreter with version >= 2.3... python
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/s                                                                            ite-packages
checking for Python include path... find: /usr/include/python/: No such file or                                                                             directory

configure: error: cannot find Python include path
```


My python version:

**$ python -V**
Python 2.4.1


**$ ls /usr/include/ | grep python**
python2.4

So i tried:
**$ sudo ln -s /usr/include/python2.4/ /usr/include/python**

But i still get the same error.
Any sugestions?

PS: Sorry for my english ... i know it sucks =\

---

### Post by Angel101 on 2005-08-25
search here in the forums: "python include path"
you'll be surprised

---

### Post by nozey on 2005-08-25
I tried this:

**$ export PYTHONPATH=/usr/include/python2.4/**

But i still get the same error

---

### Post by nozey on 2005-08-25
I got it

First i downloaded this file:

[http://ftp.litnet.lt/pub/ubuntu/pool/main/p/python-defaults/python-dev_2.4.1-0ubuntu2_all.deb](http://ftp.litnet.lt/pub/ubuntu/pool/main/p/python-defaults/python-dev_2.4.1-0ubuntu2_all.deb)

then:

**$ sudo dpkg -i python-dev_2.4.1-0ubuntu2_all.deb**


After install this file i instaled this one: python2.4-dev 

**$ sudo apt-get install python2.4-dev **

Now i got another problem:

```
configure: error: Could not find terminal management library for readline
(either ncurses, termcap or curses).

```

Im going to try to get it fixed ... i will post here if i suceed

---

### Post by nozey on 2005-08-25
Ok ... got it working already.

I did this:

**$ sudo apt-get install libncurses5-dev libreadline5-dev libimlib2 libimlib2-dev**

And got it working. =)

So ... here goes the steps i made to compile adesklets:
```

$ wget http://ftp.litnet.lt/pub/ubuntu/pool/main/p/python-defaults/python-dev_2.4.1-0ubuntu2_all.deb
$ sudo dpkg -i python-dev_2.4.1-0ubuntu2_all.deb
$ sudo apt-get install python2.4-dev 
$ sudo apt-get install libncurses5-dev libreadline5-dev libimlib2 libimlib2-dev
$ cd adesklets/dir
$ ./configure
$ make
$ sudo make install
```

Hope it helps someone. \o/

---

### Post by Kluk-Kluk on 2005-09-10
[QUOTE=nozey]Ok ... got it working already.

I did this:

**$ sudo apt-get install libncurses5-dev libreadline5-dev libimlib2 libimlib2-dev**

And got it working. =)

So ... here goes the steps i made to compile adesklets:
```

$ wget http://ftp.litnet.lt/pub/ubuntu/pool/main/p/python-defaults/python-dev_2.4.1-0ubuntu2_all.deb
$ sudo dpkg -i python-dev_2.4.1-0ubuntu2_all.deb
$ sudo apt-get install python2.4-dev 
$ sudo apt-get install libncurses5-dev libreadline5-dev libimlib2 libimlib2-dev
$ cd adesklets/dir
$ ./configure
$ make
$ sudo make install
```

Hope it helps someone. \o/[/QUOTE]
 It helped me for sure ..... thx :)

---

