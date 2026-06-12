---
title: "Error Line 55"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by RealBardock on 2010-03-12
Iam new in linux and this is my first error.I tried to change the basic toolbar to cairo dock,a tutorial that i found told me to write in terminal
 gksu gedit /etc/apt/sources.list.d/winehq.list
so i write it and a window opened,i couled not find the text that told me(the tutorial i mean)so i closed the window,after that i keep taiking the same error

E: Type ‘sudo’ is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

now whene i got in the winehq.list the text has gone and i take this error in update manager,my software center doesn't work and my terminal whenever i type sudo commands says

E: Type ‘sudo’ is not known on line 55 in source list /etc/apt/sources.list
.
HELP

---

### Post by plucky on 2010-03-12
> **RealBardock said:**
> Iam new in linux and this is my first error.I tried to change the basic toolbar to cairo dock,a tutorial that i found told me to write in terminal
 gksu gedit /etc/apt/sources.list.d/winehq.list
so i write it and a window opened,i couled not find the text that told me(the tutorial i mean)so i closed the window,after that i keep taiking the same error

E: Type ‘sudo’ is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

now whene i got in the winehq.list the text has gone and i take this error in update manager,my software center doesn't work and my terminal whenever i type sudo commands says

E: Type ‘sudo’ is not known on line 55 in source list /etc/apt/sources.list
.
HELP

From a terminal ```
cat /etc/apt/sources.list
``` and post the output to the forum.One of the lines in your sources.list is incorrect,might be more.

---

### Post by RealBardock on 2010-03-12
alex@alex-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic main restricted
deb-src [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic-updates main restricted
deb-src [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic universe
deb-src [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic universe
deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic-updates universe
deb-src [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic multiverse
deb-src [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic multiverse
deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic-updates multiverse
deb-src [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic-security main restricted
deb-src [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic-security main restricted
deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic-security universe
deb-src [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic-security universe
deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic-security multiverse
deb-src [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) karmic-security multiverse
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) karmic main ## Cairo-Dock-PPA
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5


sudo apt-get update

clear
--------------------------------------------------------
Thats what i get

---

### Post by jocko on 2010-03-12
> **RealBardock said:**
> ```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5


sudo apt-get update

clear
```
Remove these lines (starting from line 55). They do NOT belong in sources.list.

---

### Post by RealBardock on 2010-03-12
I write what ever Terminal show me , i din't write them after if you mean that

---

### Post by howefield on 2010-03-12
Open a terminal (Applications > Accessories > Terminal) and type 

```
gksudo gedit /etc/apt/sources.list
```

Then remove the last 3 lines and save.

Still in terminal type

```
sudo apt-get update
```

If you still want to  add that key, then do it in the terminal.

---

### Post by RealBardock on 2010-03-12
Tnx Howefield,as far everythink works perfect!!!!:P

---

### Post by howefield on 2010-03-12
> **RealBardock said:**
> Tnx Howefield,as far everythink works perfect!!!!:P

Excellent. 

Perfect is good. :)

---

### Post by RealBardock on 2010-03-12
I will ask somethink stupid,how do i make a new thread?

---

### Post by howefield on 2010-03-12
> **RealBardock said:**
> I will ask somethink stupid,how do i make a new thread?

Same way you did the last time...

Go into the forum that you want to post in and press the New Thread button, as per this screen shot of the top right quarter of the screen.

---

### Post by RealBardock on 2010-03-12
Tnx i lag

---

