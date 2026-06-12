---
title: "Help Needed- Texmaker and Movie Player/Banshee Player"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by satyamM on 2012-02-12
So Finally I shifted to Ubuntu from Windows after much of discussions and advices.....!!!
I installed 10.04 through a CD.

**I tried to install TexMaker (which I used in Windows so frequently for my academic work) through Ubuntu Software Center but did not get success. I also tried through Terminal but it says "Couldn't Find Installation Package" .........same two processes I did for Plugin required to play movies in Movie Player but was not succeeded..!!...**

Can Anyone help me in the installation of the two..?

_My /etc/apt/sources.list file says following:_

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
```

---

### Post by satyamM on 2012-02-12
One thing more I am in proxy server network which uses proxy authentication for users.

---

### Post by satyamM on 2012-02-23
So I somehow found solutions for both the things........I edit online my pdf documents and save them and regarding movie player..somehow after cracking head  and updating packages in Synaptic Manager....I was able to install VLC which is the solution of my multimedia things.

[B]
Next thing in which I am in search is Bluetooth working.....still not able to configure Bluetooth..how does it work.....It is always off although in task bar panel(upper right) when I click on it it shows "Turn off Bluetooth" which means its ON...!!!!

Can anyone help me in this..?[/B]

---

### Post by Adrian98 on 2012-02-23
Have you tried the wine emulator.. It may solve your problem..

---

### Post by cortman on 2012-02-23
Hi, welcome to Ubuntu!

Texmaker is available in the Ubuntu repositories. Have you tried installing via

```
sudo apt-get install texmaker
```

in the terminal? If that doesn't work, post all error messages.

I've installed plugins in Movie Player by attempting to play a file, getting the message that says "plugins needed" and following the message box instructions (I believe it downloaded and installed the plugins within Movie Player) but if VLC is working for you, great!
Is your Bluetooth built into your PC or from a dongle? If it's part of your PC, post some info on your computer (make, model number, etc.,) and any info you can get on the Bluetooth adapter.

---

