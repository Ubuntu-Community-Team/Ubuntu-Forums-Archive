---
title: "dependancy is not satisfiable error"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by ciscoboy on 2011-07-15
[SIZE=3]hello,

I am trying to install inssider on my laptop using a .deb package and the full error states:

Error: Dependency is not satisfiable: libmono-system-web2.0-cil (>= 2.6.7)

I also tried to install it using the terminal, without success. Another error pops-up and reads:

error processing inssider_0.1.1.0429_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 inssider_0.1.1.0429_i386.deb


Any advice would be greatly apreciated.

Thank you

Ciscoboy
[/SIZE]

---

### Post by zvacet on 2011-07-20
```
sudo apt-get install libmono-system-web2.0-cil 
```

After that try again to install deb package.

---

### Post by ciscoboy on 2011-07-21
I tried it, and it didn't work. Is there something to do or download for any dependancy 

errors regarding downloads? Could redownloading the .deb package or downloading it from 

another source have any change in the results?

---

### Post by wallydallas on 2012-01-13
I have the same problem and found this thread with google.  I also want to install the "inssider" wifi tool to solve problems with too many hot spots in a dense apartment building.

My GUI software center ( Ubuntu 10.04 ) shows ver 2 is installed.
seen on screen:  
libmono2.0-cil is installed.
libmono-system-web2.0cil    ( version 2.4.4  )

I'm trying to install "inssider" after downloading a DEB file 
inssider_0.1.1.0429_i386.deb
from the website:
[http://www.metageek.net/products/inssider/linux/](http://www.metageek.net/products/inssider/linux/) 

I right click that file and select open with gdebi package installer
error: dependency is not satisfiable
libmono-system-web2.0cil (>= 2.6.7)

I then get the same error noted here.  Can someone help me.
I think I need 2.6.7 or higher, but how do I use apt-get or the gdebi tools to get the very new version of this mono software?

---

### Post by raja.genupula on 2012-01-13
> **ciscoboy said:**
> [SIZE=3]hello,

I am trying to install inssider on my laptop using a .deb package and the full error states:

Error: Dependency is not satisfiable: libmono-system-web2.0-cil (>= 2.6.7)

I also tried to install it using the terminal, without success. Another error pops-up and reads:

error processing inssider_0.1.1.0429_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 inssider_0.1.1.0429_i386.deb


Any advice would be greatly apreciated.

Thank you

Ciscoboy
[/SIZE]


sudo apt-get install -f

and then try again.

---

### Post by directhex on 2012-01-13
> **wallydallas said:**
> I right click that file and select open with gdebi package installer
error: dependency is not satisfiable
libmono-system-web2.0cil (>= 2.6.7)

I then get the same error noted here.  Can someone help me.
I think I need 2.6.7 or higher, but how do I use apt-get or the gdebi tools to get the very new version of this mono software?

As per [http://mono-project.com/DistroPackages/Ubuntu](http://mono-project.com/DistroPackages/Ubuntu) 2.6.7 is officially only available for Ubuntu Maverick (10.10) and newer.

There are unofficial backports at badgerports.org

---

