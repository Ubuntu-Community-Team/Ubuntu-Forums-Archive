---
title: "apt-get update repositorys broken :("
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by earobinson on 2005-10-15
when i do an apt-get update I get this

> root@null:/home/earobinson# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports Release.gpg
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/multiverse Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/main Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/restricted Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/universe Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Sources
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/main Packages
  404 Not Found [IP: 82.211.81.193 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/restricted Packages
  404 Not Found [IP: 82.211.81.193 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/universe Packages
  404 Not Found [IP: 82.211.81.193 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/multiverse Packages
  404 Not Found [IP: 82.211.81.193 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/main Sources
  404 Not Found [IP: 82.211.81.193 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/restricted Sources
  404 Not Found [IP: 82.211.81.193 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/universe Sources
  404 Not Found [IP: 82.211.81.193 80]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/multiverse Sources
  404 Not Found [IP: 82.211.81.193 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Fetched 191B in 1s (156B/s)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.193 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.193 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.193 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.193 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz)  404 Not Found [IP: 82.211.81.193 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 82.211.81.193 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz)  404 Not Found [IP: 82.211.81.193 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 82.211.81.193 80]
Reading package lists... Done
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


I only uncommented all the lines and havent made any changes, whats wrong?

---

### Post by DJ_Max on 2005-10-15
There are no backports for Breezy, you have to comment them.

---

### Post by brodock on 2005-10-24
you didn't get the most 'buggy'  thing...

look at the BADSIG error...
i'm getting this one too

> 
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: As
seguintes assinaturas são inválidas: BADSIG 40976EAF437D05B5 Ubuntu
Archive Automatic Signing Key <ftpmaster@ubuntu.com>


---

### Post by azteech on 2005-10-24
[quote=brodock]you didn't get the most 'buggy'  thing...

look at the BADSIG error...
i'm getting this one too[/quote] 
Brodock,

If you had searched the forum you would have found that the errors your talking about have already been discussed.

See the following thread to find the answer to your problem for the bad sig:

[http://www.ubuntuforums.org/showthread.php?t=75791]("http://www.ubuntuforums.org/showthread.php?t=75791")

---

