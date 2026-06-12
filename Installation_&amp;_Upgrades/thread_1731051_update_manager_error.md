---
title: "update manager error"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by JesMFN on 2011-04-16
so when i check for updates it gets to 77 out of 80 percent and then sends me this error. how do i fix it?

W: GPG error: [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81D820A9BB7A1A83
W: Failed to fetch [http://www.statux.org/ubuntu/dists/jaunty/Release.gpg](http://www.statux.org/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'www.statux.org'

W: Failed to fetch [http://www.statux.org/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://www.statux.org/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not resolve 'www.statux.org'

W: Failed to fetch [http://repos.eeebuntu.org/dists/eb3/universe/binary-i386/Packages](http://repos.eeebuntu.org/dists/eb3/universe/binary-i386/Packages)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
&#65533;&#65533;

---

### Post by Dutch70 on 2011-04-16
What version of Ubuntu are you using? It looks like there are sources in there for Jaunty.

Also, [www.statux.org](www.statux.org) does not exist.

Please post the output of...
```
gksudo gedit /etc/apt/sources.list
```

Paste the output between [CODE][ /CODE] tags using the "#" symbol in the toolbar.

---

### Post by JesMFN on 2011-04-16
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty main restricted universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 universe

---

### Post by Old_Grey_Wolf on 2011-04-17
> **JesMFN said:**
> 
W: GPG error: [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81D820A9BB7A1A83


This means you need to get the GPG key to authenticate the package before it will download.

Enter these commands in a terminal to get the GPG key and try to update again.
```
gpg --keyserver keyserver.ubuntu.com --recv 81D820A9BB7A1A83
gpg --export --armor 81D820A9BB7A1A83  | sudo apt-key add -
```

---

### Post by dino99 on 2011-04-17
Jaunty is outdated, meaning no more supported, so no repo reachable, that it

---

### Post by JesMFN on 2011-04-20
I'm trying to update, but running into problems... i think it's easier if someone gives me the commands and i give the feed back.

---

### Post by mörgæs on 2011-04-20
9.04 is unsupported, and 9.10 will be in a few days. I would rather recommend a back up and a clean install of 10.04.2 or 10.10.

This will also give you the newest Grub automatically.

---

### Post by JesMFN on 2011-04-23
*Note: if you are  a person that posts on a thread one time and never looks back please don't bother. i need help and i'm not going to take guesses my netbook is almost dead. 

ok here is the info. I've been trying to update my netbook forever. no one on this forum seemes to be able to help. no im pretty sure i've managed to upgrade to jaunty, but im not sure. so im going to need to know how to do that. after extensive time in trying to update, i am clueless. my update manager does not seem to work. I'm not sure why it just gives me error after error. about repositorys not being avaliable. i can post it if you like, but im more worried about udpgrading. so how should i upgrade? is there a command? i tried downloading and installing off and SD card, but it would not work and i tried everything. so any suggestions?

---

### Post by Joe of loath on 2011-04-23
What's the output of:

```
cat /etc/apt/sources.list
```
```
sudo apt-get update
```

---

### Post by mikewhatever on 2011-04-23
Looks like your questions had been answered in one of the previous threads.
[http://ubuntuforums.org/showthread.php?t=1731051](http://ubuntuforums.org/showthread.php?t=1731051)
Why start new ones on the same subject?

---

### Post by anjilslaire on 2011-04-23
Try this:
press Alt+F2, type in "update-manager -d" (without the quotes), and press Enter. 
Follow the prompts

---

### Post by JesMFN on 2011-04-23
ok joe of loath i got this: # deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty main restricted universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 universe

and other dude, because no ones answers worked and no one revisits old posts anymore :p

---

### Post by snowpine on 2011-04-23
Why not just do a fresh install of the current release (10.10)?

---

### Post by JesMFN on 2011-04-23
atl f2 thing did nothing but open update manager. which doesn't work.

---

### Post by JesMFN on 2011-04-23
> **snowpine said:**
> Why not just do a fresh install of the current release (10.10)?

i already explained i tried. i cant. i tryied i put it on a sd and tried to install it. i couldnt get it to boot

---

### Post by mikewhatever on 2011-04-23
> **JesMFN said:**
> 
... 
and other dude, because no ones answers worked and no one revisits old posts anymore :p

Do me a favor...! You've started multiple threads on this, and then abandoned them all. I wonder if you want to be taken seriously here.

---

### Post by JesMFN on 2011-04-23
do me a favor and move on off this forum. i need help not to be ridiculed.

---

### Post by snowpine on 2011-04-23
> **JesMFN said:**
> i already explained i tried. i cant. i tryied i put it on a sd and tried to install it. i couldnt get it to boot

Your posts are difficult to understand. Here are simple 1-2-3-4 instructions for installing the current Ubuntu Netbook release:

[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

If you prefer to update your end-of-life release instead, you can follow these instructions:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Blasphemist on 2011-04-23
I believe the sources have been closed for that old version. Have you tried an install of 10.04? With a netbook I understand that may mean you'd have to do that with a usb device. Is that the case for you or do you have a cd drive?

---

### Post by cariboo on 2011-04-23
> **JesMFN said:**
> *Note: if you are  a person that posts on a thread one time and never looks back please don't bother. i need help and i'm not going to take guesses my netbook is almost dead. 

ok here is the info. I've been trying to update my netbook forever. no one on this forum seemes to be able to help. no im pretty sure i've managed to upgrade to jaunty, but im not sure. so im going to need to know how to do that. after extensive time in trying to update, i am clueless. my update manager does not seem to work. I'm not sure why it just gives me error after error. about repositorys not being avaliable. i can post it if you like, but im more worried about udpgrading. so how should i upgrade? is there a command? i tried downloading and installing off and SD card, but it would not work and i tried everything. so any suggestions?

Please don't try to dictate how volunteer help is given. If you demand help, I would suggest you look [here]("http://www.ubuntu.com/business/services/desktop")

---

### Post by rpm13 on 2011-04-24
> **JesMFN said:**
> *Note: if you are  a person that posts on a thread one time and never looks back please don't bother. i need help and i'm not going to take guesses my netbook is almost dead.

I understand ur frustration and I dont promise to be available (wont be on my m/c for a few days)

Still heres some experience of mine that you may benefit from knowing:

1. Trying to upgrade from something 'super-old' (ie older than obsolete) generally is an unhappy experience on ubuntu.  Just install new (hopefully youve backed up :-) )
2. update-manager I dont use.  I prefer aptitude upgrade and aptitude full-upgrade
3. For those intending to be long-term users of linux better to have a 'medium-sophisticated' partition setup such as home separate from OS so that such upgrades/reinstalls next time round are more painless
4. To fast forward from old to new with all the packages of old, you may want to collect your current package list with
dpkg --get-selections
> 
ok here is the info. I've been trying to update my netbook forever. no one on this forum seemes to be able to help. no im pretty sure i've managed to upgrade to jaunty, but im not sure. so im going to need to know how to do that. after extensive time in trying to update, i am clueless. my update manager does not seem to work. I'm not sure why it just gives me error after error. about repositorys not being avaliable. i can post it if you like, but im more worried about udpgrading. so how should i upgrade? is there a command? i tried downloading and installing off and SD card, but it would not work and i tried everything. so any suggestions?

---

### Post by JesMFN on 2011-04-24
Blasphemist: no cd drive. its an asus netbook.
 
cariboo907: i didnt mean to come off demanding im just looking for some help, because i never seem to get any unless i ask the guy i know for real and even he is confused on upgrading. so sorry. your whole comment was irrelevent. so thanks again. 
 
rpm13: ill look into your updater you use. i do have two seperate computers (not ubuntu) and im nto sure i understand that last part. "package list with
dpkg --get-selections"

---

### Post by snowpine on 2011-04-24
> **JesMFN said:**
> i didnt mean to come off demanding im just looking for some help, because i never seem to get any unless i ask the guy i know for real and even he is confused on upgrading. so sorry. your whole comment was irrelevent. so thanks again. 

"How to upgrade an end-of-life Ubuntu release" was not helpful???

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by rpm13 on 2011-04-24
> **JesMFN said:**
> 
rpm13: ill look into your updater you use. i do have two seperate computers (not ubuntu) and im nto sure i understand that last part. "package list with
dpkg --get-selections"

Basically you can choose to upgrade or else you can choose to install freshly.  Upgrading can work but often there are glitches, and the more old your running version, the more glitches.  

So you may end up re-installing even though you would prefer to upgrade.

How do you 'fast-forward' all the packages you have installed across months and years?
```
dpkg --get-selections
```
gets you everything you have currently installed.
Now giving that same list to apt to reinstall is not advisable because some packages may be obsolete conflict etc

But it can jog your memory to get upto speed in your new installation more quickly.

---

### Post by JesMFN on 2011-04-24
snowpine: plz the conversation is over, but thanks.
 
rpm13: thanks dude :D ill try that command in a few minutes. got to go get my lab top ill give you the outcome

---

### Post by Elfy on 2011-04-24
Threads merged - do not post duplicates.

---

### Post by JesMFN on 2011-04-24
ok thanks... sorry

---

### Post by JesMFN on 2011-04-25
rpm13 this does not seem to be helping me update... it just reinstalled thing like you said. no effect tho.

---

