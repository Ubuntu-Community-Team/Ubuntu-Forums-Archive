---
title: "Installing Rhythmbox"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by mouse- on 2012-04-24
I have been attempting to install Rhythmbox, which is a .tar.xz file, and, following the directions in the package {once extracted} attempted to run the command ./configure while in the file containing Rhythmbox's source code.  However, I got the following error message
```
checking for gobject-introspection... configure: error: gobject-introspection-1.0 is not installed

```However, gobject-introspection is installed.  Does anyone know what the problem is?

---

### Post by mabo5184 on 2012-04-24
Hi,
 
I recently compiled rhythmbox from source and there were many errors like this one.
 
You need to make sure the package-dev is also installed where package is the one named in the error. The -dev packages are not installed by default when the binary package is installed.
 
Also, to make it just a little more fun the package named in the errors is not always exactely the same as the one needed in the system.
 
Ubuntu have a good web site where you can search package names so I suggest you look there for the correct package name with -dev extension on the end.
 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
 
It took me a couple of days to fix all errors, compile, make, and install rhythmbox, but that maybe because I'm new at this ...
 
Hope that helps.

---

### Post by mouse- on 2012-05-02
This worked!  Thanks!

---

### Post by BeniaminK on 2012-08-20
So how come, apt-get can install it without those packages? It's weird for me: downloading about 100MB to install Rhythmbox, where is the profit?

---

