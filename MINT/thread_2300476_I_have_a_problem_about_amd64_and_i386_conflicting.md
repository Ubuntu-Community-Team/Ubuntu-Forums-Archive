---
title: "I have a problem about amd64 and i386 conflicting"
date: 2015-10-26
forum: MINT
---

### Post by kwl2 on 2015-10-26
```
]dpkg: error processing package libgl1-mesa-dri:amd64 (--configure):
 package libgl1-mesa-dri:amd64 10.1.3-0ubuntu0.5 cannot be configured because libgl1-mesa-dri:i386 is at a different version (10.1.3-0ubuntu0.4)
dpkg: error processing package libgl1-mesa-dri:i386 (--configure):
 package libgl1-mesa-dri:i386 10.1.3-0ubuntu0.4 cannot be configured because libgl1-mesa-dri:amd64 is at a different version (10.1.3-0ubuntu0.5)
dpkg: error processing package libgdk-pixbuf2.0-0:amd64 (--configure):
 package libgdk-pixbuf2.0-0:amd64 2.30.7-0ubuntu1.2 cannot be configured because libgdk-pixbuf2.0-0:i386 is at a different version (2.30.7-0ubuntu1.1)
dpkg: error processing package libgdk-pixbuf2.0-0:i386 (--configure):
 package libgdk-pixbuf2.0-0:i386 2.30.7-0ubuntu1.1 cannot be configured because libgdk-pixbuf2.0-0:amd64 is at a different version (2.30.7-0ubuntu1.2)
dpkg: error processing package libudev1:amd64 (--configure):
 package libudev1:amd64 204-5ubuntu20.15 cannot be configured because libudev1:i386 is at a different version (204-5ubuntu20.14)
dpkg: error processing package libudev1:i386 (--configure):
 package libudev1:i386 204-5ubuntu20.14 cannot be configured because libudev1:amd64 is at a different version (204-5ubuntu20.15)
dpkg: error processing package libglapi-mesa:amd64 (--configure):
 package libglapi-mesa:amd64 10.1.3-0ubuntu0.5 cannot be configured because libglapi-mesa:i386 is at a different version (10.1.3-0ubuntu0.4)
dpkg: error processing package libglapi-mesa:i386 (--configure):
 package libglapi-mesa:i386 10.1.3-0ubuntu0.4 cannot be configured because libglapi-mesa:amd64 is at a different version (10.1.3-0ubuntu0.5)
dpkg: error processing package libgl1-mesa-glx:amd64 (--configure):
 package libgl1-mesa-glx:amd64 10.1.3-0ubuntu0.5 cannot be configured because libgl1-mesa-glx:i386 is at a different version (10.1.3-0ubuntu0.4)
dpkg: error processing package libgl1-mesa-glx:i386 (--configure):
 package libgl1-mesa-glx:i386 10.1.3-0ubuntu0.4 cannot be configured because libgl1-mesa-glx:amd64 is at a different version (10.1.3-0ubuntu0.5)
dpkg: dependency problems prevent configuration of udev:
 udev depends on libudev1 (= 204-5ubuntu20.15); however:
  Package libudev1:amd64 is not configured yet.

dpkg: error processing package udev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgl1-mesa-dri:amd64
 libgl1-mesa-dri:i386
 libgdk-pixbuf2.0-0:amd64
 libgdk-pixbuf2.0-0:i386
 libudev1:amd64
 libudev1:i386
 libglapi-mesa:amd64
 libglapi-mesa:i386
 libgl1-mesa-glx:amd64
 libgl1-mesa-glx:i386
 udev
```


Now, I can't update or upgrade. HELP!!

---

### Post by kc1di on 2015-10-26
hi in a terminal try the following```
sudo dpkg --configure -a
```

---

### Post by kwl2 on 2015-10-26
Same output with above

---

### Post by Bashing-om on 2015-10-26
kwl2; Hello;

What release, graphics card and driver are you running ?
( no support to this time from AMD for 15.10's kernel ).

[INDENT][INDENT]maybe so
[/INDENT][/INDENT]

---

### Post by kc1di on 2015-10-27
> **kwl2 said:**
> Same output with above

Ok then lets try a different approach enter the following commands in a terminal.

```
sudo apt-get clean 
sudo apt-get autoclean
```
```
rm -r /var/cache/apt /var/lib/apt/lists
```
then run
```
sudo apt-get update
```
See if that will fix the problem for you.
if not. 
Please got to /etc/apt/sources.list and post that file here.

---

### Post by kwl2 on 2015-10-27
The big problem seems solved but here is another problem.

dpkg: error processing package libgdk-pixbuf2.0-0:amd64 (--configure):
 package libgdk-pixbuf2.0-0:amd64 2.30.7-0ubuntu1.2 cannot be configured because libgdk-pixbuf2.0-0:i386 is at a different version (2.30.7-0ubuntu1.1)
Errors were encountered while processing:
 libgdk-pixbuf2.0-0:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)

> **Bashing-om said:**
> kwl2; Hello;

What release, graphics card and driver are you running ?
( no support to this time from AMD for 15.10's kernel ).
[INDENT][INDENT]maybe so
[/INDENT]
[/INDENT]


I'm using Intel cpu with Mint 17.2

> **kc1di said:**
> Ok then lets try a different approach enter the following commands in a terminal.

```
sudo apt-get clean 
sudo apt-get autoclean
```
```
rm -r /var/cache/apt /var/lib/apt/lists
```
then run
```
sudo apt-get update
```
See if that will fix the problem for you.
if not. 
Please got to /etc/apt/sources.list and post that file here.

Here is. Just one line.
#deb cdrom:[Linux Mint 17.2 _Rafaela_ - Release amd64 20150723]/ trusty contrib main non-free

---

### Post by howefield on 2015-10-27
Thread moved to the "*MINT*" forum.

---

