---
title: "Help with wine"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by gtkourounis on 2006-11-04
Well, i am trying to install wine (something that should be fairly simple) but my computer doesnt seem to install it. Here is the code that i get 

```
gtkourounis@gtkourounis-laptop:~$ sudo gedit /etc/apt/sources.list
gtkourounis@gtkourounis-laptop:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://www.getautomatix.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-security Release.gpg [191B]
Get:4 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:5 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Get:6 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get:7 http://ubuntu.moshen.de dapper Release.gpg [189B]
Hit http://www.getautomatix.com dapper Release
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.canonical.com dapper-commercial Release
Hit http://archive.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper-updates Release
Ign http://wine.budgetdedicated.com dapper Release.gpg
Hit http://ubuntu.moshen.de dapper Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://www.getautomatix.com dapper/main Packages
Get:8 http://wine.budgetdedicated.com dapper Release [745B]
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.canonical.com dapper-commercial/main Packages
Ign http://wine.budgetdedicated.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Err http://wine.budgetdedicated.com dapper/main Packages
  404 Not Found
Hit http://archive.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper-security/main Sources
Hit http://archive.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper-security/restricted Sources
Hit http://archive.ubuntu.com dapper-security/universe Packages
Hit http://archive.ubuntu.com dapper-security/universe Sources
Hit http://archive.ubuntu.com dapper-security/multiverse Packages
Hit http://archive.ubuntu.com dapper-security/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/universe Sources
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/main Sources
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/universe Sources
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
Fetched 752B in 22s (33B/s)
Failed to fetch http://ubuntu.moshen.de/dists/dapper/Release Unable to find expected entry  flash/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz 404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
gtkourounis@gtkourounis-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

```

They only reason that i can think for this not working is that i have an amd turion 64. do you guys have any ideas on how i could fix this?

thanx in advance

BTW, i am still using dapper drake

---

### Post by BungaMan on 2006-11-04
make sure your line in sources.list looks like this

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

and that is all you can do.  if it gives a 404 then for some technical reason the required files are not available on that server.

In the binary directories in [http://wine.budgetdedicated.com/apt/dists/dapper/main/](http://wine.budgetdedicated.com/apt/dists/dapper/main/) you should find a file called Packages.gz.  If it is not there you could get a 404 but then simply try again later on.

---

### Post by bks on 2007-03-14
Right on the WineHQ homepage there is a link on the upper right hand side for the newest version of wine, just click and download the file.  Then cd to where it was downloaded and type "sudo apt-get install *pkg filename*" and away you go.



P.S. I just tried to access the [WineHQ]("http://www.winehq.com") and it wouldn't come up, the 404 is probably on their end.  Try again later.

---

