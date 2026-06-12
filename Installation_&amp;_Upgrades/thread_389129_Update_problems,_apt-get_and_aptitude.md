---
title: "Update problems, apt-get and aptitude"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by pjaway on 2007-03-20
Hi All,

I have a problem updating my server.

firstly I am behind a firewall, proxy and ISA server.

I have installed ntlmaps to get round problems with the isa server.

However both apt-get and aptitude fail :-

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed


my apt.conf file is as :-

/etc/apt# pg apt.conf
APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "http://localhost:5865/";
Acquire::http::Pipeline-Depth=0;


I also have problems with wget

Any suggestions ?

thanks

---

### Post by moogman on 2007-03-20
Try something like this:
```

export http_proxy=http://my-proxy:8080/
```


Also, are you sure your proxy is right in the apt config? - [http://localhost:5865/](http://localhost:5865/)

---

### Post by Clay_Banger on 2007-03-21
do u need a user name and password to go through the proxy? if so u would use something like:
```
Acquire::http::Proxy "http://username:password@proxy:port";
```

---

