---
title: "Sources.list issue"
date: 2014-04-04
forum: Installation &amp; Upgrades
---

### Post by martincho90 on 2014-04-04
Hi

Any time I run apt-get update or try to install any program from apt-install seems to be it's trying to connect to the old server:
sudo apt-get update
0% [Conectando a 200.42.56.146 (200.42.56.146)]
The I got the error time out: 
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/universe Translation-en
No se pudo conectar a 200.42.56.146:8080:

This is my sources.list:
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 

I coud find that the 200.42.56.146 is coming from the apt.conf file: 
Acquire::http::proxy "http://200.42.56.146:8080/";

Is there any way to remove or change that?
I just moved the file and uncommented the line but it's still trying to connect there.

Regards
Martin

---

### Post by steeldriver on 2014-04-04
If the configured proxy is unresponsive you could try telling apt to ignore it - I *think* the syntax is

```
sudo apt-get **-o Acquire::http::proxy=DIRECT** update
```

---

### Post by martincho90 on 2014-04-04
> **steeldriver said:**
> If the configured proxy is unresponsive you could try telling apt to ignore it - I *think* the syntax is

```
sudo apt-get **-o Acquire::http::proxy=DIRECT** update
```

Many thanks steeldriver!
Solved!

---

