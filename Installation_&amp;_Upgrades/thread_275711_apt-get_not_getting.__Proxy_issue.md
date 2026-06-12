---
title: "apt-get not getting.  Proxy issue?"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by dc310 on 2006-10-11
Hi Folks,

Apt-get is giving me hostname lookup failures.  The result is that I cant even do a proper apt-get update.

Yes I'm behind some proxy thing at work. Yes I've tried the proxy statments but not really sure what to put in there.  (IP address of the gateway?)

The Really strange part is all the http: websites that apt-get is saying it cant get to... well I can manually curl/wget the files from thoes address.  So I can download the .deb packages.  Apt-get just wont get em.

It seems to start of well then goes into hostname lookup failures.

Yes I've disabled IP6.
Yes I can get to the ip addresses its complaining about.

Help!
](*,) 

---------------------------------------------
dc@infodev-lab7:~$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  404 Hostname lookup failure
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  404 Hostname lookup failure
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  404 Hostname lookup failure
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  404 Hostname lookup failure
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  404 Hostname lookup failure [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  404 Hostname lookup failure [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  404 Hostname lookup failure [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  404 Hostname lookup failure [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
  404 Hostname lookup failure [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
  404 Hostname lookup failure [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  404 Hostname lookup failure [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  404 Hostname lookup failure [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  404 Hostname lookup failure [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  404 Hostname lookup failure [IP: 146.137.96.7 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  404 Hostname lookup failure
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  404 Hostname lookup failure
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  404 Hostname lookup failure
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  404 Hostname lookup failure [IP: 146.137.96.7 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  404 Hostname lookup failure
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  404 Hostname lookup failure [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  404 Hostname lookup failure [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  404 Hostname lookup failure [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz)  404 Hostname lookup failure [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  404 Hostname lookup failure [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  404 Hostname lookup failure [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  404 Hostname lookup failure [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  404 Hostname lookup failure [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  404 Hostname lookup failure [IP: 146.137.96.7 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
dc@infodev-lab7:~$

---

### Post by tonyr on 2006-10-11
I was having this problem this morning.  I edited the sources.list
file and substituted **eu** for **us** (to use the european
repos instead of the US repos).  All better.  Something at the US
repositories must be hosed.

---

### Post by dc310 on 2006-10-11
Thanks for the reply.

eu. returned me the same results.  That would of been too good to be true.

I suspect this is a web/proxy issue.  But I'll be dammed to figure out what I'm supposed to input as my proxy.  We dont configure proxy info in our browsers.  It just works.

Anyone have any ideas of how I can determine if I need/what is my proxy url?

---

### Post by shivam on 2006-10-12
> **dc310 said:**
> Thanks for the reply.

eu. returned me the same results.  That would of been too good to be true.

I suspect this is a web/proxy issue.  But I'll be dammed to figure out what I'm supposed to input as my proxy.  We dont configure proxy info in our browsers.  It just works.

Anyone have any ideas of how I can determine if I need/what is my proxy url?
well go to System -> preferences -> network proxy 
and input the proxy values over there 
this will make it work

---

### Post by dc310 on 2006-10-12
I assume your refering to some GUI app.  I dont have the gui on this server box.  I still need a way to determine what/if proxy  is using.  

Anyone know if I can put an IP address in the apt.conf file?

Like so:
Acquire::http::Proxy "http://10.4.6.1/:80"

Of course I tried it and it doesnt work.

So does that mean the proxy has to valid dns name?

---

### Post by cjbmtb on 2006-11-17
Your Acquire::http::Proxy arg should be "http://10.4.6.1:80"

Remove the "/" between the last IP octet and the ":"port designation

---

