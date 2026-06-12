---
title: "Java install error"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by opiv421 on 2007-05-11
I'm trying to install java but when I run ```
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
``` I get the following error:

```
E: Type '“deb' is not known on line 46 in source list /etc/apt/sources.list
```

Any suggestions? I really need to get java installed to take my final before 11:59 p.m. :confused:

---

### Post by rondackcpu on 2007-05-15
Opi.  I'm sorry I didn't see your note days ago, but I can help if you are still stuck.  There's lots of bad advice out there about installing Java stuff.  The best way to do it is with the Synaptic Package Manager.  System >> Administration >> Synaptic  >> enter password when asked >> scroll down to "sun-java6-jre" or whatever you want to install about Java6 >> mark for installation >> accept dependencies >> click apply  >> accept the license >> done.  

Good luck

CRS

---

### Post by taurus on 2007-05-15
You cannot install anything with synaptic/apt-get/aptitude until you fix your /etc/apt/sources.list first.  There is a problem with line 46 in /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```

---

