---
title: "Error During Update"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by Roadie332 on 2007-11-17
I'm trying to upgrade from Ubuntu 6.06 Dapper Drake to 6.10 Edgy Eft. I followed the upgrade notes and used alt + f2 and typed in the command "gksu "update-manager -c" when it starts the upgrade i get an error message saying this: Failed to fetch [http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz) 301 Moved Permanently

anyone know what the deal is?

thanks.

---

### Post by taurus on 2007-11-17
You need to edit your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and comment out by placing a # in front of those 3rd party repos.  Save it and then see if you can upgrade now.  

But if you are not sure what to do, just post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by Roadie332 on 2007-11-17
Thanks. THat woked perfect

---

