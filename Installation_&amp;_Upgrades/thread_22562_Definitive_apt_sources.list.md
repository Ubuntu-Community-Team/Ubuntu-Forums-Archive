---
title: "Definitive apt sources.list?"
date: 2005-03-28
forum: Installation &amp; Upgrades
---

### Post by timelord726 on 2005-03-28
Hello everyone.  Sorry to be a nuisance, but I was wondering, could someone post an absolute definitive apt sources.list file with as many sources as possible to get as wide a variety of software as possible but without any dead sources or problematic sources?  I'm sure this would be greatly appreciated not only by me but also by a few other people in the Ubuntu community.

Thanks so much!

---

### Post by bored2k on 2005-03-28
These are mine .

> 
# Ubuntu Hoary
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

# Englightenment DR17
deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/
#deb-src [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/

#XFCE
deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main
deb-src [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main

#Marillat
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

#Backports
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted


There are missing, but with those I haven't encountered any problems.

---

### Post by timelord726 on 2005-03-28
Thanks bored2k.  I wonder, why am I always having problems with Backports?

---

### Post by bored2k on 2005-03-28
[QUOTE=timelord726]Thanks bored2k.  I wonder, why am I always having problems with Backports?[/QUOTE]
 I also encounter problems with them . But I really don't use them, I posted them because you want them all ;).

After installing Hoary for the 3rd time, I decided to stick with Marillat's and Universe/Multiverse sources and that's it .

---

### Post by MkIII_Supra on 2005-07-14
[QUOTE=bored2k]These are mine .



There are missing, but with those I haven't encountered any problems.[/QUOTE]

Well they don't work either... here is my error messages...

```

Get:5 http://archive.ubuntu.com hoary/main Sources [231kB]
99% [5 Sources gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com hoary/main Sources
  Sub-process gzip returned an error code (1)
Get:6 http://archive.ubuntu.com hoary/universe Packages [2853kB]
99% [Working]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com hoary/universe Packages
  Sub-process gzip returned an error code (1)
Get:7 http://archive.ubuntu.com hoary/multiverse Packages [111kB]
99% [7 Packages gzip 0]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com hoary/multiverse Packages
  Sub-process gzip returned an error code (1)
Fetched 17.2kB in 5s (2919B/s)
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/Packages.gz  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz  401 Authorization Required
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: http://www.os-works.com testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CF455A0A8AC2C0A6
W: Couldn't stat source package list http://archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-backports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-backports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by matthew on 2005-07-14
For comparison, here are mine.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted

---

### Post by Haegin on 2005-07-14
MKIII Supra, you may wish to run "sudo apt-get update " to update your package lists so your pc knows which programs are available from which repos.

---

### Post by unconfused on 2005-07-19
This is my /etc/apt/sources.list

I get a GPG error that I'm having issues getting rid of.  Other than that, I haven't had issues with these sources.

evan

----------

## Hoary (Ubuntu 5)

## Security
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse 

## Major Bug Fixes
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse 

## Main Archive
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse 

## WINE
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ 
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/ 

## Java
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java

---

### Post by lotusleaf on 2005-07-19
Official [color=red]Skype[/color] Apt Repository

```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```

And of course, the [howto thread for this repository](http://www.ubuntuforums.org/showthread.php?t=46954). :)

---

### Post by craigevil on 2005-07-30
#Main Archive
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

##major bug fix updates 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

#Security Updates Main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

#Security Updates Universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## Backports Staging
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

Covers pretty much anything you might need and gives you over 16000 packages to choose from.

---

### Post by bored2k on 2005-07-31
[QUOTE=craigevil]#Main Archive
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

##major bug fix updates 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

#Security Updates Main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

#Security Updates Universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## Backports Staging
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

Covers pretty much anything you might need and gives you over 16000 packages to choose from.[/QUOTE]
 Backports staging repositories. Bleeding edge + unstable. Regular users should not use these. They are mostly for bug testing and special needs-

---

