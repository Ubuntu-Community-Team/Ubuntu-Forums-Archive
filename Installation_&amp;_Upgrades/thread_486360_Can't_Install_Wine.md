---
title: "Can't Install Wine?"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by chris_504 on 2007-06-27
I'm running Ubuntu-feisty 7.04 x64 edition.  Synaptic is up to date with all the repo's enabled. When i try to install wine using 'apt-get' this is what i get.

chris@chris-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

Kindly Help.

---

### Post by Keisad on 2007-06-27
Install it using synaptic!

There is a possibility that you aren't spelling the exact name of the package. Use the search tool in the synaptic package manager to deal with that.

---

### Post by chris_504 on 2007-06-27
Synaptic lists around 21150 packages & my system is up-to-date.

Here's the screen shot of synaptic when i search for wine.

[[IMG]http://img165.imageshack.us/img165/4016/screenshotsynapticpackaky6.th.png[/IMG]](http://img165.imageshack.us/my.php?image=screenshotsynapticpackaky6.png)

Here's the content of my source list. 
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe


---

### Post by Keisad on 2007-06-27
Download libwine.

It is what you are looking for.

---

### Post by chris_504 on 2007-06-27
When i try to install libwine this is what get
[[IMG]http://img146.imageshack.us/img146/1359/screenshotsynaptic1wn5.th.png[/IMG]](http://img146.imageshack.us/my.php?image=screenshotsynaptic1wn5.png)

---

### Post by Ptero-4 on 2007-06-27
You need another repo (look around for automatix2 or easyubuntu, one of those adds the wine repo).

---

### Post by Keisad on 2007-06-28
Or possibly right click on libwine, scroll down to mark recommended packages and install them. Do the same for suggested, if there are any.

---

### Post by equihenk on 2007-06-29
Hey,

I was looking for an answer for this and found this topic. Then one google click further I found the solution so I figured I do my good deed, press back on browser, register here and tell ya ;)

Here you can find a repository to add for Feist:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Edit: and there is a hack to get it running on 64 bits.
Edit: and appearently the hack is not needed for feisty. 

Love/peace
Henk

---

