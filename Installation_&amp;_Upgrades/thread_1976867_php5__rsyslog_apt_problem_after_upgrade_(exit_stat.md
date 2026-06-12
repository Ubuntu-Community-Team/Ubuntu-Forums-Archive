---
title: "*php5* / rsyslog apt problem after upgrade (exit status 139)"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by remyd1 on 2012-05-09
Hi,


I have some problems with the precise [12.04] upgrade with the following packages :

```
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 139
Paramétrage de rsyslog (5.8.6-1ubuntu8) ...
dpkg*: erreur de traitement de rsyslog (--install)*:
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 139
dpkg*: des problèmes de dépendances empêchent la configuration de php5*:
 php5 dépend de libapache2-mod-php5 (>= 5.3.10-1ubuntu3.1) | libapache2-mod-php5filter (>= 5.3.10-1ubuntu3.1) | php5-cgi (>= 5.3.10-1ubuntu3.1) | php5-fpm (>= 5.3.10-1ubuntu3.1)*; cependant*:
 Le paquet libapache2-mod-php5 n'est pas encore configuré.
 Le paquet libapache2-mod-php5filter n'est pas encore configuré.
  Le paquet php5-cgi n'est pas installé.
 Le paquet php5-fpm n'est pas encore configuré.
dpkg*: erreur de traitement de php5 (--install)*:
 problèmes de dépendances - laissé non configuré
Traitement des actions différées («*triggers*») pour «*man-db*»...
Traitement des actions différées («*triggers*») pour «*ureadahead*»...
Des erreurs ont été rencontrées pendant l'exécution*:
 libapache2-mod-php5_5.3.10-1ubuntu3.1_amd64.deb
 libapache2-mod-php5filter_5.3.10-1ubuntu3.1_amd64.deb
 php5-cli
 php5-fpm
 rsyslog
 php5

```

This is in french but, to summarize, I have the "exit status 139" error for 6 packages listed above.

I try apt-get check, apt-get -f install, aptitude autoclean, aptitude update, aptitude remove (these packages), aptitude purge (these packages) and try to reinstall, but it did not change anything.

I also tried to reconfigure these packages (dpkg-reconfigure ...), to remove them from /var/lib/dpkg/status (because these packages are lidted as half-configured), to clean the apt cache manually (rm -f /var/cache/apt/archives/*.deb) and their informations (rm -f /var/lib/dpkg/info/php5-cli.* ...).

I also tried force options for many operations (install, check),  dist-upgrade, safe-upgrade and build-dep option from aptitude.

Now, I really do not know what to do...

I should specify that I did 2 upgrades : 11.04 -> 11.10 -> 12.04

My libperl5.10 package was too old. It has been replace two times, by version 5.12 and then, version 5.14. I have to create a symbolic link to lure apt :
1st upgrade
```
ln -s /usr/lib/libperl.so.5.12 /usr/lib/libperl.so.5.10
```
2nd upgrade
```
ln -s /usr/lib/libperl.so.5.14 /usr/lib/libperl.so.5.10
```

I have many server under ubuntu and I can not do this upgrade on other servers as this error was not the only one I had (on my desktop, I had problem with my nvidia card : unity crash during upgrade).

---

