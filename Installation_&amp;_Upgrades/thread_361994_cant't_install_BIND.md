---
title: "cant't install BIND"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by rokey on 2007-02-15
dear community

i have the following problem. i can't install bind :( when i type apt-get install bind9 i see always this error
```
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  bind9-doc
The following NEW packages will be installed:
  bind9
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 289kB of archives.
After unpacking 717kB of additional disk space will be used.
Err http://security.ubuntu.com dapper-security/main bind9 1:9.3.2-2ubuntu1.1
  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/bind9_9.3.2-2ubuntu1.1_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? 
```

and when i look, this package is really not there, because the version has changed. the new package is *bind9-host_9.3.2-2ubuntu1.[COLOR="Red"]2[/COLOR]_i386.deb *. but how could i fix this? i have already made a *apt-get update* and i also used the *--fix-missing* parameter... but nothing helps :( 

what else could i do? i need bind...

greets rokey

---

### Post by Kateikyoushi on 2007-02-15
The current version is Version: 1:9.3.2-2ubuntu3.1. You have to update before try to install something.
Try the following.

```
sudo aptitude update
sudo aptitude install bind9
```

---

### Post by rokey on 2007-02-15
thanks for the fast response!
i have more then ones made an update of the repository...

but when i type your suggestion, i have the following error
```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  bind9
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 289kB of archives. After unpacking 717kB will be used.
Writing extended state information... Done
Err http://security.ubuntu.com dapper-security/main bind9 1:9.3.2-2ubuntu1.1
  404 Not Found
```

...also there he can't find the right package :( 

perhaps i have to say i use ubuntu 6.06 server.

---

### Post by Kateikyoushi on 2007-02-15
Sorry I should have noticed your are using dapper.

The newest package is 1:9.3.2-2ubuntu1.2 [LINK]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=bind9&searchon=names&subword=1&version=dapper&release=all")
You are trying to get an older version which should not happen after the update.

How does your sources list look like ?

---

### Post by rokey on 2007-02-15
Kateikyoushi, thanks for your help! there was a problem in the source.list, i changed the sources and now i was able to install bind!
again thx for your help :KS

---

