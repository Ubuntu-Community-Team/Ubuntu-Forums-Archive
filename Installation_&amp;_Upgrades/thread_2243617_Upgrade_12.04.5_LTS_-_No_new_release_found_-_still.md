---
title: "Upgrade 12.04.5 LTS - No new release found - still..!"
date: 2014-09-10
forum: Installation &amp; Upgrades
---

### Post by tsouthwick102 on 2014-09-10
Hi All,

I have two Ubuntu Servers which I cannot get to upgrade, when i run do-release-upgrade (with or without the -d option), it still comes back with this message. 

Here is the result of:

root@ubuntuDNS2:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise
root@ubuntuDNS2:~# 

And I have the following in the:

grep Prompt= /etc/update-manager/release-upgrades
Prompt=lts
root@ubuntuDNS2:~# 

There is nothing to update, as I have always kept up to date with apt-get update & apt-get dist-upgrade.. I am at a loss as to what to do next. I don't really want to re-install them..

---

### Post by kansasnoob on 2014-09-10
Post the output of:

```
apt-cache policy update-manager-core
```

---

### Post by grahammechanical on 2014-09-10
You should not use the -d switch.

That will upgrade to a development version. There is only one development version and that is for the version coming after 14.04. We cannot upgrade to Utopic Unicorn (14.10) from 12.04. Only from 14.04. So, there are two reasons for not using -d switch. 1) there is not an development version after 12.04. That is why it does not work. 2) It is a development version and should not be used unless we are willing to accept the possibility of things breaking.

This might work

```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

Regards.

---

### Post by tsouthwick102 on 2014-09-12
Output as requested:

root@ubuntuDNS2:~# apt-cache policy update-manager-core
update-manager-core:
  Installed: 1:0.156.14.17
  Candidate: 1:0.156.14.17
  Version table:
 *** 1:0.156.14.17 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:0.156.14.5 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main amd64 Packages
     1:0.156.14 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main amd64 Packages
root@ubuntuDNS2:~#

---

