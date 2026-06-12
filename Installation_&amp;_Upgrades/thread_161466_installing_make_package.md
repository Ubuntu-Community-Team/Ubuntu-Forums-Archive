---
title: "installing make package"
date: 2006-04-17
forum: Installation &amp; Upgrades
---

### Post by ashimseth on 2006-04-17
hey guys...
sorry to ask stupid questions ..but plz help me..
 wrkin on ubuntu 5.10..tryin to install make..
have dwnlded this package make_3.80-9_i386.deb
[B]
this wat i did:[/B]


root@LB:~# dpkg install /var/cache/apt/archives/make_3.80-9_i386.deb

**and this is what i get:**

dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

plz  help!!

:mad:

---

### Post by Sutekh on 2006-04-17
```
sudo dpkg -i /var/cache/apt/archives/make_3.80-9_i386.deb
```
or```
sudo dpkg --install /var/cache/apt/archives/make_3.80-9_i386.deb
```

---

