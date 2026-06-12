---
title: "Failed to Fetch while trying to upgrade"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by SeaRox on 2006-08-12
I've been trying to upgrade from 6.06 to 6.06.1.  I tried using the Update Manager.  This is the error missage I got:

(Begin Error)

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-i386/Packages.gz) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-i386/Packages.gz) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/source/Sources.gz) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/source/Sources.gz) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)

(End Error)

I'm not sure why this is happening because I'm submitting this thread on the same computer.  I don't know if it helps but it always stalls at file 37 out of 48.  Another reason I don't think it is a network problem on my end is because I was able to update a couple of individual packages that the  Update Manager showed needing updating.

So I tried doing it with apt-get.  Here is my code/errors.

(Begin code)

ubuntu:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
ubuntu:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Fetched 3B in 4s (1B/s)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Reading package lists... Done
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
ubuntu:~$ sudo apt-get update && sudo apt-get dist-upgrade
Password:
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

(End Code)

I tried looking in Synaptic but I could ony find individual packages, nothing to upgrade the OS.

I've looked around on the wiki and in the forums but to no avail.  It's probably something simple, but me being a newbie can't find anything that seems to help.  Any help would be appreciated.

---

### Post by SeaRox on 2006-08-12
If anyone else has this problem, I solved it by updating my sources.list file.

---

### Post by Incendium on 2006-08-15
What did you change?

---

### Post by SeaRox on 2007-01-15
The sources.list file had the debs pointed at breezy badger instead of dapper drake.

---

