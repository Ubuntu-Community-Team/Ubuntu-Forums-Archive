---
title: "Installing from a local http server"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by kakao2 on 2010-05-14
I'm trying to install Lucid 64 desktop from a pen drive using a local http server. 

I zcated [http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/netboot/boot.img.gz]("http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/hd-media/boot.img.gz") to the pen drive fist partition and it works.

I have setup the http server with the mounted iso install image.

When I supply the server address and directory it says that the file download failed although I can see at the server log that the files are served without errors:

```

10.1.1.4 - - [14/May/2010:18:18:10 -0300] "GET /iso/dists/lucid/Release HTTP/1.1" 200 1778 "-" "Wget"
10.1.1.4 - - [14/May/2010:18:18:10 -0300] "GET /iso/dists/lucid/Release HTTP/1.1" 200 1778 "-" "Wget"
10.1.1.4 - - [14/May/2010:18:18:10 -0300] "GET /iso/dists/lucid/main/binary-amd64/Release HTTP/1.1" 200 95 "-" "Wget"
10.1.1.4 - - [14/May/2010:18:18:10 -0300] "GET /iso/dists/lucid/Release HTTP/1.1" 200 1778 "-" "Wget"
10.1.1.4 - - [14/May/2010:18:18:10 -0300] "GET /iso/dists/lucid/Release.gpg HTTP/1.1" 200 189 "-" "Wget"
10.1.1.4 - - [14/May/2010:18:19:58 -0300] "GET /iso/dists/lucid/Release HTTP/1.1" 200 1778 "-" "Wget"
10.1.1.4 - - [14/May/2010:18:19:58 -0300] "GET /iso/dists/lucid/Release.gpg HTTP/1.1" 200 189 "-" "Wget"

```There are no errors at the error log. Any ideas?

---

