---
title: "can't update natty main sources"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by 3xp10r3r|X13 on 2011-05-18
[FONT=Courier New]Hello there,
I've got the following problem:

Since a week or so I don't receive any updates from the launchpad natty mainsources. I just wanted to have a look, if some bug fixes would be out there (searching for available updates using the update manager - kpackage - usual ubuntu software center) and suddenly the following error message popped up:

E: Error [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main/Sources Sources
404 Not Found

I posted a thread concerning this topic already but if there are two out there it will attract more attention --> solution really needed

However I would really appreciate it if somebody would offer a soluton or at least some advice

--> ANY ADVICE IS REALLY NEEDED

So thanks for any replies:)[/FONT]

---

### Post by zvacet on 2011-05-18
Witch PPA you want to add to your source list.I ask that because link in your post look like [this.]("http://ppa.launchpad.net/")

---

### Post by 3xp10r3r|X13 on 2011-05-19
[FONT=Courier New]Sry, but the link is just part of the error message. So the whole thing is part of the PPA I've already added.

Only problem is that it doesn't update... :(
[/FONT]

---

### Post by zvacet on 2011-05-19
Does that PPa have packagfes for Natty?can you post output of 


```
cat /etc/apt/sources.list
```

---

### Post by 3xp10r3r|X13 on 2011-05-19
# deb cdrom:[Kubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty partner
# deb-src [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) natty main
deb-src [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) natty main



deb [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources
deb-src [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources

that's about it, so what do I have to replace, change or delete

By the way, thanks for sticking to this :)

---

### Post by zvacet on 2011-05-20
PPPA lines make all the trouble.They are not pointing at some specific PPA.In terminal

```
gksudo gedit /etc/apt/sources.list
```

remove PPA lines and save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by 3xp10r3r|X13 on 2011-05-20
Wow, this worked perfectly :D

But I've still got a question:

I understand that if I remove the repos, which are causing the trouble, apt won't try to update those and therefore there isn't the possibility that they cannot be found.

BUT

How am I meant to get PPA updates now?

---

### Post by oldos2er on 2011-05-20
Which PPA are you needing updates for?

---

### Post by 3xp10r3r|X13 on 2011-05-20
vlc virtual box skype --> the usual stuff, so as I've just deleted the repos for all those, where am I going to get updates from?

---

### Post by zvacet on 2011-05-20
If you want to add ppa for some package you have to find it on Launchpad.I found [this]("https://launchpad.net/~videolan/+archive/master-daily") for **vlc**.If you want to ad other PPA´s then look for them [here.]("https://launchpad.net/ubuntu/+ppas")Of course packages have to match your ubuntu version.

---

### Post by 3xp10r3r|X13 on 2011-05-21
Thanks to everybody, you helped me a lot :)

---

### Post by spleach on 2011-05-24
I'm getting a very similar problem, but I don't have any ppa sources listed in /etc/apt/sources.list

I see this is solved, but the solution doesn't work for me... Can someone help me with this?? Looks like there's apt sources that aren't listed in /etc/apt/sources.list
My error messages:-

```

...
Hit http://gb.archive.ubuntu.com natty-security/main Sources         
Err http://ppa.launchpad.net natty/main Sources                                            
  404  Not Found
Err http://ppa.launchpad.net natty/main amd64 Packages                                     
  404  Not Found
...
Fetched 6,939 B in 24s (287 B/s)
W: Failed to fetch http://ppa.launchpad.net/scipy/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/scipy/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

My sources.list file:-

```
deb http://gb.archive.ubuntu.com/ubuntu natty main restricted universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu natty-updates main restricted universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu natty-security main restricted universe multiverse

# deb http://packages.medibuntu.org/ natty free non-free # disabled on upgrade to natty
# deb http://dl.google.com/linux/deb/ stable non-free main # disabled on upgrade to natty

deb http://archive.canonical.com/ubuntu/ natty partner
deb-src http://archive.canonical.com/ubuntu/ natty partner
# deb http://download.virtualbox.org/virtualbox/debian natty non-free # disabled on upgrade to natty


deb-src http://gb.archive.ubuntu.com/ubuntu natty main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu natty-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu natty-security main restricted universe multiverse
```

---

### Post by 3xp10r3r|X13 on 2011-05-26
This is just a suggestion, but could it be, that you've used nano to display them and forgot to scroll down?
--> They are at the bottom of the list

if this wasn't the problem, please tell me :)

---

### Post by oldos2er on 2011-05-26
PPA .list files usually install to /etc/apt/sources.list.d/ , so check in that folder for files with "scipy" in their name.

---

### Post by MartynHaigh on 2011-06-13
Same problem here.

I'm getting this error when I try to update:

    E: Error [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources
    404 Not Found


and sometimes along with this I get

    E: Error [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages
    404 Not Found


My sources.list file is:

# deb cdrom:[Kubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427)]/ natty main restricted 

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty universe 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty universe 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates universe 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty multiverse 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty multiverse 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates multiverse 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse 
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security main restricted 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security universe 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security multiverse 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security multiverse 

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty partner 
deb-src [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty partner 

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) natty main 
deb-src [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) natty main 
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner 
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner 

deb [http://repository.spotify.com/](http://repository.spotify.com/) stable non-free 
# deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/) lucid main 
# deb-src [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/) lucid main 
 

and I don't seem to have any scipy files/folders:

[email]martyn@ubuntu:/etc/apt/sources.list[/email].d$ ll
total 44
drwxr-xr-x 2 root root 4096 2011-06-11 07:29 ./
drwxr-xr-x 6 root root 4096 2011-06-13 10:11 ../
-rw-r--r-- 1 root root   53 2011-06-13 10:23 dropbox.list
-rw-r--r-- 1 root root   50 2011-06-11 07:29 dropbox.list.save
-rw-r--r-- 1 root root  121 2011-06-13 10:23 http-ppa-natty.list
-rw-r--r-- 1 root root  116 2011-06-11 07:29 http-ppa-natty.list.save
-rw-r--r-- 1 root root  135 2011-06-13 10:23 kubuntu-ppa-ppa-natty.list
-rw-r--r-- 1 root root  157 2011-06-13 10:23 repository_spotify_com-ppa-natty.list
-rw-r--r-- 1 root root  152 2011-06-11 07:29 repository_spotify_com-ppa-natty.list.save
-rw-r--r-- 1 root root  119 2011-06-13 10:23 wfg-0ad-natty.list
-rw-r--r-- 1 root root  114 2011-06-11 07:29 wfg-0ad-natty.list.save

Can anyone help?

---

### Post by nick12inferno on 2011-07-25
hey i didint understand which ppa lines u removed...can you plz tellme...i got the same problem....

---

### Post by nick12inferno on 2011-07-25
[SIZE=3]this is what its showing


W: Failed to fetch [http://ppa.launchpad.net/baudm/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/baudm/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/baudm/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/baudm/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

[/SIZE]

---

### Post by oldos2er on 2011-07-25
Can you post the output of **ls /etc/apt/sources.list.d** ?

---

### Post by fendijr on 2011-07-30
> **zvacet said:**
> PPPA lines make all the trouble.They are not pointing at some specific PPA.In terminal

```
gksudo gedit /etc/apt/sources.list
```

remove PPA lines and save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

sorry, i`m newbie using ubuntu.
pls guide me which part to edit :

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://localhost:9977/localhost:9977/help.ubuntu.com/community/UpgradeNotes](http://localhost:9977/localhost:9977/help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://localhost:9977/localhost:9977/my.archive.ubuntu.com/ubuntu/](http://localhost:9977/localhost:9977/my.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
deb-src [http://localhost:9977/localhost:9977/my.archive.ubuntu.com/ubuntu/](http://localhost:9977/localhost:9977/my.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://localhost:9977/localhost:9977/archive.canonical.com/ubuntu](http://localhost:9977/localhost:9977/archive.canonical.com/ubuntu) maverick partner
deb-src [http://localhost:9977/localhost:9977/archive.canonical.com/ubuntu](http://localhost:9977/localhost:9977/archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://localhost:9977/localhost:9977/extras.ubuntu.com/ubuntu](http://localhost:9977/localhost:9977/extras.ubuntu.com/ubuntu) natty main
deb-src [http://localhost:9977/localhost:9977/extras.ubuntu.com/ubuntu](http://localhost:9977/localhost:9977/extras.ubuntu.com/ubuntu) natty main

# deb [http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu](http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu) maverick main universe restricted multiverse
# deb-src [http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu](http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu) maverick universe main multiverse restricted #Added by software-properties
deb [http://localhost:9977/localhost:9977/security.ubuntu.com/ubuntu/](http://localhost:9977/localhost:9977/security.ubuntu.com/ubuntu/) maverick-security universe main multiverse restricted
deb-src [http://localhost:9977/localhost:9977/security.ubuntu.com/ubuntu/](http://localhost:9977/localhost:9977/security.ubuntu.com/ubuntu/) maverick-security universe main multiverse restricted
deb [http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu](http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu) maverick-updates universe main multiverse restricted
deb-src [http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu](http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu) maverick-updates universe main multiverse restricted
deb [http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu](http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu) maverick-backports universe main multiverse restricted
deb-src [http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu](http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu) maverick-backports universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe

tq so much
Pls PM me at :
[email]fendijr@gmail.com[/email]

---

### Post by deadmantfa on 2011-10-05
try this

[http://www.webupd8.org/2011/07/get-rid-of-ppa-404-not-found-messages.html](http://www.webupd8.org/2011/07/get-rid-of-ppa-404-not-found-messages.html)

---

