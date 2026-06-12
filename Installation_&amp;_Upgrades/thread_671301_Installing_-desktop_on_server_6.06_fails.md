---
title: "Installing *-desktop on server 6.06 fails"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by eriklou on 2008-01-18
Not sure if this is my problem or not, but when I try and install xubuntu/ubuntu-desktop via apt-get I get the following message and it fails.
> 
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main xserver-xorg-core 1:1.0.2-0ubuntu10.8
  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.8_i386.deb)  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Not sure what to do, I was really wanting to get the box upgraded to 7.10 but I was unable to find an apt-get command that would work.

---

### Post by Pumalite on 2008-01-18
At the Terminal:
sudo apt-get update --fix-missing

---

### Post by eriklou on 2008-01-18
I did try that, it updates the package list and thats it. The system never had a 'desktop' environment installed, this was going to be the first.

It looks like I'll have to find a way around this.

---

### Post by Pumalite on 2008-01-18
Post:
uname -a
cat /etc/apt/sources.list

---

### Post by eriklou on 2008-01-18
It looks like other people are having the problem as well; [http://ubuntuforums.org/showthread.php?t=671276](http://ubuntuforums.org/showthread.php?t=671276)

Unfortunately the system is a PBX and we need it to be working, so I have reverted the system back to its original ceros4 :( for now. I'll try to 'upgrade' to Ubuntu again here when we don't need the thing near as bad. 

Thanks for your willingness to help.

-Erik

---

### Post by Pumalite on 2008-01-18
OK. Good luck.

---

