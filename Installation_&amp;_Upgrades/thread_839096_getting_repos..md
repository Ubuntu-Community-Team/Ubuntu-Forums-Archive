---
title: "getting repos."
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by sys_alpha on 2008-06-24
hi all,
   I wanted to know that is there any way to get all upgrades/updates ,that one need to do after installation using apt-get , in a go and save them to disk so that the offline users can get benefit of this by just getting them from disk rather than from Internet.

---

### Post by Kobalt on 2008-06-24
Daily builds of Ubuntu CD images are available from this wensite if you should need them : [http://cdimage.ubuntu.com/daily/](http://cdimage.ubuntu.com/daily/)
Using this you can straight install an up-to-date system, or upgrade an existing one (using the Alternate CD only).

---

### Post by iaculallad on 2008-06-24
Use the [aptoncd]("http://aptoncd.sourceforge.net/") utility to save all your update files located in your /var/cache/apt/archives/ directory to a CD media.


```
sudo apt-get install aptoncd
```

---

### Post by sys_alpha on 2008-06-24
thanks for reply . 
But all i want to do is update/upgrade a system connected for some time to internet and then move that system to some other place where internet is not available then i want to upgrade all other systems using this upgraded system.

This is doable in one respect if i make my system a repository place and change the sources.list and all those apt-get/utils things . But i want to do this by using simple pen drive transportation , is there any way to do this ?

My next Q is suppose i have XP machine with internet connectivity , can i download all upgrades to its HDD and upgrade my other systems which don't have internet using simple PenDrive operations ?
Thanks in advance.

---

