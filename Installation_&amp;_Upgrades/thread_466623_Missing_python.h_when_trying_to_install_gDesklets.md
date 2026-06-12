---
title: "Missing python.h when trying to install gDesklets"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by dean_brfc on 2007-06-06
When I do ./configure to try and install gDesklets, it stops short saying:

```
ite-packages
checking /usr/include/python2.5/Python.h usability... no
checking /usr/include/python2.5/Python.h presence... no
checking for /usr/include/python2.5/Python.h... no
configure: error: Can't find Python.h! You will need the python development package to successfully compile gDesklets.

```

I've looked in Synaptic and virtually everything to do with Python is installed, so I'm not really sure what I need and Google isn't giving any useful results.

Edit: I also tried going through the terminal, but this was the response:

```
...desktop:~$ sudo apt-get install gdesklets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gdesklets
```

---

### Post by arkham on 2007-06-07
To install python headers, you need the python2.5-dev package:

```
sudo apt-get install python2.5-dev
```

Switch out to 2.4 if you are running that but that is not what your error message suggests.

---

