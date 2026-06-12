---
title: "apt-get errors for autofs"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by mvirtual on 2011-02-02
Tried to update autofs feature. As per this link
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

I tried 

$ sudo apt-get install autofs

I get error:
-----------
$ sudo apt-get install autofs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package autofs
--------------

I am new to linux, please let me know how what is going wrong.

I get similar errors when trying to update some other packages as well. Is there a location where the packages are ?

---

### Post by arpanaut on 2011-02-02
Looks like that since lucid the name of the program has changed.

Try:
```
sudo apt-get install autofs5
```

---

### Post by mvirtual on 2011-02-03
Thanks ! That helped. Eventually found that autofs was already included in the initial install :)

---

