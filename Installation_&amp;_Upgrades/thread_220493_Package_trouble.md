---
title: "Package trouble"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by spahn on 2006-07-21
I have tried and tried to figure out why i cannot get to certain packages...](*,) 

i have a clean **sources.list **, i don't know what else to do!
Here is a print out from my system:

```

$ sudo apt-get update
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Get:4 http://archive.ubuntu.com dapper-updates Release [30.9kB]
Get:5 http://archive.ubuntu.com dapper-backports Release [19.6kB]
Ign http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Sources
Get:6 http://archive.ubuntu.com dapper-updates/main Packages [43.0kB]
Get:7 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:8 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:9 http://archive.ubuntu.com dapper-updates/main Sources [25.0kB]
Get:10 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:11 http://archive.ubuntu.com dapper-backports/main Packages [14B]
Get:12 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:13 http://archive.ubuntu.com dapper-backports/universe Packages [14B]
Get:14 http://archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Get:15 http://archive.ubuntu.com dapper-backports/main Sources [14B]
Get:16 http://archive.ubuntu.com dapper-backports/restricted Sources [14B]
Get:17 http://security.ubuntu.com dapper-security Release [30.9kB]
Get:18 http://archive.ubuntu.com dapper-backports/universe Sources [14B]
Get:19 http://archive.ubuntu.com dapper-backports/multiverse Sources [14B]
Get:20 http://archive.ubuntu.com dapper/main Packages [821kB]
97% [20 Packages gzip 0] [17 Release 7006/30.9kB 22%]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/main Packages
  Sub-process gzip returned an error code (1)
Get:21 http://security.ubuntu.com dapper-security/main Packages [39.4kB]
Get:22 http://security.ubuntu.com dapper-security/restricted Packages [4275B]
Get:23 http://security.ubuntu.com dapper-security/main Sources [9552B]
Get:24 http://security.ubuntu.com dapper-security/restricted Sources [974B]
Get:25 http://security.ubuntu.com dapper-security/universe Packages [6951B]
Get:26 http://security.ubuntu.com dapper-security/multiverse Packages [2041B]
Get:27 http://security.ubuntu.com dapper-security/universe Sources [902B]
Get:28 http://security.ubuntu.com dapper-security/multiverse Sources [521B]
Fetched 215kB in 8s (24.1kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Can anybody give me a tip?
Thanks in advance!

---

### Post by avtolle on 2006-07-21
What packages are you after? What error messages do you get when you try to install the desired packages? TIA.

---

### Post by spahn on 2006-07-21
There are a bunch of packages that i am after but cannot access- (to many to list). I am trying to get at my main tools like GFTP, PHP5-GD...

---

### Post by spahn on 2006-07-21
Maybe it would be easier to diagnose if i put what i get when trying to install php5-gd via the Synaptic package manager:

**Could not mark all packages for installation or upgrade**
The following packages have unresolvable dependancies. Make sure that all required repositories are added and enabled in the preferences:

php5-gd:
 Depends: libt1-5 (>=5.0.2) but it is not installable

---

### Post by SkyNet2029 on 2006-07-22
It's giving you that error message because of the first error message in your 'sources.list' output:
This line in particular:
```
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Sub-p
```
because running a 'search' via apt shows the package listed here
'Depends: libt1-5 (>=5.0.2) but it is not installable'
is located in this archive: pool/main/t/t1lib/libt1-5_5.1.0-2_i386.deb

.Bummer.

You could apt-get update for awhile to see if it is just a server-side (like a timeout) error, or you could edit your 
/etc/apt/sources.list to include your country code, which might help just being on a different server and what not.
As an example:

```
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

```
hope that helps.

---

### Post by KenF on 2006-08-12
I'm pretty new to ubuntu.  I had a very similar problem 30 minutes ago.  Basically, for some reason, a run of "sudo apt-get update" was getting:

ken@newbox:/etc/apt$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages [3143kB]
99% [3 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 3B in 1s (2B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


After suggestions about "sudo apt-get clean" .... etc.  I did the following:

1.  Edited by /etc/apt/sources.list and replaced the "http" in the line:
    [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
with "ftp:.
2.  I ran "sudo apt-get update".
3.  That failed miserably.
4.  I changed the "ftp" back to an "http"
5.  I ran "sudo apt-get update" ... and everything was fine.

Somehow it triggered apt-get to no longer ignore the line.  I have no idea why.  I hope it helps.

Thanks,

Ken

---

