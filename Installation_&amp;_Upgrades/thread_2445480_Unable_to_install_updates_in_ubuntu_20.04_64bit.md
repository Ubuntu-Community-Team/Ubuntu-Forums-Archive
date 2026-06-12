---
title: "Unable to install updates in ubuntu 20.04 64bit"
date: 2020-06-15
forum: Installation &amp; Upgrades
---

### Post by mfskanpur on 2020-06-15
when ever I run livepatch the following message is displayed.

[B]Livepatch is on. An error occured when checking for Livepatch updates.

When I update via terminal using command line the following screen is visible.

[/B]mfskanpur@mfskanpur-DL-H61MXP:~$ sudo apt update
[sudo] password for mfskanpur: 
Hit:1 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates InRelease                                                                                      
Hit:3 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports InRelease                                                                                    
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                                                                                              
Hit:5 [http://ppa.launchpad.net/mdoyen/homebank/ubuntu](http://ppa.launchpad.net/mdoyen/homebank/ubuntu) focal InRelease                                                                                  
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease                                                                                                 
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [107 kB]                                                                              
Get:8 [http://ftp.au.debian.org/debian](http://ftp.au.debian.org/debian) buster InRelease [121 kB]                                                                     
Ign:9 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable InRelease                                                                                     
Hit:10 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable Release                                                                                      
Err:8 [http://ftp.au.debian.org/debian](http://ftp.au.debian.org/debian) buster InRelease                                                                   
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 04EE7237B7D453EC NO_PUBKEY 648ACFD622F3D138 NO_PUBKEY DCC9EFBF77E11517
Ign:12 [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge InRelease
Hit:13 [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge Release
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [18.7 kB]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [31.6 kB]
Reading package lists... Done               
W: GPG error: [http://ftp.au.debian.org/debian](http://ftp.au.debian.org/debian) buster InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 04EE7237B7D453EC NO_PUBKEY 648ACFD622F3D138 NO_PUBKEY DCC9EFBF77E11517
E: The repository 'http://ftp.au.debian.org/debian buster InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
mfskanpur@mfskanpur-DL-H61MXP:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mfskanpur@mfskanpur-DL-H61MXP:~$ 

Please guide me in the matter.

---

### Post by CelticWarrior on 2020-06-15
Why do you have a Debian repository? The error is right there.

---

### Post by ActionParsnip on 2020-06-15
Eugh Webmin. Its not part of Ubuntu and crow-baring it onto Ubuntu from Debian sources will make a big mess. The dependencies are different and you will mangle your package system.
Why do you want Webmin? What do you plan to use it to do? There may be a solution in Ubuntu that can assist.
If you want Debian packages....USE DEBIAN

---

