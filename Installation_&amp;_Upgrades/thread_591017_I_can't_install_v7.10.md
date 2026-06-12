---
title: "I can't install v7.10"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by molly.moggins on 2007-10-25
I have been trying to upgrade from Feisty 7.04 to Gutsy 7.10 but I keep on getting the following errors;

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve ‘wine.lowvoice.nl’
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_GB.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_GB.bz2) Could not resolve ‘wine.lowvoice.nl’
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.gz) Could not resolve ‘wine.lowvoice.nl’

I have a failed installation of Wine that I cannot remove from my PC. 

Has anyone got any ideas what I can do to fix this problem?

I don't actually want Wine anyway. How do I get rid of it if it is the problem that is stopping the Ubuntu upgrade?

:confused::confused::confused::confused:

---

### Post by mikewhatever on 2007-10-25
Can you post your sources.list. 
> cat /etc/apt/sources.list

---

### Post by taurus on 2007-10-25
Why don't you edit /etc/apt/sources.list and remove all the repos regarding wine.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by tipiglen on 2007-10-25
I have a problem which may also involve apt-get.

I went through serial upgrade from 6.06, 6.10, 7.04 to 7.10 and was offered a 'restricted' thingy which seems to have thrown my display drivers out of whack.  Now everything boots, but the screen is screwed sideways.  I can hear the drumbeat and can login, but still no useable display.

Am going to look in sources and var/log to see if I can remove the culprit, but would love a few helpful hints if there are any going

Salaam/Shalom/Shanthi/Dorood/Peace
   Namaste  -ed

---

### Post by tipiglen on 2007-10-25
info at bottom of last post is not for the machine with problems.  It's an elderly celeron 633MHz with a dodgy cd drive.
Salaam/Shalom/Shanthi/Dorood/Peace
   Namaste  -ed

---

### Post by molly.moggins on 2007-10-25
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
carole@carole-desktop:~$ 

Is that what you meant?

What should i do next?

I am not really very techie.

Should I just delete the line where it refers to wine?

I know that URL doesn't actually exist.

---

### Post by taurus on 2007-10-25
Personally, I would edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and delete all those lines at the end.

```

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

```
Then, save the changes and at the prompt, run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by molly.moggins on 2007-10-27
Thanks,

I edited out those lines mentioned and Gutsy upgraded perfectly.

I do have one question though, I have an update pending for nswrapper but when I try to run it I get the following error;

E: /var/cache/apt/archives
nspluginwrapper_0.9.91.5-1ubuntu1_amd64.deb: trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer.bin', which is also in package nspluginwrapper-i386

Two questions, firstly do I need this? I did a nswrapper fix to make Flash work and I think I have to use the i386 version of Flash. Secondly, can I remove this update from the list of pending updates if I don't?

---

