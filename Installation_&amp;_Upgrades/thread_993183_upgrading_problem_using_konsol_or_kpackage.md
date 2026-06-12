---
title: "upgrading problem using konsol or kpackage"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by supermal on 2008-11-25
I'm trying to upgrade/ install a few bits and bobs on my 8.04 ubuntu. If I use kpackage it never manages to connect with the gb. archive and if I use sudo apt-get install (package) in konsole I have the same problem.It never gets beyond 0%. My system works through a proxy address and I have tried to enter the proxy a few times now but with no joy. Does anyone know which is the correct method of  entering the proxy address. There seems to be more than one package to do this , but so far none have worked for me. Needless to say I have a good internet connection or you wouldn#t be reading this., but of course firefox allows you to set up a proxy address in its own setup.

---

### Post by unimpeccable on 2009-09-09
Add the following lines to your /etc/apt/apt.conf

```
Acquire::http::Proxy "http://proxy:port";
Acquire::ftp::Proxy "http://proxy:port";
```

Where "proxy" and "port" are you respective proxy server address and port number.

---

