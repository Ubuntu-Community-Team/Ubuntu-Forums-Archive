---
title: "8800gt in hardy??"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by stienjo on 2008-05-14
I have a 8800gt and I will install it on Ubuntu 
This are my screen print of my problems
[IMG]http://www.plaatjesupload.nl/bekijk/2008/05/14/1210766475-520.png[/IMG]
This is my problem Can some one help me??????

Thankz

---

### Post by Partyboi2 on 2008-05-14
put sudo before the command to start the installer.
so for example
```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
```

---

### Post by stienjo on 2008-05-14
> **Partyboi2 said:**
> put sudo before the command to start the installer.
so for example
```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
```


I did that an then came the error of the screenshot

---

### Post by Partyboi2 on 2008-05-14
check that you are part of the admin group.  System --> Administration --> Users and Groups, unlock then click on "Properties" then the tab "User Privileges" then make sure "Administer the System" is ticked.

---

