---
title: "upgrading the Ubuntu 6.06 LTS - Dapper Drake release"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by boondocks on 2008-03-05
I just dusted off an old laptop and discovered that it has - Ubuntu 6.06 LTS - Dapper Drake release

lsb_release -a
> Distributor ID: Ubuntu
Description:    Ubuntu 6.06.2 LTS
Release:        6.06
Codename:       dapper


According to:
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

I did:
gksu "update-manager -c" 

Which says:
Your system is up-to-date

So that is it?
I should be at Ubuntu 6.06.2 LTS ?
For LTS, is this "as good as it gets"?

---

### Post by jeffus_il on 2008-03-05
Try these in a terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by boondocks on 2008-03-05
sudo aptitude update
> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 3B in 2s (1B/s)
Reading package lists... Done


sudo aptitude upgrade
> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


So my system is up-to-date.  My question is - Can I go from Ubuntu 6.06.2 LTS to 6.10 ?

---

### Post by jeffus_il on 2008-03-05
do ```
gksu "update-manager -c -d"
```

---

### Post by boondocks on 2008-03-05
Ok, I did that - but whoa ...
It says "New distribution release '8.04' is available"

So I Upgrade from 6.06.2 LTS  to 8.04 (Alpha) release?

Shouldn't I be upgrading to a 7.x release?

---

### Post by jeffus_il on 2008-03-05
Oh! It's the -d for development, Are you sure the command without the -d (only -c) does not work, No don't go for Hardy unless you have a reason to, I am running Hardy, It's fine but requires much more attention.

```
jeff@jeff-desktop:~$ update-manager --help
Usage: update-manager [options]

Options:
  -h, --help            show this help message and exit
  -V, --version         Show version and exit
  -c, --check-dist-upgrades
                        Check if a new distribution release is available
  -d, --devel-release   Check if upgrading to the latest devel release is
                        possible
  -p, --proposed        Try to run a dist-upgrade
  --dist-upgrade, --dist-ugprade
                        Try to run a dist-upgrade

```

---

### Post by zvacet on 2008-03-05
Hardy is LTS too and that is why update manager lead you to that version.If you want my opinion stay with Dapper until April and then upgrade to Hardy.At that time Hardy will be stable.

---

### Post by boondocks on 2008-03-05
I did omit the -d 
gksu "update-manager -c"

That says the system is up-to-date.

So it appears that if I want to upgrade then Hardy is the only option.

I can wait till April (or shortly after that).

Thanks for all the help.

---

