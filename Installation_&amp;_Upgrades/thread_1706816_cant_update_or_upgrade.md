---
title: "cant update or upgrade"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by rawtoas on 2011-03-14
when i want to upgrade i get this error

Failed to fetch [http://ports.ubuntu.com/dists/karmic/Release](http://ports.ubuntu.com/dists/karmic/Release)  Unable to find expected entry  partner/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch [http://ports.ubuntu.com/dists/karmic-proposed/Release](http://ports.ubuntu.com/dists/karmic-proposed/Release)  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://ports.ubuntu.com/dists/karmic-updates/Release](http://ports.ubuntu.com/dists/karmic-updates/Release)  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://ports.ubuntu.com/dists/karmic-backports/Release](http://ports.ubuntu.com/dists/karmic-backports/Release)  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
help!

---

### Post by tommcd on 2011-03-14
Have you tried using a different mirror to update from? Just go to: system > administration > software sources (or the software sources from synaptic package manager) and try another mirror. Then run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
If it still fails, then post the contents of your *etc/apt/sources.list*. And post any files that may be in the */etc/apt/sources.d/* directory.

FYI: Ubuntu 9.10 will reach end of life (EOL) next month. You should upgrade to 10.04 ASAP. 
Or better yet, do a clean install of either 10.04 or 10.10.

---

### Post by rawtoas on 2011-03-14
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release powerpc (20090421)]/ jaunty main
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic restricted main
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic partner restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic partner

deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-security restricted main
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-security restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-security universe
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-proposed partner restricted main multiverse universe
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-proposed partner restricted main multiverse universe
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-updates partner restricted main multiverse universe
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-updates partner restricted main multiverse universe
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-backports partner restricted main multiverse universe
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-backports partner restricted main multiverse universe

---

### Post by tommcd on 2011-03-14
Try removing the Partner repos from Synaptic Package Manager, then reload the sources when prompted. Then see if you can run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Alternatively, you could just comment out (i.e., put a **#** in front of) any of the Partner repos in your /etc/apt/sources.list file. Then run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Also see this thread (post #4) for an alternative sources.list:
[http://ubuntuforums.org/showthread.php?t=1441906](http://ubuntuforums.org/showthread.php?t=1441906)
If you want to try that, backup your current sources.list before using the one posted there.

From some googleing I have done, this issue seems to be limited to Power PC versions of Ubuntu.

Have you tried using a different mirror, as I suggested in my last post???

---

### Post by rawtoas on 2011-03-14
i tried using the united states server and that adds more failed sources than the main

---

### Post by rawtoas on 2011-03-14
it worked, thanks for the help!

---

### Post by rawtoas on 2011-03-14
[SIZE=2][FONT=Arial Black]when i try to upgrade to 10.10  i get this error 
[/FONT][/SIZE]W:Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/maverick/Release](http://ports.ubuntu.com/ubuntu-ports/dists/maverick/Release)  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.
how do i fix it

---

### Post by Dutch70 on 2011-03-15
First of all, how are you attempting the upgrade?

---

### Post by tommcd on 2011-03-15
> **rawtoas said:**
> [SIZE=3][FONT=Arial Black]it worked, thanks for the help![/FONT][/SIZE]
Just out of curiosity, what exactly did you do to fix this?

---

### Post by rawtoas on 2011-03-15
> **Dutch70 said:**
> First of all, how are you attempting the upgrade?
update manager

---

### Post by Dutch70 on 2011-03-15
I'm not sure what to tell you, other than make sure you have all of the correct software sources enabled. 

Other than that, I can tell you that upgrades rarely work unless you have a very basic system without any real customizations. That is why everyone recommends a clean install when you want to upgrade to a newer version. If you have a separate /home partition, then it's a 15-20 install & you don't lose your files or ever your settings. If you don't have a separate /home, now would be a good time to create one, and I guess you can see why.

---

### Post by rawtoas on 2011-03-18
how can i tell if they are right

---

### Post by rawtoas on 2011-03-18
i removed the partner sources, i am now having the error with upgrading to 10.10
 W:Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/maverick/Release](http://ports.ubuntu.com/ubuntu-ports/dists/maverick/Release)  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)

---

### Post by CharlesA on 2011-03-18
Threads merged. Please stick to one thread please.

---

