---
title: "apt by BitTorrent"
date: 2006-04-24
forum: Installation &amp; Upgrades
---

### Post by oneleaf on 2006-04-24
:) 

server: [http://paste.ubuntu.org.cn/29](http://paste.ubuntu.org.cn/29)
client:  [http://paste.ubuntu.org.cn/30](http://paste.ubuntu.org.cn/30)

---

### Post by oneleaf on 2006-04-24
first run aptbt.py

then

sudo vim /etc/apt/sources.list

breezy:

deb [http://127.0.0.1:8080/ubuntu/](http://127.0.0.1:8080/ubuntu/) breezy main restricted universe multiverse
deb [http://127.0.0.1:8080/ubuntu/](http://127.0.0.1:8080/ubuntu/) breezy-security main restricted universe multiverse
deb [http://127.0.0.1:8080/ubuntu/](http://127.0.0.1:8080/ubuntu/) breezy-updates main restricted universe multiverse
deb [http://127.0.0.1:8080/ubuntu/](http://127.0.0.1:8080/ubuntu/) breezy-backports main restricted universe multiverse

dapper:

deb [http://127.0.0.1:8080/ubuntu/](http://127.0.0.1:8080/ubuntu/) dapper main restricted universe multiverse
deb [http://127.0.0.1:8080/ubuntu/](http://127.0.0.1:8080/ubuntu/) dapper-security main restricted universe multiverse
deb [http://127.0.0.1:8080/ubuntu/](http://127.0.0.1:8080/ubuntu/) dapper-updates main restricted universe multiverse
deb [http://127.0.0.1:8080/ubuntu/](http://127.0.0.1:8080/ubuntu/) dapper-backports main restricted universe multiverse

---

