---
title: "query bout wine!"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by axyelp on 2007-10-31
I am working on ubuntu 7.04, thought of installing wine for windows supported applications.

but wouldn't installing wine trigger any windows-based malwares and spywares on the machine!

Thanks!

---

### Post by Saubazi on 2007-10-31
Good question but couple of remarks - wine won't execute anything unless you tell it to. So in order to 
get some virus invested software running you'd need to copy it over from windows partition for example and still I don't know how much damage that could inflict. Here one remark - you should never run wine as root (or with sudo), this already protects a lot against whatever wine might be doing...
I think the risk group mighgt be windows applications that want to connect to internet but I think they can then only screw up themselves or apps within same .wine prefix.

So I don't see the immediate huge risk.

---

