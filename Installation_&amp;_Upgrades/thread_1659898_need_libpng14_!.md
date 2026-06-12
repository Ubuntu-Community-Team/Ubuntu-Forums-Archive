---
title: "need libpng14 ?!?"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by anystupidname1 on 2011-01-04
I'm trying to get rawtherapee running but I can't get / find one or more dependencies?!?:confused:
[http://www.rawtherapee.com](http://www.rawtherapee.com)

```
error while loading shared libraries: libpng14.so.14: cannot open shared object file: No such file or directory
``````
apts libpng
p   libpng++-dev                                                           - C++ interface to the PNG (Portable Network Graphics) library                    
v   libpng-dev                                                             -                                                                                 
p   libpng-sixlegs-java                                                    - Sixlegs Java PNG Decoder                                                        
p   libpng-sixlegs-java-doc                                                - Documentation for Sixlegs Java PNG Decoder                                      
i   libpng12-0                                                             - PNG library - runtime                                                           
v   libpng12-0-dev                                                         -                                                                                 
p   libpng12-dev                                                           - PNG library - development                                                       
p   libpng3                                                                - PNG library - runtime                                                           
v   libpng3-dev                                                            -                                                                                 
p   libpnglite-dev                                                         - lightweight C library for loading and writing PNG images                        
v   libpngwriter                                                           -                                                                                 
v   libpngwriter-dev                                                       -                                                                                 
p   libpngwriter0-dev                                                      - easy to use graphics library (development)                                      
p   libpngwriter0c2                                                        - easy to use graphics library (runtime)        
```

```
getlibs -l libpng14.so.14
No match for libpng14.so.14
No packages to install
getlibs -l libpng14.so
No match for libpng14.so
No packages to install
getlibs -l libpng14
No match for libpng14
No packages to install

```

boohoo

---

### Post by anystupidname1 on 2011-01-04
Workaround > use stable version

---

### Post by Defrector on 2011-01-06
I am bumping this because I need libpng14 for an unstable version of unrelated software and am not in a position to use the stable version.

---

### Post by Defrector on 2011-01-06
I got it.

I went here and downloaded libpng14 to my favorite downloading directory.
[http://rpm.pbone.net/index.php3/stat/26/dist/12/size/125952/name/libpng-1.4.5-1.x86_64.rpm]("http://rpm.pbone.net/index.php3/stat/26/dist/12/size/125952/name/libpng-1.4.5-1.x86_64.rpm")

I opened a terminal, ran 
```
sudo apt-get install alien
```

cd to the directory with the downloaded RPM file then,
```
sudo alien -i libpng-1.4.5-1.x86_64.rpm
```
Some fireworks and warnings but it worked! I would expect this to work with most (all?) libs which are available as RPMs.

---

### Post by rat9 on 2012-01-18
The directory in the link changed but i found a similar file and this worked for me! thanks !!

libpng-1.4.5-1.i486.rpm

---

### Post by Defrector on 2012-08-20
More links have broken and directories may have changed;  re-posting with an updated working version:

```


sudo apt-get install alien

wget ftp://rpmfind.net/linux/opensuse/update/11.4/rpm/x86_64/libpng14-14-1.4.4-3.6.1.x86_64.rpm

sudo alien -i libpng14-14-1.4.4-3.6.1.x86_64.rpm


```

... but my application would not find the .so file until I did this:

```

sudo ln --symbolic /usr/lib64/libpng14.so.14 /usr/lib/libpng14.so.14

```

---

