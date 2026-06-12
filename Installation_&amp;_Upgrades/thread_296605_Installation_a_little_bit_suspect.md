---
title: "Installation a little bit suspect"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by marbig on 2006-11-09
I've been trying to install 'Automatix' without success. Going through the install procedure it tells me to add  
"deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main" to source.list file.
My source.file looks like this...```

# Line commented out by installer because it failed to verify:
#deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://au.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu dapper-security main
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu dapper-security main
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://www.getautomatix.com/apt dapper main
``` All the lines commented out by installer.
Did this occurr during the original installion and how might I rectify it?
Thank you.

---

### Post by Cable on 2006-11-09
To get those repositories uncommented, you can either remove the pound sign in front of each repository you want to use, or you can open Synaptic (System>Administration>Synaptic Package Manager).  From Synaptic, Settings>Repositories.  In the window that opens you can choose which repositories to use.

---

### Post by rsosa on 2006-11-12
Hi
This is exactly what ocurred to me after installing kubuntu 6.06
The problem was, i was installing it in a lappie when was watching tv, so the ethernet cable was not connected (it was away from me :D), when the installer tryed to update the repositories automatically, it failed of course, and i guess thats the reason why it commented out those lines. Maybe it was coincidence, but that was the only different thing i made comparing with other previous ubuntu installations. Should i post it in the bugs or something?
regards

---

