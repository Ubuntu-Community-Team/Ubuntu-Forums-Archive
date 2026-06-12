---
title: "Unable to lock the download directory"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by Gendor on 2006-06-27
Hi,

I'm trying to upgrade my Breezy Badger installation to Dapper Drake.

When running sudo apt-get update && sudo apt-get dist-upgrade (I'm upgrading from a CD), I get the following error message:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory ](*,) 

Is there a manual way to unlock the directory, as the directory was probably locked during a previous failed upgrade attempt?

Thanks,
Gendor

---

### Post by Dr. Nick on 2006-06-27
Have you rebooted the comouter yet? That may unlock it for you. apt-get may be still running in the background and be frozen up,

---

### Post by snick512 on 2008-02-14
```
sudo pkill apt
```

---

### Post by CrankyFilipino on 2008-06-12
i sooooooo needed this.. awesome thanks

---

### Post by Tobes on 2008-06-17
Yeah thanks for this. Using Ubuntu here and it just didn't want to update.

---

### Post by lyndaj70 on 2008-07-12
Thanks!  I had tried rebooting my system without success, but this worked.

---

