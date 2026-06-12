---
title: "Trying to install sun java6 -plugin but getting error"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by nmalekar on 2011-08-14
Hi ,
Trying to install sun java6-plugin but i am getting following error.dpkg: dependency problems prevent configuration of sun-java6-plugin:

 sun-java6-plugin depends on sun-java6-bin (>= 6.21dlj-0ubuntu1~maverick1~ppa1); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-plugin

Kindly tell me the right solution with the detail installation steps.

Thanks in advance.

---

### Post by nmalekar on 2011-08-14
qr

---

### Post by raja.genupula on 2011-08-14
man i have tried for you an got this 


assassin@genupulas:~$ sudo aptitude install sun-java6-plugin
The following NEW packages will be installed:
  gsfonts-x11{a} odbcinst{a} odbcinst1debian2{a} sun-java6-bin{a} 
  sun-java6-jre{a} sun-java6-plugin unixodbc{a} 
0 packages upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.8 MB of archives. After unpacking 105 MB will be used.
Do you want to continue? [Y/n/?]

---

### Post by raja.genupula on 2011-08-14
if aptitude not installed just type this 

```
sudo apt-get install aptitude 
```

---

### Post by sammiev on 2011-08-14
[This]("http://sites.google.com/site/easylinuxtipsproject/java") has always worked for me. GL :)

---

### Post by nmalekar on 2011-08-14
I tried the above command getting below msg

sudo aptitude install sun-java6-plugin
The following partially installed packages will be configured:
  man-db sun-java6-plugin 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 350 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the sun-java6-bin package. This might mean you need to manually fix this package.
E: I wasn't able to locate file for the sun-java6-bin package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

---

### Post by raja.genupula on 2011-08-14
hmmm ok have you installed java ? if so which version ?

---

