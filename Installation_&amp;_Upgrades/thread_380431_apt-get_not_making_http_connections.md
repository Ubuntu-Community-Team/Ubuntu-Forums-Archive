---
title: "apt-get not making http connections"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by Something_Generic on 2007-03-09
Hey all,

I have run into a little problem were apt is not able to make http connections.  If the site allows anonymus logins then I can just switch to ftp in sources.list but in some cases that is not possible.  Any suggestions?

I can browes the package sites in firefox.  I do not use a proxy and my firewall is not blocking http traffic.

I have pasted my sources.list below.

Below that I have pasted the results of an apt-get update with the only changes made changeing the "ht" of http to "f" in sources.list.

And, not all the time, (but all the updates for today) the apt-get update will hang at 99% when running with the FTP edits I have made.  

SG

*************** sources.list start **************
# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper universe multiverse 
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
# deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) dapper-seveas all 

# Medibuntu multimedia packages
# GPG key: 0C5A2783
# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free 

# Canonical Commercial packages
# GPG key: 437D05B5
# deb [ftp://archive.canonical.com](ftp://archive.canonical.com) dapper-commercial main

## Repository for Skype
# deb [ftp://download.skype.com/linux/repos/debian/](ftp://download.skype.com/linux/repos/debian/) stable non-free

# Unofficial Deb Packages
# deb [ftp://ftp.debian-unofficial.org/debian](ftp://ftp.debian-unofficial.org/debian) dapper main contrib non-free restricted

## Automatix repository
# GPG key: 521A9C7C 
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

*************** sources.list end ***************
*********** apt-get update (http ver)**********
root@All-in-1der:/etc/apt# sudo gedit sources.list

(gedit:15456): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
root@All-in-1der:/etc/apt# sudp apt-get update
bash: sudp: command not found
root@All-in-1der:/etc/apt# sudo apt-get update
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release.gpg
  Connection failed
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Packages
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release.gpg
  Connection failed [IP: 88.191.42.241 80]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/universe Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/multiverse Packages
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages
  Connection failed
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Packages
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Packages
  Connection failed
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/multiverse Packages
  Connection failed
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages
  Connection failed
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Packages
  Connection failed
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/universe Packages
  Connection failed
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/multiverse Packages
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
  Connection failed
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Packages
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Packages
  Connection failed [IP: 88.191.13.100 80]
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Packages
  Connection failed [IP: 88.191.26.58 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg) Connection failed
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg) Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg) Connection failed
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/dapper/Release.gpg) Connection failed [IP: 88.191.42.241 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz) Connection failed
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz) Connection failed
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz) Connection failed
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz) Connection failed
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz) Connection failed
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz) Connection failed
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz) Connection failed
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz) Connection failed
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz) Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz) Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz) Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz) Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz) Connection failed
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.gz) Connection failed [IP: 88.191.13.100 80]
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.gz) Connection failed [IP: 88.191.26.58 80]
Reading package lists... Done
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@All-in-1der:/etc/apt#

*********** apt-get update (ftp ver)***********

root@All-in-1der:/etc/apt# apt-get update
Get:1 [ftp://ca.archive.ubuntu.com](ftp://ca.archive.ubuntu.com) dapper Release.gpg [189B]
Hit [ftp://ca.archive.ubuntu.com](ftp://ca.archive.ubuntu.com) dapper-updates Release.gpg
Get:2 [ftp://ca.archive.ubuntu.com](ftp://ca.archive.ubuntu.com) dapper Release [34.8kB]
Get:3 [ftp://ca.archive.ubuntu.com](ftp://ca.archive.ubuntu.com) dapper-updates Release [50.9kB]
Hit [ftp://ca.archive.ubuntu.com](ftp://ca.archive.ubuntu.com) dapper/main Packages
Hit [ftp://ca.archive.ubuntu.com](ftp://ca.archive.ubuntu.com) dapper/restricted Packages
Hit [ftp://ca.archive.ubuntu.com](ftp://ca.archive.ubuntu.com) dapper/universe Packages
Hit [ftp://ca.archive.ubuntu.com](ftp://ca.archive.ubuntu.com) dapper/multiverse Packages
Hit [ftp://ca.archive.ubuntu.com](ftp://ca.archive.ubuntu.com) dapper-updates/main Packages
Hit [ftp://ca.archive.ubuntu.com](ftp://ca.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [ftp://ca.archive.ubuntu.com](ftp://ca.archive.ubuntu.com) dapper-updates/universe Packages
Hit [ftp://ca.archive.ubuntu.com](ftp://ca.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security Release.gpg
Get:4 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security Release [50.9kB]
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/main Packages
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/restricted Packages
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/universe Packages
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/multiverse Packages
99% [Connecting to ca.archive.ubuntu.com (206.167.141.10)]

---

### Post by bikuta on 2007-03-10
Hi guys,

I'm having a similar problem too. I've just done a clean install and when I try to connect to the repositories (default ones) it fails.

Any ideas?

---

### Post by Kochin on 2007-04-05
In your /etc/apt.conf, is there a line about 'Acquire::http::Proxy'? If there is one, delete it or comment it out with double slashes.

Mime says 'Acquire::http::Proxy "false"', but the apt-get still treats it as a proxy.

---

