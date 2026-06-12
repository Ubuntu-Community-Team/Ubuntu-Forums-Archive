---
title: "Cannot upgrade to Gutsy (failed to fetch...)"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by medeivalstargazer on 2007-10-26
when upgrading to gutsy it gets to the second step and stops at 29 out of 43(If i recall correctly) files and shows this message when i hit cancel:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2) 

my sources.list:  

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

# Medibuntu multimedia packages
# GPG key: 0C5A2783


I had removed medibuntu to see if it helped, it didn't...

---

### Post by nglnx on 2007-10-26
1. Have you tried a different mirror? Maybe the server you are using is overwhelmed.

---

### Post by medeivalstargazer on 2007-10-26
Uhm, so could you walk me through how to do that?

---

### Post by nglnx on 2007-10-27
Sorry for the late response...:)

There are several ways to do it, but perhaps the simplest one is to go to System/Administration and choose Software Sources menu item.

At the first tab use the download drop down list, choose other locations and then select one of the mirrors, preferably one near your location if you want better download speeds.

Hope this helps.

---

