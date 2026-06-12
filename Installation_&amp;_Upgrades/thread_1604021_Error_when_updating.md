---
title: "Error when updating"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by ydm39 on 2010-10-23
Hi Everyone!
 I installed Ubuntu 10.10 ,now  I've been trying to add some applications like docky and jdownloader but always I got this message error :

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources 404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages 404 Not Found
Descargados 2477B en 5s (446B/s)
W: Imposible obtener [http://ppa.launchpad.net/tualatri/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/tualatri/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Imposible obtener [http://ppa.launchpad.net/tualatri/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/tualatri/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

I do not know how to solve these and how to find a way to install my applications . 
Than you in advance !

---

### Post by Wobblybob on 2010-10-23
can you post the result of;

$ cat /etc/apt/sources.list

Ta

---

### Post by sikander3786 on 2010-10-23
404 errors are caused by non-responsive servers most of the time.

You can disable the Launchpad PPAs from Software Center > Edit > Software Sources and disable all the PPAs from Other Software tab and again try the update.

---

### Post by ydm39 on 2010-10-23
sikander3786
Thanks I tried disabling the PPAs from the list , no problem updating now !

---

