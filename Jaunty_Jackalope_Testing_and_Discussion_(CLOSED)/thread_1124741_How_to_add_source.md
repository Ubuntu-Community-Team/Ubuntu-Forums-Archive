---
title: "How to add source"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by crapple on 2009-04-13
How to I add this source in jaunty?
deb [http://ppa.launchpad.net/globalmenu-team/ubuntu](http://ppa.launchpad.net/globalmenu-team/ubuntu) intrepid main

I need to get a package from it

---

### Post by collinp on 2009-04-13
System - Administration - Software Sources. Click on the "Third-Party Software" tab, then the "Add" button. Paste your source, click "Ok", then quit. It will automagically update the package cache, just install your package once it closes.

---

### Post by crapple on 2009-04-13
Thanks
It works but I get an error saying

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA


How do I fix this

---

### Post by Darkshade on 2009-04-13
> **crapple said:**
> Thanks
It works but I get an error saying

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA


How do I fix this


```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DA6DEEAA
```

Also the right source would be
```
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main
```
not intrepid ;)

---

### Post by jmmL on 2009-04-13
[FONT=Arial][SIZE=2]Check out [https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories) , specifically the section "Adding a PPA's keys to your system"
[/SIZE][/FONT]

---

### Post by crapple on 2009-04-21
thanks I added it and it works fine

---

