---
title: "Updates install problem"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by WildeBeest on 2008-01-23
When I attempt to install the latest updates, I get the following error message.

dpkg: can't mmap package info file '/var/lib/dpkg/available': No such device

Anyone see this before?

---

### Post by a_posse_ad_esse on 2008-01-23
Does

```

sudo dpkg --configure -a

```

do anything?  I wonder if there was a problem with the last update and there are things that have remained unfinished.

---

### Post by WildeBeest on 2008-01-24
Gives me the same message:

dpkg: can't mmap package info file `/var/lib/dpkg/available': No such device

---

### Post by scizzo on 2008-01-24
```
sudo apt-get -f install
```

if that gives you the same error:

```
sudo apt-get update && apt-get -u dist-upgrade
```

to see if there is dependency problems.

---

### Post by WildeBeest on 2008-01-24
OK, thanks. I'll try that when I get home from work.

---

### Post by WildeBeest on 2008-01-24
The output of sudo apt-get -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

The output of sudo apt-get update && apt-get -u dist-upgrade

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by WildeBeest on 2008-01-24
I tried installing samba and received the same error message.

sudo apt-get install samba

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  openbsd-inetd inet-superserver
Recommended packages:
  smbldap-tools
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
Need to get 3841kB of archives.
After unpacking 9433kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main samba 3.0.26a-1ubuntu2.3 [3841kB]
Fetched 3841kB in 5s (645kB/s)  
Preconfiguring packages ...
dpkg: can't mmap package info file `/var/lib/dpkg/available': No such device
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by WildeBeest on 2008-01-25
Bump it up!

---

