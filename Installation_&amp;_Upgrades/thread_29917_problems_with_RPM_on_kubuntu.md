---
title: "problems with RPM on kubuntu"
date: 2005-04-26
forum: Installation &amp; Upgrades
---

### Post by oppilif on 2005-04-26
1   I got a problem with my kubuntu beacause the is a lot of software that i need to install and i can t find them in kynaptic, and when i download them as rpm and i try to open them it ask me for a program to open the file ](*,) 

2  I am building my own ftp server is there any tutorial for kubuntu or for securityO:) 
3  what is a good firewall for kubuntu 64bit compatible  :| 

thanks for every thing 

compaq r3000
nvidia 4 amd64 3400
kub 5.04

---

### Post by tread on 2005-04-26
1. Try adding more repositories to find your software. Go to [www.ubuntuguide.org](www.ubuntuguide.org) for more information about that.
2. Convert rpm to deb using alien, then install with dpkg -i filename.deb
3. Firestarter is a good firewall interface.
Edited to add: I don't know if a 64 bit package is available though.

---

### Post by bored2k on 2005-04-26
1. You can't do anything with an .rpm in (K)ubuntu. Ubuntu is a debian based distribution, not a redhat based one. You can try to get those files in .deb or the source package. If you don't find them, do this to convert the rpm to deb:
```
sudo alien -d foo.rpm
sudo dpkg -i foo.deb
```
3. There is a fedora core x64 firestarter. [http://www.fs-security.com/download.php](http://www.fs-security.com/download.php)

---

