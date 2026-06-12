---
title: "Ubuntu 8.04 problems"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by al3x3y on 2008-07-18
Hello guys.I'm new around here and also a newbie using ubuntu :).
So a few weeks ago i installed Ubuntu 8.04 and i used my Nvidia 8600GT with it.Everything was smooth and fine bun 2 days ago i got my Nvidia 8800GTS G92 and now when i try to use the Update manager i get a error saying:
[IMG]http://i35.tinypic.com/14bqog2.png[/IMG]


Thanks in advance to all that will post here :)

---

### Post by Pumalite on 2008-07-18
Post:
cat /etc/apt/sources.list

---

### Post by al3x3y on 2008-07-18
```
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
## Avant Window Navigator
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator

deb  http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
“deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main”
deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main

echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'
sudo tee -a /etc/apt/sources.list
exit
deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main

```

---

### Post by Pumalite on 2008-07-18
Comment out (put a # in front) of these lines:
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
Remove these:
“deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main”
echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main'
sudo tee -a /etc/apt/sources.list
exit
Save, exit.
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by al3x3y on 2008-07-18
> **Pumalite said:**
> Comment out (put a # in front) of these lines:
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
Remove these:
“deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main”
echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main'
sudo tee -a /etc/apt/sources.list
exit
Save, exit.
sudo apt-get update
sudo apt-get dist-upgrade

i tried but it doesn't work.like i said before i'm noob with ubuntu...but still doesn't works

---

### Post by avtolle on 2008-07-18
You need to edit /etc/apt/sources.list. To do so, you will need to open an editor. I prefer nano, and from the terminal I would do```
cp /etc/apt/sources.list /etc/apt/sources.list.bak #back up, just in case
sudo nano /etc/apt/sources.list #open file for editing
```
then, comment out and delete the lines Pumalite indicated. To write the changes, you would do a CTRL-o, followed by <enter> to select the default file name, then CTL-x to exit nano. While still in the terminal, then run ```
sudo apt-get update
sudo apt-get dist-upgrade
```as Pumalite has suggested.

The problem has nothing to do with replacing the graphics card, and everything to do with your /etc/apt/sources.list. The suggestions he made will hopefully fix the problem. Good luck.

---

