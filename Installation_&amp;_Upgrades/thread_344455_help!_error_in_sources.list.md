---
title: "help! error in /sources.list"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by caltabellotta on 2007-01-22
Hi,

I was recently trying to change my monitor resolution through changing some changes in```
"sudo nano /etc/apt/sources.list"
```.  I have tried going back but don't know *that* much about navigation in konsole:-\"   When I try to update or go to add/remove programs, I get this message:
```
E: Type 'N.B.' is not known on line 12 in source list /etc/apt/sources.list

```

I have tried recovery mode, but it does not fully open the desktop, help me undo these changes and rollback!

Thanks

---

### Post by aysiu on 2007-01-22
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by meng on 2007-01-22
You don't change monitor resolution by changing your sources.list!!!!

Please:
cat /etc/apt/sources.list

and tell us what you have there.

---

### Post by caltabellotta on 2007-01-22
heres everything

```


deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
 N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 team, and may not be under a free licence. Please satisfy yourself as to
 your rights to use the software. Also, please note that software in
 universe WILL NOT receive any review or updates from the Ubuntu security
 team.
 deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
 deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://www.getautomatix.com/apt edgy main
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt edgy main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy universe multiverse

```

---

### Post by aysiu on 2007-01-23
This part is not supposed to be uncommented. The # sign "comments out" a line--making it invisible to Ubuntu. Notice how these lines *don't* have the # sign in front of them? Well, they should have it. Instead of ```
 N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 team, and may not be under a free licence. Please satisfy yourself as to
 your rights to use the software. Also, please note that software in
 universe WILL NOT receive any review or updates from the Ubuntu security
 team.
``` it should be ```
#N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
# team, and may not be under a free licence. Please satisfy yourself as to
 #your rights to use the software. Also, please note that software in
 #universe WILL NOT receive any review or updates from the Ubuntu security
 #team.
```

---

### Post by caltabellotta on 2007-01-23
> **aysiu said:**
> This part is not supposed to be uncommented. The # sign "comments out" a line--making it invisible to Ubuntu. Notice how these lines *don't* have the # sign in front of them? Well, they should have it. Instead of ```
 N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 team, and may not be under a free licence. Please satisfy yourself as to
 your rights to use the software. Also, please note that software in
 universe WILL NOT receive any review or updates from the Ubuntu security
 team.
``` it should be ```
#N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
# team, and may not be under a free licence. Please satisfy yourself as to
 #your rights to use the software. Also, please note that software in
 #universe WILL NOT receive any review or updates from the Ubuntu security
 #team.
```

how do I "re-quote" them? I opened up the xorg config, but that is not in there...thanks for the help, im just learning:roll:

---

### Post by meng on 2007-01-23
You seem to be confusing two different files
/etc/apt/sources.list, which defines your software repositories
/etc/X11/xorg.conf, which configures your x-server

You need to fix your sources.list first (since we know something about this problem)
sudo nano -B /etc/apt/sources.list
will allow you to edit
ctrl-x to save your changes and exit.

---

### Post by caltabellotta on 2007-01-23
> **meng said:**
> You seem to be confusing two different files
/etc/apt/sources.list, which defines your software repositories
/etc/X11/xorg.conf, which configures your x-server

You need to fix your sources.list first (since we know something about this problem)
sudo nano -B /etc/apt/sources.list
will allow you to edit
ctrl-x to save your changes and exit.

thank you!  Everything works now, but I seem to have a problem here:
```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```

It seems to have to do with automatix, that was the only problem I had after sudo-apt update once reconfiguring the sources.list.

thanks again to both:wink:

---

### Post by aysiu on 2007-01-23
It usually means you're trying to use *aptitude*, *apt-get*, or *dpkg* while you also have Adept, Add/Remove, or Synaptic open.

Only one program can access the package manager at a time.

---

