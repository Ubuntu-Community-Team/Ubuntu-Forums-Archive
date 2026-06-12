---
title: "E: Internal Error, No file name for libapt-pkg4.12"
date: 2014-07-08
forum: Installation &amp; Upgrades
---

### Post by manfredauerv on 2014-07-08
I tried to update my Ubuntu-Server but i get some errors

Login:
```
Welcome to Ubuntu 12.04.4 LTS (GNU/Linux 3.8.0-36-generic x86_64)


 * Documentation:  https://help.ubuntu.com/


 System information disabled due to load higher than 1.0


64 packages can be updated.
37 updates are security updates.


Last login: Tue Jul  8 14:27:56 2014



```

I start upgrading:

```
auer@intranetserver:~$ sudo apt-get upgrade
[sudo] password for auer:
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut
Statusinformationen werden eingelesen... Fertig
Die folgenden Pakete sind zurückgehalten worden:
  linux-image-generic-lts-raring
Die folgenden Pakete werden aktualisiert (Upgrade):
  apache2 apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common apt apt-transport-https apt-utils bsdutils curl file gnupg gpgv grub-common grub-pc
  grub-pc-bin grub2-common ifupdown iproute libapache2-mod-php5 libapt-inst1.4 libblkid1 libcurl3 libcurl3-gnutls libdrm-intel1 libdrm-nouveau1a libdrm-radeon1
  libdrm2 libgnutls26 libmagic1 libmount1 libmysqlclient18 libssl1.0.0 libudev0 libuuid1 libwbclient0 libxml2 linux-generic-lts-raring linux-headers-3.8.0-42
  linux-headers-3.8.0-42-generic mount mysql-client-5.5 mysql-client-core-5.5 mysql-common mysql-server mysql-server-5.5 mysql-server-core-5.5 openssh-client
  openssh-server openssl php5-cli php5-common php5-mysql samba-common samba-common-bin tzdata udev update-manager-core util-linux uuid-runtime whoopsie xkb-data
62 aktualisiert, 0 neu installiert, 0 zu entfernen und 1 nicht aktualisiert.
10 nicht vollständig installiert oder entfernt.
Es müssen noch 8.743 kB von 69,1 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 15,4 kB Plattenplatz freigegeben.
Möchten Sie fortfahren [J/n]? j
Hole:1 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main libudev0 amd64 175-0ubuntu9.5 [28,4 kB]
Hole:2 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main util-linux amd64 2.20.1-1ubuntu3.1 [596 kB]
Hole:3 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main udev amd64 175-0ubuntu9.5 [314 kB]
Hole:4 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main mount amd64 2.20.1-1ubuntu3.1 [166 kB]
Hole:5 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main bsdutils amd64 1:2.20.1-1ubuntu3.1 [39,7 kB]
Hole:6 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main libuuid1 amd64 2.20.1-1ubuntu3.1 [12,8 kB]
Hole:7 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main libblkid1 amd64 2.20.1-1ubuntu3.1 [73,7 kB]
Hole:8 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main libmount1 amd64 2.20.1-1ubuntu3.1 [71,5 kB]
Hole:9 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm2 amd64 2.4.52-1~precise1 [26,1 kB]
Hole:10 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-intel1 amd64 2.4.52-1~precise1 [65,8 kB]
Hole:11 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-nouveau1a amd64 2.4.52-1~precise1 [14,0 kB]
Hole:12 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-radeon1 amd64 2.4.52-1~precise1 [27,9 kB]
Hole:13 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main whoopsie amd64 0.1.34 [24,4 kB]
Hole:14 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main xkb-data all 2.5-1ubuntu1.5 [473 kB]
Hole:15 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main iproute amd64 20111117-1ubuntu2.3 [444 kB]
Hole:16 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main ifupdown amd64 0.7~beta2ubuntu11.1 [48,3 kB]
Hole:17 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main openssh-server amd64 1:5.9p1-5ubuntu1.4 [339 kB]
Hole:18 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main openssh-client amd64 1:5.9p1-5ubuntu1.4 [942 kB]
Hole:19 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main update-manager-core amd64 1:0.156.14.13 [182 kB]
Hole:20 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main uuid-runtime amd64 2.20.1-1ubuntu3.1 [14,1 kB]
Hole:21 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main apache2 amd64 2.2.22-1ubuntu1.6 [1.490 B]
Hole:22 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main apache2-mpm-prefork amd64 2.2.22-1ubuntu1.6 [2.414 B]
Hole:23 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main apache2.2-common amd64 2.2.22-1ubuntu1.6 [228 kB]
Hole:24 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main apache2.2-bin amd64 2.2.22-1ubuntu1.6 [1.340 kB]
Hole:25 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main apache2-utils amd64 2.2.22-1ubuntu1.6 [91,4 kB]
Hole:26 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main grub-pc amd64 1.99-21ubuntu3.15 [140 kB]
Hole:27 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main grub-pc-bin amd64 1.99-21ubuntu3.15 [869 kB]
Hole:28 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main grub2-common amd64 1.99-21ubuntu3.15 [94,9 kB]
Hole:29 http://at.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.15 [2.073 kB]
Es wurden 8.743 kB in 14 s geholt (620 kB/s)
E: Internal Error, No file name for libapt-pkg4.12

```

What can i do?

---

### Post by slooksterpsv on 2014-07-10
Run: sudo apt-get update, then try sudo apt-get upgrade again.

---

