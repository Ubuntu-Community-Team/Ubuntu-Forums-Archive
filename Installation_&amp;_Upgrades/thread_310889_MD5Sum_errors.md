---
title: "MD5Sum errors"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by digeratess on 2006-12-02
I'm trying to re-install Dapper (after a short stint with Edgy), and I keep getting md5sum errors when I try to do the first round of updates that Synaptic automatically wants to do. I read about similar problems awhile back that people solved by pointing their us.archives sources to just archives or uk.archives. I tried both of those, and I get the same errors, pasted below. The thing is, I've installed Dapper on this machine with the same Live CD at least twice before without problems. When I first got this error last night, I thought it might have been because I added (uncommented) everything except the backports repositories before doing any upgrades. Since Ubuntu is so easy to install, to fix it, I just did a new install and made sure to do the upgrades before touching anything. I got the same errors in both cases. Thanks for any suggestions.

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb)
  MD5Sum mismatch


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-26-386_2.6.15-26.47_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-26-386_2.6.15-26.47_i386.deb)
  MD5Sum mismatch


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-27-386_2.6.15-27.48_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-27-386_2.6.15-27.48_i386.deb)
  MD5Sum mismatch


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/linux-restricted-modules-2.6.15-26-386_2.6.15.11-4_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/linux-restricted-modules-2.6.15-26-386_2.6.15.11-4_i386.deb)
  MD5Sum mismatch


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/linux-restricted-modules-2.6.15-27-386_2.6.15.12-1_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/linux-restricted-modules-2.6.15-27-386_2.6.15.12-1_i386.deb)
  MD5Sum mismatch

---

### Post by tommcd on 2006-12-02
Is this still happening? I read some posts where people reported temporary problems like this. Try to reload synaptic again (or sudo aptitude update) and see if it works. Other posts mentioned removing the "us" from us.archives like you tried. I assume this is a clean install of Dapper?

---

### Post by digeratess on 2006-12-02
> **tommcd said:**
> Is this still happening? I read some posts where people reported temporary problems like this. Try to reload synaptic again (or sudo aptitude update) and see if it works. Other posts mentioned removing the "us" from us.archives like you tried. I assume this is a clean install of Dapper?

I am still getting these errors. This is my second completely fresh install since Thursday. I have run update several times, including each time I changed my sources list. I ran it again just now just to see, and there was no change.

Any help is greatly appreciated. Like I said in my first post, I've already rebuilt once assuming that would fix this problem, but it hasn't. I don't know what to do when a fresh install doesn't work.

---

### Post by digeratess on 2006-12-02
I thought I would put the original /etc/apt/sources.list (which I copied before changing) back in place and try everything again. So I did and ran apt-get update. This resulted in a different error, below:

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release [34.8kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release [30.9kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages [619kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages [4571B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources [255kB]
74% [6 Packages bzip2 0] [8 Sources 10867/255kB 4%]
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Sub-process bzip2 returned an error code (2)
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources [1478B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages [129kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources [47.9kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Fetched 1123kB in 4s (265kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by digeratess on 2006-12-02
Problem solved!

After I got that different error and searched the forums for "sub-process bzip2", I found [this post]("http://ubuntuforums.org/showthread.php?t=192770") and followed its suggestion to change all my sources from http to ftp. That worked like a charm! Hooray. I don't know enough about how the repositories work to know, but it seems like some packages somewhere are messed up. For the record, I am posting the sources list that gave me the error and the one that didn't.

Gave Error, and for the record, I also tried this exact file except with archive and uk.archive instead of us.archive:

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

Did NOT give error:

```

deb ftp://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src ftp://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb ftp://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src ftp://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb ftp://archive.ubuntu.com/ubuntu/ dapper universe
deb-src ftp://archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb ftp://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src ftp://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb ftp://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src ftp://security.ubuntu.com/ubuntu dapper-security main restricted
deb ftp://security.ubuntu.com/ubuntu dapper-security universe
deb-src ftp://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by tommcd on 2006-12-03
Glad you fixed it. I'll have to keep that in mind, in case it ever happens to me. It seems (from the threads you linked to) that it is a problem with firewalls or proxies on the ubuntu http servers.

---

