---
title: "dkpg error with fdisk"
date: 2021-01-14
forum: Installation &amp; Upgrades
---

### Post by Carbunkel on 2021-01-14
I was trying to update and swap some apps around and I've hit a wall. I've normally been able to fix any issues with the basic clean, purge, remove and install methods but nothing seems to be working. Software updater tole me to use ```
sudo dpkg --configure -a
``` which presented this:
> dpkg: error processing package fdisk (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Errors were encountered while processing:
 fdisk```


I've tried [CODE]sudo dpkg --configure -a
sudo apt-get install -f 
sudo apt autoremove 
sudo apt autoremove --purge 
sudo apt update 
sudo apt upgrade 
sudo apt dist-upgrade
```
but they all fail and I'm not sure where to go from here to correct the issue. Any help or advice would be great.

---

### Post by CelticWarrior on 2021-01-14
If the error message says
```
[COLOR=#000000]*package is in a very bad inconsistent state; you should*[/COLOR]
[COLOR=#000000]*reinstall it before attempting configuration*[/COLOR]
```
then you should do just that and take it from there:
```
sudo apt install --reinstall fdisk
```

---

### Post by Carbunkel on 2021-01-14
So simple, I can't believe I didn't think to do this. Thank you. Homeschooling kids must have fried my brain. &#55357;&#56837;

---

### Post by ActionParsnip on 2021-01-14
If this is all OK then please mark as solved

---

