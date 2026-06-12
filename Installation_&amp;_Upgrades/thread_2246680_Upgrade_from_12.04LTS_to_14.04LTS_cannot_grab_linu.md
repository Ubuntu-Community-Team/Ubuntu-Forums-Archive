---
title: "Upgrade from 12.04LTS to 14.04LTS cannot grab linux-headers"
date: 2014-10-02
forum: Installation &amp; Upgrades
---

### Post by thaine-rowley on 2014-10-02
So, I was wanting to install new cuda drivers, and figured i would upgrade to 14.04 while i was at it.  Started the upgrade last night (takes forever at work sometimes), and i come back to it couldn't grab linux-headers-3.13.0-36 all 3.13.0-36.63.

I checked with my IT deptartment, and the computer doesn't have a problem in the network (specially since it grabbed every other package), but when i try to do the upgrade i just get:

Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main linux-headers-3.13.0-36 all 3.13.0-36.63
  Connection failed [IP: 91.189.88.153 80]                                     
Fetched 0 B in 6s (0 B/s)                                                      
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-headers-3.13.0-36 all 3.13.0-36.63
  Connection failed                                                            
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main linux-headers-3.13.0-36 all 3.13.0-36.63
  Connection failed [IP: 91.189.91.15 80]                                      
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-headers-3.13.0-36 all 3.13.0-36.63
  Connection failed                                                            
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main linux-headers-3.13.0-36 all 3.13.0-36.63
  Connection failed [IP: 91.189.92.201 80]                                     
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-headers-3.13.0-36 all 3.13.0-36.63



I've tried a few different countries codes for the archive.  Any suggestions?

---

