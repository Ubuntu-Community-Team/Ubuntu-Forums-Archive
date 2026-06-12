---
title: "cannot update from sources.list"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by figo2476 on 2008-01-19
* I am using gusty (7.10) from the kubuntu cd. I have no problem to browse the net, but I cannot 'sudo apt-get update/upgrade', It complains cannot connet to bla bla
* I read this post and I can update my  sources.list, but still cannot upgrade
[http://ubuntuforums.org/archive/index.php/t-380840.html](http://ubuntuforums.org/archive/index.php/t-380840.html)
* It seems there is something to do with the dns.. any hint?

---

### Post by zvacet on 2008-01-19
Chek that you have all repos open.if you don´t know how to do it look [here](http://kubuntu.org/~jriddell/kubuntu-upgrade/).If you have all reos open and still can not update go to network manager and select manual configuration>in DNS tab put this nameservers and delete one you find there 

208.67.222.222 and 208.67.220.220  Close.

```
pppoeconf
```

---

### Post by figo2476 on 2008-01-19
* It seems working
* Does it mean the default DNS is not working with the kubuntu os or with my ISP?

---

### Post by zvacet on 2008-01-19
If you find just one under DNS tab it is probably gateway and not your ISP nameservers.If you feel like it you can try with your ISP nameservers,but delete one you find when you open DNS tab.It is not related to distro.

---

