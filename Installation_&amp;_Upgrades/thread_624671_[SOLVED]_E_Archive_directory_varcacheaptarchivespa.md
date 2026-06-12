---
title: "[SOLVED] E: Archive directory /var/cache/apt/archives/partial is missing."
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by recklessray on 2007-11-27
hi , i have broken something to do with apt ... not sure how. this is the error message:

root@rays-laptop:/var/cache/apt/archives# apt-get install ipcalc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tile
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  ipcalc
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
E: Archive directory /var/cache/apt/archives/partial is missing.
root@rays-laptop:/var/cache/apt/archives# 


anyone know how to fix this? ive searched the forums and cant seem to see a solution... also, i have tried to touch partial in /var/cache/apt/archives/partial to see if apt will do it then; it didnt... please help if you can.. most apreciated :)

ray */:confused:

---

### Post by taurus on 2007-11-27
I see that you log in as root.  Try

```
mkdir /var/cache/apt/archives/partial
apt-get update
apt-get install ipcalc
```

---

### Post by recklessray on 2007-11-27
hi there,

thanks for that - so simple! i have wrongly thought 'partial was a file not a dir, your fix worked. 

many thanks!

ray */:popcorn:

---

