---
title: "During 13.04 upgrade, failed to remove packages"
date: 2013-07-06
forum: Installation &amp; Upgrades
---

### Post by zpierce on 2013-07-06
I did the upgrade to 13.04 this morning, and everything went well but when I got to the part where it removes packages, I looked over the list and noticed it was removing Python, which I thought was odd.  So I selected Python and hit Keep, but that caused it to keep all the packages it was going to remove.  Is there a way to have those removed now?  It was over 50 packages, so I don't remember what even half of them were.  Thanks.

---

### Post by DJ_Max on 2013-07-06
What was the name of the package? Was it the Python interperter, or a Python module? It's either going to remove/upgrade or if it's a module it probabably doesn't need it anymore. APT usually knows what's best.

---

### Post by zpierce on 2013-07-06
It was Python 3.2 that I was trying to keep, but there were over 50 packages set to be removed, and it kept them all.

---

### Post by DJ_Max on 2013-07-06
Ubuntu 13.04 uses Python v3.3

Like I said, APT usually knows best. Let it upgrade and/or remove packages. You're likely run into issues trying to keep outdated packages.

---

### Post by zpierce on 2013-07-06
Ok,in the future I'll trust it, but my question is now that I have completed the upgrade to 13.04 and have accidentally kept all those outdated packages, is there any way to get them removed now?  Obviously, I don't remember what they all were, so I can't manually go and remove them.  Do I have to just wait for 13.10?

---

### Post by DJ_Max on 2013-07-06
How did you upgrade? You should be able to

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
```

---

### Post by zpierce on 2013-07-06
autoremove did it, thanks

---

### Post by DJ_Max on 2013-07-06
The APT package manager is very mature. It's come a very long way, in terms of handling dependcies and it's user-friendliness

---

