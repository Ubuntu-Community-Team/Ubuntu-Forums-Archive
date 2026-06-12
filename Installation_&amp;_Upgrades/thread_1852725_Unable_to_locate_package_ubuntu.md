---
title: "Unable to locate package ubuntu"
date: 2011-09-30
forum: Installation &amp; Upgrades
---

### Post by fred stuff on 2011-09-30
sudo apt-get --reinstall install ubuntu desktop
 
returns
 
E: unable to locate package ubuntu
E: unable to locate package desktop

---

### Post by MAFoElffen on 2011-09-30
> **fred stuff said:**
> [COLOR=Red]sudo apt-get --reinstall install ubuntu desktop[/COLOR]
 
returns
 
E: unable to locate package ubuntu
E: unable to locate package desktop
Welcome to Ubuntu Forums!

You have some syntax and typo's, First the package name is "ubuntu-desktop", not "ubutu desktop.

Next is the syntax error. "--reinstall" is not an option of apt-get.  I think it is an aptitude option.  What I usually recommend is:
```

sudo service gdm stop
sudo apt-get remove --purge ubuntu-desktop
sudo apt-get install ubuntu-desktop
sudo service gdm start

```

---

### Post by garvinrick4 on 2011-09-30
> sudo apt-get --reinstall install ubuntu desktop
 
```
sudo apt-get install --reinstall "package name"
```without quotes

---

