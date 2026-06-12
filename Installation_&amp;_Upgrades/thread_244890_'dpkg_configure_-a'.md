---
title: "'dpkg configure -a'"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by norfin on 2006-08-27
so. running 'dpkg configure -a' bounces me to a server that is not sending me any information back. just keeps retrying connection.  

i get an erorr message trying to update my system. tells me to run 'dpkg configure -a' manually. when i run it it doesnt work. so how can i fix this problem. i need the package but i cant get it. is the server down? any thoughts?? help would be much appriciated =) thx..

---

### Post by Timokl on 2006-08-27
> **norfin said:**
> so. running 'dpkg configure -a' bounces me to a server that is not sending me any information back. just keeps retrying connection.  

i get an erorr message trying to update my system. tells me to run 'dpkg configure -a' manually. when i run it it doesnt work. so how can i fix this problem. i need the package but i cant get it. is the server down? any thoughts?? help would be much appriciated =) thx..

First we need to know **which** server dpkg tries to contact. Can you post your /etc/apt/sources.list into this thread.

To do this, open a terminal window and type

```
gedit /etc/apt/sources.list
```

The Text Editor Gedit will open and display the file. Please copy these lines into a new reply to this thread.

Bye,
Timo

---

### Post by norfin on 2006-08-27
thx. here is the info..

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates multiverse universe main restricted

---

### Post by norfin on 2006-08-27
and this is the message ive been getting by the way..

root@ninj4-desktop:/home/ninj4# dpkg --configure -a
Setting up setiathome (3.08-4) ...
setiathome-3.08.i686-pc-linux-gnu.tar not found in /tmp.
--10:06:19--  [ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar](ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar)
           => `/tmp/filexZYeYN'
Resolving alien.ssl.berkeley.edu... 128.32.18.176
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21...


i think that the server for ftp is down because it retrys and retrys and gets nothing

is there a site someone can redirect me to so i can get the file its trying to send.. 

thx.. much appriciated

---

### Post by anorexicpillow on 2006-12-02
BUMP!!

This is the exact same problem i am having right now! 


deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by matchstich on 2006-12-06
i got the same thing trying to install java runtime. cept i am a newbie and dont know how to run dpkg configure -a.

---

### Post by ubuntu27 on 2006-12-06
I don't know much about this.
But, when I've installed Kubuntu desktop (I have Ubuntu)
```
sudo aptitude install kubuntu-desktop
```
and decided to remove kubuntu desktop after trying it out.
```
sudo aptitude remove kubuntu-desktop
```

in the process of removing all those packages, the electricity or whatever responsible it is, made my computer turn-off.
After that (I turned on the como again)
I run sudo aptitude remove kubuntu-desktop again
and it told me to run dpkg configure -a'

So I did. I couldn't do any aptitude or apt commands unless I "dpkg configure -a' :)

so, this is just me guessing, but

dpkg configure -a'  must be in order to clean out (fix) some error in apt or related app. 

Now, anybody knowledgeable should correct me :)


PS:

**you have to run with sudo**

```
sudo dpkg configure -a
```

---

