---
title: "Cant get rid of Microsoft MySql"
date: 2017-09-28
forum: Installation &amp; Upgrades
---

### Post by nagybal on 2017-09-28
Dear All! Please help as I do not know where to google further.

I would like to get rid of the package mssql-server

I have Ubuntu 14.04 installed.

I have the two xenial sources added:
[https://packages.microsoft.com/ubuntu/16.04/mssql-server](https://packages.microsoft.com/ubuntu/16.04/mssql-server)
[https://packages.microsoft.com/ubuntu/16.04/prod](https://packages.microsoft.com/ubuntu/16.04/prod)

```
bigb@127:~$ sudo apt-get remove --purge mysql-server mysql-client mysql-common
Csomaglisták olvasása... Kész
Függ&#337;ségi fa építése       
Állapotinformációk olvasása... Kész
Package 'mysql-client' is not installed, so not removed
A következ&#337; csomagok automatikusan lettek telepítve, és már nincs rájuk szükség:
  libdbi-perl libterm-readkey-perl mysql-client-core-5.5 mysql-server-core-5.5
Ezeket az „apt-get autoremove” paranccsal törölheti.
Az alábbi csomagok el lesznek TÁVOLÍTVA:
  libdbd-mysql-perl* libmysqlclient18* mysql-client-5.5* mysql-common*
  mysql-server* mysql-server-5.5*
0 frissített, 0 újonnan telepített, 6 eltávolítandó és 1 nem frissített.
1 nincs teljesen telepítve/eltávolítva.
Letöltend&#337; adatmennyiség: 0 B/149 MB.
A m&#369;velet után 67,2 MB lemezterület szabadul fel.
Folytatni akarja? [I/n] I
(Adatbázis olvasása ... 404718 fájl és könyvtár van jelenleg telepítve.)
Eltávolítás: mysql-server (5.5.57-0ubuntu0.14.04.1) ...
Eltávolítás: mysql-server-5.5 (5.5.57-0ubuntu0.14.04.1) ...
mysql stop/waiting
Beállítófájlok törlése: mysql-server-5.5 (5.5.57-0ubuntu0.14.04.1) ...
Eltávolítás: mysql-client-5.5 (5.5.57-0ubuntu0.14.04.1) ...
Eltávolítás: libdbd-mysql-perl (4.025-1ubuntu0.1) ...
Eltávolítás: libmysqlclient18:amd64 (5.5.57-0ubuntu0.14.04.1) ...
Beállítófájlok törlése: libmysqlclient18:amd64 (5.5.57-0ubuntu0.14.04.1) ...
Eltávolítás: mysql-common (5.5.57-0ubuntu0.14.04.1) ...
Beállítófájlok törlése: mysql-common (5.5.57-0ubuntu0.14.04.1) ...
dpkg: figyelmeztetés: a(z) mysql-common eltávolítása közben a(z) „/etc/mysql” könyvtár nem üres, így nem lett eltávolítva
Aktiválók feldolgozása: man-db (2.6.7.1-1ubuntu1) ...
Aktiválók feldolgozása: libc-bin (2.19-0ubuntu6.13) ...
dpkg: hiba a csomag feldolgozásakor: mssql-server (--configure):
 A(z) mssql-server csomag nem beállítható
 (jelenlegi állapota: `half-installed')
E: Sub-process /usr/bin/dpkg returned an error code (1)
bigb@127:~$ 

```

---

### Post by ian-weisser on 2017-09-28
> **nagybal said:**
> 
```

dpkg: figyelmeztetés: a(z) mysql-common eltávolítása közben a(z) „/etc/mysql” könyvtár nem üres, így nem lett eltávolítva

```

Empty that directory.

---

### Post by SeijiSensei on 2017-09-28
```
sudo apt-get remove --purge mysql-server mysql-client mysql-common
```

You want to remove the mssql packages, but your commands referenced mysql instead.  Maybe it's just a typo?

There's a reference at the end of the output you posted to mssql, but I can't tell why it's appearing in response to your request to remove mysql.

---

