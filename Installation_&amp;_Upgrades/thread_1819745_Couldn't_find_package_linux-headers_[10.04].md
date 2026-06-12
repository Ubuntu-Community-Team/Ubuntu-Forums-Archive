---
title: "Couldn't find package linux-headers [10.04]"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by luigi1010 on 2011-08-06
Hi, I'm new in the forum and ubuntu.

I use Ubuntu 10.04 and I have problems when I tried to use VirtualBox and VMware Player, for now I would like to use VMware but I can't because when I run  VMware I get this error:

[CENTER][IMG]http://i52.tinypic.com/358zcle.jpg[/IMG][/CENTER]

I typed the following command:
```
root@s1:/# sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
```

And I got the following message:
```
root@s1:/# sudo apt-get install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
E: Couldn't find package linux-headers-2.6.18-238.19.1.el5.028stab092.2
```

What can I do?

Thanks a lot for your help

---

### Post by realzippy on 2011-08-06
Where you got that kernel from, redhat?
Don't they have the headers ?

---

