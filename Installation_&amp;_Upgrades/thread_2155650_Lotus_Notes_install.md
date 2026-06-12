---
title: "Lotus Notes install"
date: 2013-06-19
forum: Installation &amp; Upgrades
---

### Post by uzumakifahim on 2013-06-19
I'm trying to install Lotus Notes 8.5.3 using terminal, but it shows the following file dependency error.

```
(Reading database ... 191117 files and directories currently installed.)
Unpacking ibm-lotus-notes (from ibm-lotus-notes-8.5.3.i586.deb) ...
dpkg: dependency problems prevent configuration of ibm-lotus-notes:
 ibm-lotus-notes depends on libcupsys2; however:
  Package libcupsys2 is not installed.
 ibm-lotus-notes depends on libgnome-desktop-2 | libgnome-desktop-2-7 | libgnome-desktop-2-11 | libgnome-desktop-2-17; however:
  Package libgnome-desktop-2 is not installed.
  Package libgnome-desktop-2-7 is not installed.
  Package libgnome-desktop-2-11 is not installed.
  Package libgnome-desktop-2-17 is not installed.
 ibm-lotus-notes depends on libjpeg62; however:
  Package libjpeg62 is not installed.
```

Problem is that, when I'm trying to install **libsupsys2**, it's showing the following error. How can I solve that?

```
sudo apt-get install libcupsys2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcupsys2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libcupsys2' has no installation candidate

```

Please help experts. Thanks in advance.

---

### Post by uzumakifahim on 2013-06-19
I just need to know, how can I get & install **libcupsys2** package?

---

### Post by claracc on 2013-06-19
The package libcupsys2 is in conflict with libcups2. If you have a fully updated 12.04 system, you will have libcups2.

I suggest you to follow some guide as : [http://insane-on-linux.blogspot.com.es/2013/02/installing-lotus-notes-853-on-ubuntu.html](http://insane-on-linux.blogspot.com.es/2013/02/installing-lotus-notes-853-on-ubuntu.html) since it cannot seem to be straightforwar to install lotus notes in ubuntu

---

### Post by uzumakifahim on 2013-06-19
Thanks for this resourceful reply.

---

### Post by claracc on 2013-06-19
You are very welcome

---

### Post by matsbekman on 2013-08-13
Just installed Notes 9 on Ubuntu 64 without problems.
Installing it completely with no errors in the operating system


[http://iwonthemove.wordpress.com/tag/ubuntu-64-bit-lotus-notes/](http://iwonthemove.wordpress.com/tag/ubuntu-64-bit-lotus-notes/)


For reading on how to


This is my companys blog on wordpress and it is written by me

---

