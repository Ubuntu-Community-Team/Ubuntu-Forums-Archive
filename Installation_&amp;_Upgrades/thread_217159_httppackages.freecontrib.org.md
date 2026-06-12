---
title: "http://packages.freecontrib.org"
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by Drunken Pirate on 2006-07-16
I noticed that my Freecontrib repo was not working. I quicked fixed it by changing it from this:

```
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
**deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free**
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
#deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
## MAJOR BUG FIX UPDATES produced after the final release
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
[B]deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free[/B]                                              
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

to this

```
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
**deb http://packages.freecontrib.org/plf/ dapper free non-free**
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
#deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
## MAJOR BUG FIX UPDATES produced after the final release
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
[B]deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free[/B]                                          
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

I dont know if this is a recent thing or something, but this seems to fix it for now. I got my sources.list from [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories") as well as EasyUbuntu. Both of the lists have a problem with the Freeconfig repo.

If there is another repo/fix for this please tell me.

Thanks!

---

### Post by sakis on 2006-07-16
thank you :mrgreen:

---

### Post by dyrer on 2006-10-15
these packages ask me for a public key

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following sign atures couldn't be verified because the public key is not available: NO_PUBKEY F 120156012B83718
W: You may want to run apt-get update to correct these problems

Any help?

---

### Post by nickpaton on 2006-10-15
Dryer:

You need to add the Public key as detailed in the following post:

[http://www.ubuntuforums.org/showthread.php?t=232029]("http://www.ubuntuforums.org/showthread.php?t=232029")

---

