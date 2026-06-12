---
title: "error: &quot;could not download all repository indexes&quot;"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by ab525 on 2007-07-07
I started to install beryl, using this guide: [http://pimpyourlinux.com/linux-feature-review/beryl-an-easy-graphical-howto/](http://pimpyourlinux.com/linux-feature-review/beryl-an-easy-graphical-howto/) .  However, I'm getting the following message telling me there's a problem with the repositories.  I found an old thread on here where the issue was a few typos in the sources.list file, so I included that in case.

```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz: 302 Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz: 302 Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz: 302 Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz: 302 Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz: 302 Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz: 302 Found
http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz: 302 Found [IP: 91.189.89.6 80]
http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz: 302 Found
http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz: 302 Found [IP: 91.189.89.6 80]
http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz: 302 Found
http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz: 302 Found [IP: 91.189.89.6 80]
http://ubuntu.beryl-project.org/dists/edgy/main/binary-i386/Packages.gz: 302 Found [IP: 208.113.193.9 80]
```

Here's my sources list:

```
$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://ubuntu.beryl-project.org edgy main
```

I know this may be a simple problem, but I'm new to Linux, and am still learning the fundamentals.

---

### Post by Circuit99 on 2007-07-22
I don't know if this will help but I had similar problem with Mint until today. I got error message 302 repos not downloading, even using sudo apt-get upgrade and mint install hanged and synaptic.  I was not to bothered because you could still download via link from error,  pain in the neck when you got more than 2 package updates. 
I multi-boot and use Ubuntu fiesty which worked fine with no problems. 

The system I have Abit KW7 with a built in sound card and upgraded the video card to ATI RADEON X1650 PRO, just upgraded new drivers from ATI (AMD). I wanted to use a game port based joystick so I put in a 
Xwave-QS3000A sound card and hoped it would get detected. What happened the sound card became the main output, and disabled on board sound card, no luck with game port. Please note I also have to 2 usb joypads  working fine. I disabled onboard sound card via bois on motherboard.

I booted up into mint to see what had happened with the joypad and game port. What I found when I tired update  manager it did not report error 302.
This what I did, I opened a terminal and, 

[PHP]sudo apt-get update
[/PHP]
[PHP]sudo apt-get upgrade
[/PHP]

then  all the packages started to updating and now synaptic works and mint install. 

My suggestion is look at your hardware setup and try disabling sound card, Beryl will need to be cleaned out.

DO NOT DO ANYTHING TO HARM YOUR SYSTEM. [-X
 
Bear in mind Mint Cassandra and Ubuntu Fiesty are 90% or so the same. I think the problem lies with way either hardware setup or the way ATI drivers install in my case.  :):):)

Have a look at your hardware setup
Post them here and let me know how you go.

Good Luck !!!!!

---

