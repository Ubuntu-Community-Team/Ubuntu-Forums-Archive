---
title: "Installing apache2 for svn give some problems"
date: 2013-09-23
forum: Installation &amp; Upgrades
---

### Post by enrico5 on 2013-09-23
Hi All,

I'm trying to install all i need to start using svn, downloading svn was no problem via the apt-get install command, but when i try installing apache2 via: sudo apt-get install apache2
I get the following: see bottom of message:
```
Err http://nl.archive.ubuntu.com/ubuntu/ oneiric-updates/main apache2.2-bin amd64 2.2.20-1ubuntu1.2
  404  Not Found
Err http://security.ubuntu.com/ubuntu/ oneiric-security/main apache2.2-bin amd64 2.2.20-1ubuntu1.2
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com/ubuntu/ oneiric-security/main apache2-utils amd64 2.2.20-1ubuntu1.2
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com/ubuntu/ oneiric-security/main apache2.2-common amd64 2.2.20-1ubuntu1.2
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com/ubuntu/ oneiric-security/main apache2-mpm-worker amd64 2.2.20-1ubuntu1.2
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com/ubuntu/ oneiric-security/main apache2 amd64 2.2.20-1ubuntu1.2
  404  Not Found [IP: 91.189.92.181 80]

```Indeed in the dir: [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/)
I cant find the packages mentioned in the above errors, 
I have checked my /etc/apt/sources.list , and i can only find the references to the root (parent) dir of the repository, i could not really find a solution on the web, any advice?

---

### Post by enrico5 on 2013-09-23
Solved, i need to run an apt-get update first!

---

### Post by wim3 on 2013-09-23
What happens here is that you local index has an old file name (thus version) because you didnt run update for a while. The security section is cleaned up often, thus this file doesn't exist anymore.
So yes, always run an update before an install ;o)

---

