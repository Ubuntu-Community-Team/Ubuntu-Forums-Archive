---
title: "Is unixodbc Installed or Not"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by cmnorton on 2008-04-29
How do I tell if unixodbc is installed or not? I've searched for the directory, and cannot find it other than a doc directory, and apt-get install tells me it's installed.

sudo apt-get -y install 

gives this:

sudo apt-get -y install unixodbc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unixodbc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Searching for unixodbc results in this:
/usr/share/doc/unixodbc
/usr/share/lintian/overrides/unixodbc

---

### Post by ghstridr on 2008-04-29
Fire up Synaptic and search for the package.  Get the properties of the package, one of the tabs will tell you what files are installed where. :)

---

### Post by cmnorton on 2008-04-30
Thanks. I did that but could not find where the binaries were installed.

---

