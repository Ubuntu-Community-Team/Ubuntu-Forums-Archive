---
title: "lesstif instal"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by gegemax on 2007-12-10
I am new in Ubuntu ...
I try to install lesstif-dev_0.93.94-12_i386.deb
I choose "Open with GDebi Package installer"
Error : Dependancy is not satisfied lesstif1
Then I install lesstif1 : OK
But still same error message for lesstif-dev_0.93.94-12_i386.deb ???

---

### Post by Partyboi2 on 2007-12-10
Have you done a search with Synaptic Package Manager to see if the package is there? (easier way to install if it is listed)
otherwise
open a terminal (Applications>Accessories>Terminal)
change directory to where you have the package downloaded to if it is on your desktop (easiest way) you would type:
```
cd Desktop
```then
```
sudo dpkg -i lesstif-dev_0.93.94-12_i386.deb
```Post what happens. (you might want to use absolute beginners forum for this sort of question)

---

