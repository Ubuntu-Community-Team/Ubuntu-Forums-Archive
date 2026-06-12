---
title: "How to really uninstall programms"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by lrohr on 2008-07-22
Hallo,

since I've got this problem several times and never find a solution in any boards I post it here.

My problem is, that I installed something and after deinstalling it with:
```
apt-get remove xyz
apt-get autoclean xyz
apt-get autoremove xyz
apt-get purge xyz
```
there are still peaces of it in the system. To give you an example:
I installt phpmyadmin but missed to put a "*" by apache2, so it isn't loaded by apache2. Since I didn't want to dig in to apache2 configs and where to copy which file, I want to deinstall phpmyadmin to check the apache2 option during the installation. but after 
```
apt-get remove apache2
apt-get autoclean apache2
apt-get autoremove apache2
apt-get purge apache2 
```
and the 
```
root@ubuserv:/usr/share/phpmyadmin# apt-get install phpmyadmin
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  libmcrypt4 php5-mcrypt
Vorgeschlagene Pakete:
  libmcrypt-dev mcrypt
Die folgenden NEUEN Pakete werden installiert:
  libmcrypt4 php5-mcrypt phpmyadmin
0 aktualisiert, 3 neu installiert, 0 zu entfernen und 9 nicht aktualisiert.
Es müssen 2963kB Archive geholt werden.
After this operation, 10,7MB of additional disk space will be used.
Möchten Sie fortfahren [J/n]? j
Hole:1 http://de.archive.ubuntu.com hardy/universe libmcrypt4 2.5.7-5 [82,8kB]
Hole:2 http://de.archive.ubuntu.com hardy/universe php5-mcrypt 5.2.3-0ubuntu1 [19,7kB]
Hole:3 http://de.archive.ubuntu.com hardy/universe phpmyadmin 4:2.11.3-1ubuntu1 [2860kB]
Es wurden 2963kB in 4s geholt (602kB/s)
Vorkonfiguration der Pakete ...
Wähle vormals abgewähltes Paket libmcrypt4.
(Lese Datenbank ... 38588 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke libmcrypt4 (aus .../libmcrypt4_2.5.7-5_amd64.deb) ...
Wähle vormals abgewähltes Paket php5-mcrypt.
Entpacke php5-mcrypt (aus .../php5-mcrypt_5.2.3-0ubuntu1_amd64.deb) ...
Wähle vormals abgewähltes Paket phpmyadmin.
Entpacke phpmyadmin (aus .../phpmyadmin_4%3a2.11.3-1ubuntu1_all.deb) ...
Richte libmcrypt4 ein (2.5.7-5) ...

Richte php5-mcrypt ein (5.2.3-0ubuntu1) ...

Richte phpmyadmin ein (4:2.11.3-1ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```
the configuration doesn't appear. I think this file is still in the system.

This is just one example it is still getting worse.

I installed ebox, since it crashes because I didn't have ldap running I deinstalled it. But ebox hat some cronjobs left, which mailed me every hour that there is an problem and ebox isn't running correct ... 

So how can I deinstall a program with all the crap configuration files ?

Thanks so far

lrohr

---

### Post by zvacet on 2008-07-22
```
sudo dpkg --remove --force-remove-reinstreq packagename
```

---

### Post by foolano on 2008-07-23
If you still have those cronjobs running, and you wanna get rid of them execute:

```

rm /etc/cron.hourly/ebox /etc/cron.hourly/99purgeEBoxLogs

```

By the way, can you tell me a bit more about what happened yo your LDAP and eBox, thanks :)

---

