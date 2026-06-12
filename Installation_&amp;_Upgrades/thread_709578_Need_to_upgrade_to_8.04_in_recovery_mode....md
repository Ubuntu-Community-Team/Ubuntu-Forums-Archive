---
title: "Need to upgrade to 8.04 in recovery mode..."
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by Sir Paul on 2008-02-27
I was wondering how to upgrade to 8.04 from 7.10 in recovery mode?

Thanks,

Paul

---

### Post by Pumalite on 2008-02-27
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Pumalite on 2008-02-27
You might want to try this:
sudo sed -i 's/gutsy/hardy heron/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by zvacet on 2008-02-27
You don´t need** sudo** in recovery mode.

---

### Post by Pumalite on 2008-02-27
Quite right. My mistake.

---

### Post by Sir Paul on 2008-02-27
Thanks!

---

### Post by Sir Paul on 2008-02-27
sudo sed -i 's/gutsy/hardy heron/' /etc/apt/sources.list 

when I did that command it just gave me:

<
(and whenever I pressed enter another one popped up...any idea?

---

### Post by Pumalite on 2008-02-27
Take out the 'sudo'

---

### Post by Sir Paul on 2008-02-27
I believe I tried both ways and I think I got the same thing...but I will try again...

---

### Post by confused57 on 2008-02-27
> **Sir Paul said:**
> I believe I tried both ways and I think I got the same thing...but I will try again...
Maybe this will work:
```
sed -e 's/\sgutsy/ hardy/g' -i /etc/apt/sources.list
```

then do:
apt-get update
apt-get dist-upgrade

Added:  If the first command works for changing your sources.list, you might want to open your sources.list & make sure any cdrom repositories are commented out(place a # in front):
```
nano /etc/apt/sources.list
```

---

### Post by Sir Paul on 2008-02-28
Thanks I'll try it...

---

### Post by Sir Paul on 2008-02-28
So I tried it out...I think I messed things up even more...it isn't fetching any updates it seems as if all the the resps. are wrong...maybe I should just tell you the other problem I have maybe you can help me with that...I can't startx...it doesn't load...something said:

> /etc/gdm/failsafeXServers: line 47 [: too many arguments 
Waring: Could not retrieve EDID because get-edid is not installed(1)

So I tried apt-get install get-edid ...didn't work
I also tried apt-get install edid ...didn't work....

Any ideas?

---

### Post by confused57 on 2008-02-28
> **Sir Paul said:**
> So I tried it out...I think I messed things up even more...it isn't fetching any updates it seems as if all the the resps. are wrong...maybe I should just tell you the other problem I have maybe you can help me with that...I can't startx...it doesn't load...something said:



So I tried apt-get install get-edid ...didn't work
I also tried apt-get install edid ...didn't work....

Any ideas?
If you can, you might want to check your sources.list to see that all the repositories have been changed to hardy:
```
nano /etc/apt/sources.list
```
It would probably be advisable to comment out any 3rd party repos.

You could also try "re-running" the upgrade process:
```
apt-get update && apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
``` 

Upgrading from one stable version to another stable version can be problematic, even more so upgrading to a development version.

---

### Post by Sir Paul on 2008-02-28
Can you show me what the /etc/apt/sources.list is supposed to look like after I put switch everything to hardy?

---

### Post by Pumalite on 2008-02-28
Delete.

---

### Post by confused57 on 2008-02-28
Here's my Hardy /etc/apt/sources.list that I installed at Alpha2:
```
# 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha i386 (20071129.5)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha i386 (20071129.5)]/ hardy main restricted
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
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse    
```

---

### Post by Sir Paul on 2008-02-28
Thanks for your help...I ended up fixing the problem a different way...I went to the /etc/X11/xorg.conf and ran the command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
 suggested to reonfigure and now everythings working fine so I can upgrade the normal way now...Thanks again!

---

