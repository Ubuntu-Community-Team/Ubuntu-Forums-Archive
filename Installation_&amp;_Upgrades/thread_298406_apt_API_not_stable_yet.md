---
title: "apt API not stable yet"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by KevlarGurra on 2006-11-12
Hi!

I'm trying to update from dapper to edgy, but when I run gksu "update-manager -c" I get the error "warnings.warn("apt API not stable yet", FutureWarning)"... The update-manager seems to work but I haven't dared to actually start the upgrading due to the error message... What does it mean and is it safe to upgrade?

---

### Post by deepwave on 2006-11-12
The upgrade process to edgy is a bit rough.  I suggest going the command line route of:

apt-get dist-upgrade

Edit: Yes it is safe.  Be prepared for a few oddities nontheless.

---

### Post by newagelink on 2006-11-21
I got a similar error, except it said "these updates will not be downloaded." I posted [the full thing here]("http://ubuntuforums.org/showpost.php?p=1785256&postcount=96").

I'm gonna try ```
apt-get dist-upgrade
``` after ```
sudo apt-get update
``` finishes successfully -- it hasn't, yet. Doesn't seem like it's going to:
```
daniel@daniel-laptop:~$ sudo apt-get update
Password:
Ign http://wine.budgetdedicated.com breezy Release.gpg
Ign http://wine.budgetdedicated.com dapper Release.gpg
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:3 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Hit http://archive.ubuntu.com dapper Release
Get:4 http://security.ubuntu.com dapper-security Release [30.9kB]
Hit http://archive.canonical.com dapper-commercial Release
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://wine.budgetdedicated.com breezy Release
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://wine.budgetdedicated.com dapper Release
Hit http://archive.ubuntu.com dapper/restricted Packages
Ign http://wine.budgetdedicated.com breezy/main Packages
Ign http://wine.budgetdedicated.com dapper/main Packages
Hit http://wine.budgetdedicated.com breezy/main Packages
Hit http://wine.budgetdedicated.com dapper/main Packages
Get:5 http://security.ubuntu.com dapper-security/main Packages [80.5kB]
Get:6 http://security.ubuntu.com dapper-security/restricted Packages [6460B]
Get:7 http://security.ubuntu.com dapper-security/main Sources [14.9kB]
Get:8 http://security.ubuntu.com dapper-security/restricted Sources [968B]
Get:9 http://security.ubuntu.com dapper-security/multiverse Packages [2782B]
Get:10 http://security.ubuntu.com dapper-security/universe Packages [41.5kB]
Err http://us.archive.ubuntu.com dapper Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed  out
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed  out
Fetched 178kB in 8m0s (371B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Co uld not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release .gpg  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection t imed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used  instead.
daniel@daniel-laptop:~$
``` :(

---

