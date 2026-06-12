---
title: "SYnaptic and apt-get will not work."
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by jordan420 on 2007-08-24
Hello, i am having a problem. Actually it is three problems but i feel they are directly related as they all display the same error message. The problem started when i attempted to install the 3d desktop. i downloaded and began the install of the lg3d-jdk file in synaptic but after waiting for a relatively long time i had a hunch something was wrong so i peeked into the terminal thing and there was a license statement only i couldnt agree to it, only look at it. so because it would not let me close synaptic because it still thought i was installing something so i had no choice but to turn my cpu off and restart. however when i restarted and attempted to use apt-get command to install i got:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package lg3d-jdk needs to be reinstalled, but I can't find an archive for it.

 i thought this was a little wierd so i attempted to open up synaptic and remove the obviously faulty package as i have heard that if you have one broken packaGE you cant update or install for some reason, but only this time it wouldnt let me open synaptic either, as it displayed the same error message. it does the same thing when i attempt to update. also adept does open for me but only in read only mode, so if someone could tell me how to open adept under root or maybe has another solution i would be thankful. Peace and chicken-grease!

---

### Post by Pumalite on 2007-08-24
Try:

sudo dpkg --configure -a

If it doesn't work, try: sudo dpkg --remove --force-remove-<packagename>

Or:  sudo apt-get remove --purge <packagename>

---

### Post by jordan420 on 2007-08-29
hello,
thanks for the reply but i am afraid it hasnt helped. dpkg displays the following :

jordan@jordan-laptop:~$ sudo dpkg --remove --force-remove-<lg3d-jdk>
bash: syntax error near unexpected token `newline'
 
and apt-get... this.

jordan@jordan-laptop:~$ sudo apt-get install lg3d-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package lg3d-jdk needs to be reinstalled, but I can't find an archive for it.

 no matter which operation i choose. any further suggestions would be appreciated, as i miss my updates and new installs. thanks!!!

---

### Post by Pumalite on 2007-08-29
The command is this: sudo dpkg --remove --force-remove-lg3d-jdk

---

### Post by bapoumba on 2007-08-29
I cannot find the package lg3d-jdk in any of the ubuntu repositories. Were did you install it from in the first place? Can you please post your sources.list?
```
cat /etc/apt/sources.list
```

---

### Post by jordan420 on 2007-08-31
hello,
 The package came from the java website. this is the link: [https://lg3d-core.dev.java.net/binary-builds.html](https://lg3d-core.dev.java.net/binary-builds.html)
and this is the output from the command you gave me:
```
jordan@jordan-laptop:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

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
deb-src http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
```

also, i found the code to run adept as root, and it is no help, i recieve a similar error message (the package is in a very inconsistent state, removing it may break other packages) when i try to install or reinstall a package. the only difference is that it actually lets me into the program, and lets me view packages. i checked the lg3d-jdk package, and it shows up as installed, but it takes up 0 bytes, so it is most definetly
that reason.

---

