---
title: "upgrade problem from xubuntu 6.06 to 6.10"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by plusnplus on 2007-06-04
Hi All,
I tried to upgrade my xubuntu 6.06 to 6.10.
after i launch update manager, click the "upgrade" button beside "new destribution release 6.10 is available" then the system download 2 upgrading tool. after that finish it go back again to updatemanager/ software updates forms.
Anybody know what is wrong with my xubuntu 6.06 ?

thanks for any reply

---

### Post by zvacet on 2007-06-04
Maybe system need that upgrade tools.Did you try to upgrade after that?

---

### Post by plusnplus on 2007-06-04
Hi..,
after complete download the upgrade tool (2), i try click upgrade button again, then it repeated download the upgrade tool again. i did it 3 times already. the same thing happen. i even already re-start the pc.

any idea why ?

thanks for helping me :)

---

### Post by zvacet on 2007-06-04
Try this and see what happened

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by cari on 2008-04-03
Hi everyone,
I seem to be having the same problem- I can't upgrade from xubuntu 6.06 to 6.10 (It's simply not available in update-manager).
when I run
```
sudo aptitude update && sudo aptitude upgrade
```
I get
```

Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Get:3 http://ee.archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://ee.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:5 http://ee.archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://ee.archive.ubuntu.com dapper Release
Hit http://ee.archive.ubuntu.com dapper-updates Release
Hit http://ee.archive.ubuntu.com dapper-backports Release
Hit http://ee.archive.ubuntu.com dapper/main Sources
Hit http://ee.archive.ubuntu.com dapper/restricted Sources
Hit http://ee.archive.ubuntu.com dapper/universe Sources
Hit http://ee.archive.ubuntu.com dapper-updates/main Packages
Hit http://ee.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://ee.archive.ubuntu.com dapper-updates/main Sources
Hit http://ee.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://ee.archive.ubuntu.com dapper-backports/main Packages
Hit http://ee.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://ee.archive.ubuntu.com dapper-backports/universe Packages
Hit http://ee.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://ee.archive.ubuntu.com dapper-backports/main Sources
Hit http://ee.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://ee.archive.ubuntu.com dapper-backports/universe Sources
Hit http://ee.archive.ubuntu.com dapper-backports/multiverse Sources
Fetched 5B in 1m32s (0B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
markus@markus-hp:~$

```

can anyone help?

---

### Post by zvacet on 2008-04-03
Change your source list from Dapper to Edgy.

```
gksudo gedit /etc/apt/sources.list
```

Go to the search tab>replace>under search type dapper and replace edgy.Save file and close it.

```
sudo apt-get update && sudo apt-get upgrade
```

or you can do it with this command 

```
 sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list 
```

---

### Post by cari on 2008-04-07
Hi again,

yesterday I managed to get the "upgrade to 8.04" button by running 
```

sudo update-manager -d

```

problem solved:)

---

