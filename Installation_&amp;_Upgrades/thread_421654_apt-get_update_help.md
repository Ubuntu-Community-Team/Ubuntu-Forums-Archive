---
title: "apt-get update help"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by zwest on 2007-04-24
I've just installed Edubuntu 6.06LTS and would like to update firefox to 2.0, but have gotten stuck at the first step. (Yes, I am new to Linux).  I've pasted the terminal session below.  It seems to stop at [waiting for headers]

west@edubuntu:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: x.x.x.x 80]
40% [Waiting for headers] [Waiting for headers]

My internet connection seems to be ok (I am making this post from the same machine). Any ideas about what I may have done wrong? 

Thank You

---

### Post by Big Ed on 2007-04-24
> **zwest said:**
> I've just installed Edubuntu 6.06LTS and would like to update firefox to 2.0, but have gotten stuck at the first step. (Yes, I am new to Linux).  I've pasted the terminal session below.  It seems to stop at [waiting for headers]

west@edubuntu:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: x.x.x.x 80]
40% [Waiting for headers] [Waiting for headers]

My internet connection seems to be ok (I am making this post from the same machine). Any ideas about what I may have done wrong? 

Thank You

Try changing the security lines /etc/apt/sources.list to 

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

These lines taken from [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

HTH,
Ed

---

