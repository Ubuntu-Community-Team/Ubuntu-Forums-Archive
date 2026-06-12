---
title: "How do you check to see if 14.04.1 installed ?"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by Timmoore001 on 2014-08-14
I've tried 'Devices' but that does not show if .1 has been added .

is there any other way to find out ?

Any thoughts very welcome.

Tim

---

### Post by vasa1 on 2014-08-14
```
**[03:39 PM] ~ $** lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty
**[03:39 PM] ~ $**
```

---

### Post by kc1di on 2014-08-14
go to system setting >Details the first screen that pops up give you the version of Ubuntu your running on your machine. Overview tab. look at the bottom if the box in the right hand corner say system up to date , your running the latest possible version. if it say updates are needed then you need to do the updates to get the .1 version.  if you've been updating on a regular basis you should have 14.04.1 :) 
You can also check via the terminal by entering this command ```
lsb_release -a 
```

---

### Post by Timmoore001 on 2014-08-14
Many thanks to both replies!

Worked a treat and shows I have the .1 release trusty running !

A very happy,

Tim

---

### Post by kc1di on 2014-08-14
Enjoy ;)

---

