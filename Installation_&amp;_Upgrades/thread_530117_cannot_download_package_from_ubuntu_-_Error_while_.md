---
title: "cannot download package from ubuntu - Error while using apt-get command"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by gokul_ifs on 2007-08-20
Hi,

when i do apt-get update from my ubuntu machine i get thefollowing error.

root@saaskde:~# apt-get update
Err Index of / edgy-security Release.gpg
Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Err Index of / edgy Release.gpg
Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Err Index of / edgy-security/main Translation-en_US
Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Err Index of / edgy-security/restricted Translation-en_US
Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Err Index of / edgy/main Translation-en_US
Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Err Index of / edgy/restricted Translation-en_US
Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Err Index of / edgy-updates Release.gpg
Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Err Index of / edgy-updates/main Translation-en_US
Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Err Index of / edgy-updates/restricted Translation-en_US
Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...gy/Release.gpg](http://in.archive.ubuntu.com/ubuntu/...gy/Release.gpg) Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...tion-en_US.bz2](http://in.archive.ubuntu.com/ubuntu/...tion-en_US.bz2) Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...tion-en_US.bz2](http://in.archive.ubuntu.com/ubuntu/...tion-en_US.bz2) Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...es/Release.gpg](http://in.archive.ubuntu.com/ubuntu/...es/Release.gpg) Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...tion-en_US.bz2](http://in.archive.ubuntu.com/ubuntu/...tion-en_US.bz2) Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...tion-en_US.bz2](http://in.archive.ubuntu.com/ubuntu/...tion-en_US.bz2) Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/di...ty/Release.gpg](http://security.ubuntu.com/ubuntu/di...ty/Release.gpg) Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/di...tion-en_US.bz2](http://security.ubuntu.com/ubuntu/di...tion-en_US.bz2) Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/di...tion-en_US.bz2](http://security.ubuntu.com/ubuntu/di...tion-en_US.bz2) Could not connect to 172.25.232.130:80 (172.25.232.130). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

I want to download some VNC client and do remote login in to another unix machine.

Thanks in advance,
GOKUL

---

### Post by ddrichardson on 2007-08-20
I just pinged that IP address and there is no response. The server may be down for maintainance.

---

### Post by Gregory Elderberry? on 2007-08-21
i get the same message too, trying to do apt-get update to get a driver for ATIX1300

im a first time user (havent even seen the ubuntu desktop yet) - so all i would have to do is wait a couple of hours and try again, when the server will probably be up?

---

