---
title: "Repository access problems"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by notabot on 2008-04-27
I just upgraded to Hardy using the dvd distro and am now trying to upgrade the rest of my packages but am having lots of trouble accessing repositories. I'm not going via a proxy server but I'm getting behaviour like my proxy settings are wrong. I don't think I have any proxies set up.

Pressing Reload in Synaptic gives me a "Could not download all repository indexes" dialog box with 403 Forbidden errors on every line like this for example:
> Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/main/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/main/restricted/source/Sources.gz)  403 Forbidden

System|Preferences|Network Proxy (gnome-network-preferences) is set to "Direct internet connection"
and so is 
gksu gnome-network-preferences
The Synaptic Preferences|Network is set to "Direct connection to the internet".

Is there a guide somewhere that explains how Synaptic and/or the Update Manager use proxies? I found some bug reports that may be relevant but didn't help me, specifically Bug #21536.
After lots of failures, I added the local repositories that my ISP maintains to the sources.list file. The following shell approach then partially worked, but apt-get produces some 404 Not Found errors for the au repository and Synaptic still fails with 403 Forbidden errors for everything:
> export http_proxy=""
sudo apt-get update
sudo apt-get upgrade
but I don't know why I had to export http_proxy="".

Are there other places that proxies are defined? I can get to all the repositories via a web browser. I also tried pointing at repositories other than the main Australian one with no more luck.

My sources.list file is as follows:

> deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

deb [http://mirror.gamearena.com.au/ubuntu/](http://mirror.gamearena.com.au/ubuntu/) hardy main restricted universe
deb [http://mirror.gamearena.com.au/ubuntu/](http://mirror.gamearena.com.au/ubuntu/) hardy-updates main restricted universe
deb [http://mirror.gamearena.com.au/ubuntu/](http://mirror.gamearena.com.au/ubuntu/) hardy-security main restricted universe

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) main restricted universe multiverse

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-security main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-security main restricted universe multiverse

Any thoughts?

---

### Post by Bari on 2008-04-27
I am having the same problem with the UK repositories. They were working fine until around 1 week ago and then I get the same as you. I have also tried the Netherland ones with the same result.

---

### Post by notabot on 2008-04-27
Any luck accessing any repositories Bari? What about with apt-get?

The current state of affairs for me is that I can browse the packages using Synaptic but not install them - I have to use apt-get for that. I wonder if it's just a timeout problem and maybe Synaptic just has a very short timeout before it gives up. I suggest this because accessing the repositories with a browser was sometimes very slow.

---

### Post by Bari on 2008-04-27
I am still struggling with this I have tried a sudo apt-get update and all I got was

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-security/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

Before I got this I got a message saying /etc/apt/sources.list file malformed in line 22. On checking line 22 is part of some plain text which is commented out. But I must admit I don't really know what this file should say. It looks ok to me but here it is, it may help if you compare it with yours.

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319)]/ hardy main #restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy restricted web main
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates restricted web main
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security restricted web main
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security multiverse

or hopefully someone will check the files and tell us what is wrong.

---

### Post by Bari on 2008-04-27
SOLVED.... I tried again to update the repositories and got the usual reply:
[Http://gb.archive.ubuntu.com/ubuntu/dists/hardy/release](Http://gb.archive.ubuntu.com/ubuntu/dists/hardy/release)  unable to find web/binary-i386 packages in meta-index file (malformed release file?)  I also got the same message for /hardy-update/Release and /hardy-security/Release. I then went to the web pages for [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release) and the other two and found that in all the lists of packages there were no web/binary ones so I went and did a sudo gedit /etc/apt/sources.list and in line 4 and 8 and 41 of my file deleted the word web saved it and all seems to be working ok.  
Hope this helps

---

