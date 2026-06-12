---
title: "Unable to locate package"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by Fjupt on 2011-10-24
I'm still having the same problem... tried with sudo apt-get update -> which it did, and then i tried with sudo apt-get install xxx and it just said: 
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xxxxxx"

Can anyone tell me what i'm doing wrong here? :P

---

### Post by oldos2er on 2011-10-24
Post moved to its own thread.

---

### Post by Fjupt on 2011-10-25
I thank you for letting me have my own thread... :D
 
- And a note to the editional thread post i'm running the new 11.4, if i'm not entirely wrong. :P
 
Still have no luck.. it's seem like it's cutting itself off checking the internet for the stuff i tell it to get.

---

### Post by matt_symes on 2011-10-25
Hi

What package are you trying to install. Have you checked your software sources.

Open a terminal and type

```
cat /etc/apt/sources.list
```

Post the results back here.

Also, from the terminal..

```
ls -l /etc/apt/sources.list.d/
```

That is a small L after ls. Post back results.

Kind regards

---

### Post by raja.genupula on 2011-10-25
> **matt_symes said:**
> Hi

What package are you trying to install. Have you checked your software sources.

Open a terminal and type

```
cat /etc/apt/sources.list
```Post the results back here.

Also, from the terminal..

```
ls -l /etc/apt/sources.list.d/
```That is a small L after ls. Post back results.

Kind regards


+1 

post the code of your terminal here , as it is , what ever you have typed in terminal.

Thank you.

---

### Post by Fjupt on 2011-10-25
[I]"fjupt@Grown-Midget:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse[/I]"

 - I was trying to install a program called emerald... i wanted to make my Ubuntu platform here my own.. Like edit the theme and so on. :)

Actually i would like to find a program that would make me edit all of this. to make it more plane and simple. I'm fairly good at programming myself, but i just don't really know where to start.. i'm not that experienced user of Ubuntu tbh. :)

Thanks for the feedback
Regards

Fjupt

---

### Post by Fjupt on 2011-10-25
The other ls -l /etc/apt.....
Here it is:[I]
"fjupt@Grown-Midget:~$ ls -l /etc/apt/sources.list.d/
total 36
-rw-r--r-- 1 root root 136 2011-10-24 21:50 cloudfoundry-ppa-oneiric.list
-rw-r--r-- 1 root root 136 2011-10-24 21:50 cloudfoundry-ppa-oneiric.list.save
-rw-r--r-- 1 root root  80 2011-10-24 21:50 dropbox.list
-rw-r--r-- 1 root root  80 2011-10-23 18:50 dropbox.list.distUpgrade
-rw-r--r-- 1 root root  80 2011-10-24 21:50 dropbox.list.save
-rw-r--r-- 1 root root 114 2011-10-24 21:50 jockey.list
-rw-r--r-- 1 root root 114 2011-10-23 18:50 jockey.list.distUpgrade
-rw-r--r-- 1 root root 114 2011-10-24 21:50 jockey.list.save
-rw-r--r-- 1 root root 130 2011-10-24 21:50 team-xbmc-ppa-oneiric.list"[/I]

Thanks again for the feedback.
Regards

Fjupt

---

### Post by nlucaroni on 2011-10-25
in 11.04+ Ubuntu has played around a lot with the UI, and I don't believe emerald is compatible with compiz-fusion --Emerald is not in the package manager.

you can search the available packages by,
```
apt-cache search XXX
```.

You should be able to load ubuntu-classic, and install emerald (not from aptitude). Good luck.

PS; the newest Ubuntu is 11.10 that came out earlier this month.

---

### Post by Fjupt on 2011-10-25
> **nlucaroni said:**
> in 11.04+ Ubuntu has played around a lot with the UI, and I don't believe emerald is compatible with compiz-fusion --Emerald is not in the package manager.

you can search the available packages by,
```
apt-cache search XXX
```.

You should be able to load ubuntu-classic, and install emerald (not from aptitude). Good luck.

PS; the newest Ubuntu is 11.10 that came out earlier this month.

Oh god i feel like a newbie. :P 
I just updated from the 10.10 version so.. but i'm pretty sure it's only 11.04. but i'm not 100% sure.
Anyhow... How could i make it back to classic? - Since that's a start in  the right direction for me. i could do it on 10.10 but i haven't found a way to do it on this one. :P

Thanks

Regards

Fjupt

EDIT: Let's try again, shall we?
- It&#836;s 11.10 i'm running here. my bad with the confusing here.
But that doesn't change that i can't seem to install my apps. O.o

---

### Post by matt_symes on 2011-10-25
Hi

[www.ubuntuupdates.org/packages/show/329590](www.ubuntuupdates.org/packages/show/329590)

Yes; the Emerald package was deleted from the repository.

What other packages are you having trouble with ?

Kind regards

---

### Post by Fjupt on 2011-10-25
Well i guess that might be it for now then...
But do you guys have any good theme managing tools?
Or in any language i can program ubuntu to look the way i want it to look? :)

as i told before i'm pretty new at this. :)

Regards

Fjupt

EDIT: Actually i found a fix for Emerald which didn't work either... 

[B][http://ubuntugenius.wordpress.com/2011/05/22/ubuntu-11-04-fix-enable-emerald-themes-for-compiz-fusion-window-borders-title-bars/](http://ubuntugenius.wordpress.com/2011/05/22/ubuntu-11-04-fix-enable-emerald-themes-for-compiz-fusion-window-borders-title-bars/)

[/B]That i also tried to install but with no better luck than the emerald itself. :)

---

### Post by nlucaroni on 2011-10-25
My apologies about suggesting the ubuntu-classic. It looks like it was taken away. If it still exists under your version, in the login screen there is either a drop-down, a little gear or some options you can attach to your login session. Here you'll find ubuntu-classic, and a recovery console, et cetera.

---

### Post by Fjupt on 2011-10-26
Okay. Then they've taken it away. :)
Since i didn't find it there...
There's only Ubuntu, ubuntu 2d and that recovery thingy and a some other thing aswell. :)

So sadly my dear ubuntu classic is long gone... :) (As far as i can tell)

---

