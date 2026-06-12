---
title: "f-spot &amp;&amp; shutterfly &amp;&amp; glimmr"
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by ankitmalik on 2005-06-26
F-Spot aint working for me...Does anyone know of a quick solution

```
maliks@ubuntu:~$ f-spot

(<unknown>:14977): Gdk-WARNING **: locale not supported by Xlib

(<unknown>:14977): Gdk-WARNING **: cannot set locale modifiers

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00213> PhotoStore:Query (.Tag[] tags, .DateRange range)
in <0x00029> FSpot.PhotoQuery:.ctor (.PhotoStore store)
in <0x005f3> MainWindow:.ctor (.Db db)
in <0x00134> Driver:Main (System.String[] args)
maliks@ubuntu:~$

```

Next Problem : Shutterfly

I downloaded the software RPM they provide... I installed it thru Alien...Now when I run it

```
maliks@ubuntu:~/Desktop$ sudo dpkg -i *.deb
Selecting previously deselected package sflysusw.
(Reading database ... 102713 files and directories currently installed.)
Unpacking sflysusw (from sflysusw_1.1.0-7_i386.deb) ...
Setting up sflysusw (1.1.0-7) ...
maliks@ubuntu:~/Desktop$ sflysusw
sflysusw: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
maliks@ubuntu:~/Desktop$

```

Next Problem: Glimmr

Can anyone point me to binaries of Glimmr for Ubuntu..or a quick howto on installing it???


Thanks

---

### Post by jlo on 2005-11-11
Here is how you can install the c++ library necessary to run the shutterfly software.

cd /usr/lib
wget [http://www.sqldesktop.com/download/libstdc++-2-libc6.1-1-2.9.0.so](http://www.sqldesktop.com/download/libstdc++-2-libc6.1-1-2.9.0.so)
ln -s libstdc++-2-libc6.1-1-2.9.0.so libstdc++-libc6.1-1.so.2

---

### Post by DirtDart on 2006-08-10
Thanks for the link for the libstdc++ file...couldn't seem to find it anywhere, at least not one that would work with Ubuntu.

---

