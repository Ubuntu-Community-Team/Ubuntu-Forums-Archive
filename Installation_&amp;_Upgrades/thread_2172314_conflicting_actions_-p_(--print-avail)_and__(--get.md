---
title: "conflicting actions -p (--print-avail) and  (--get-selections)"
date: 2013-09-04
forum: Installation &amp; Upgrades
---

### Post by Harmeet_Singh on 2013-09-04
when i try to run ```
dpkg --get-selections --print-avail  > install.txt
``` this command in Ubuntu 12.04 the following error generate : 
```

dpkg: error: conflicting actions -p (--print-avail) and  (--get-selections)

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;



```

i want to retrieve all detailed information about installed packackages like synaptic manager using command

---

