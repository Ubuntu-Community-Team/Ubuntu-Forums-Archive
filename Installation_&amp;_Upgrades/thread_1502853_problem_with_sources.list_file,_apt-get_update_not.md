---
title: "problem with sources.list file, apt-get update not working"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by durga11 on 2010-06-06
Hi 


I am  using ubuntu 9.10,

Can any one check my **/etc/apt/sources.list** file and let me know if  anything wrong in the file.

sudo apt-get  update is not working, there are some packages which are failing.

please find the attached sources.list and the output of apt-get update.

Thanks in Advance
Durga

---

### Post by Elfy on 2010-06-06
ubuntu is missing from them all 

sources list has for example  deb [http://ubuntuarchive.hnsdc.com/](http://ubuntuarchive.hnsdc.com/) karmic multiverse 
whereas the line should read deb [http://ubuntuarchive.hnsdc.com/ubuntu/dists/karmic/multiverse/](http://ubuntuarchive.hnsdc.com/ubuntu/dists/karmic/multiverse/)

You can probably edit them in Software sources or do it with a text editor 

```
kdesudo kate /etc/apt/sources.list
```

Edit - sorry you are running kubuntu - command edited

---

