---
title: "Backup Upgrades"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by yannifan on 2007-02-01
Hello ppl,
  i just installed Ubuntu drapper and updates all necessary packages.
I have a small doubt. I was experimenting some time bak and had to reinstall Ubuntu and download all packages again. Was wondering if the downloads are stored some where so tat i can save it and use it later for upgrades if needed

Cheers

---

### Post by bapoumba on 2007-02-02
There may be other tricks. Here is what I do :
Save a list of installed packages :
```
sudo dpkg --get-selections >installed_package_list
```
Use it :
```
sudo dpkg --set-selections <installed_package_list
sudo aptitude update
sudo aptitude upgrade
```

---

