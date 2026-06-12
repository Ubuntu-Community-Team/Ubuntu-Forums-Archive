---
title: "[SOLVED] unable to update"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by tontikki on 2008-11-20
There is a problem with the update manager, when i try to check for updates it displays 'downloading file 44 out of 65' then stops and shows following errors: 

```

Failed to fetch http://archive.canonical.com/ubuntu/dists/intrepid/partner/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://archive.canonical.com/ubuntu/dists/intrepid/partner/source/Sources.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz  403 Forbidden
Some index files failed to download, they have been ignored, or old ones used instead.

```

Same with add/remove programs and package manager. If i try to use terminal, i still get the error:

```
oli@cactus:~$ sudo apt-get update
[sudo] password for oli: 
Err http://archive.canonical.com intrepid Release.gpg                          
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err http://archive.canonical.com intrepid/partner Translation-en_GB            
  Unable to connect to archive.canonical.com http:
Err http://gb.archive.ubuntu.com intrepid Release.gpg                          
  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
Err http://gb.archive.ubuntu.com intrepid/main Translation-en_GB               
  Unable to connect to gb.archive.ubuntu.com http:
Err http://gb.archive.ubuntu.com intrepid/restricted Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err http://gb.archive.ubuntu.com intrepid/universe Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err http://gb.archive.ubuntu.com intrepid/multiverse Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err http://gb.archive.ubuntu.com intrepid-updates Release.gpg
  Unable to connect to gb.archive.ubuntu.com http:
Err http://gb.archive.ubuntu.com intrepid-updates/main Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err http://gb.archive.ubuntu.com intrepid-updates/restricted Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err http://gb.archive.ubuntu.com intrepid-updates/universe Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err http://gb.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err http://security.ubuntu.com intrepid-security/restricted Translation-en_GB
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/main Translation-en_GB
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/universe Translation-en_GB
  Unable to connect to security.ubuntu.com http:
Reading package lists... Done
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_GB.bz2  Unable to connect to archive.canonical.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

``` 


My wireless connection is working perfectly, i think i'm behind my university proxy which is wwwcache.nottingham.ac.uk port 3128. I entered the proxy in Synaptic package manager> Preferences>Network.


The problem was with Xubuntu Hardy, now i installed 8.10 and it still the same. Its incredibly frustrating, i've tried almost everything including completely reinstalling the system, but to no avail 	:neutral:

---

### Post by taurus on 2008-11-20
Try another server, okay.  No need to get mad.

System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and pick the Main Server.  Reload and check for the update again.

---

### Post by Kevbert on 2008-11-20
If the last post doesn't work, try browsing to one of the web addresses and see if you get an error e.g. [http://archive.canonical.com/ubuntu/dists/intrepid/partner/binary-i386](http://archive.canonical.com/ubuntu/dists/intrepid/partner/binary-i386) If this works please post your /etc/apt/sources.list file.

---

### Post by tontikki on 2008-11-20
Did it - still the same error. Then i tried to use 'Other'>'Select best server', it run throught them all and said 'No suitable download server was found. Please check your internet connection'.
Thanks for your help

---

### Post by tontikki on 2008-11-20
Browsing addresses works fine and very quick. The sources list:
```
oli@cactus:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Xubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main multiverse restricted universe

# deb cdrom:[Xubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main multiverse restricted universe
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

---

### Post by taurus on 2008-11-20
You should check your proxy setting again.

---

### Post by lightnin on 2008-11-20
I dont know if its related - but mine wont update either

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb
  Size mismatch


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb
  Size mismatch


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb
  Size mismatch

```

I'm using 7.10 Gutsy

Help :)

---

### Post by tontikki on 2008-11-20
> **taurus said:**
> You should check your proxy setting again.

OMG yes it was the proxy - and  our 'helpful' university IT helpline who had no idea that the proxy across the uni has been changed!!:lolflag: So had to go manually unpack their automatic proxy configuration file, which revealed that the proxy we are supposed to be using now is 128.243.253.119:8080. Now all working:guitar:

---

### Post by tontikki on 2008-11-20
how do i mark the thread as solved?

---

### Post by tontikki on 2008-11-20
done;)

---

### Post by Kevbert on 2008-11-21
One thing you may want to re-enable is the security updates (which previously failed to verify). Remove the '#' from the start of each line.

---

### Post by Nicu Alecu on 2008-11-21
> **lightnin said:**
> I'm using 7.10 Gutsy
Help :)
@Lightnin: there's another thread on this subject [here](http://ubuntuforums.org/showthread.php?t=987911)
Which is still in dire straits ...

---

### Post by tontikki on 2008-11-24
> **Kevbert said:**
> One thing you may want to re-enable is the security updates (which previously failed to verify). Remove the '#' from the start of each line.

thanks will do!

---

