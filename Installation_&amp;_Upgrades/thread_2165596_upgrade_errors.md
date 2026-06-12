---
title: "upgrade errors"
date: 2013-08-05
forum: Installation &amp; Upgrades
---

### Post by spencer2 on 2013-08-05
Hi: i need some help. I've been trying to update - and now, upgrade - my ubuntu version. 
I currently have 12.04 and am trying to get upgraded to the new 13, but am continually getting the same error message. 

This is the error message:  

_______________________________________
W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

__________________________________________

any help would be appreciated. 
also, I'm not a computer genius like so many other ubuntu users, so some help in laymen terms would also be awesome. 
thank you very much

spencer ownside

---

### Post by bapoumba on 2013-08-05
The archive points to Maverick backports. Maverick is not supported anymore, you should remove them from your repos.
Please post the output to **cat /etc/apt/sources.list**.

---

### Post by spencer2 on 2013-08-07
here is the output from cat /etc/apt/sources.list  :::

_______________________________________________________________________

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-proposed restricted main multiverse universe

_______________________________________________________________________


hope that is what you were asking for and thank you for your help: appreciate it greatly. 

thank you very much

---

### Post by zealibib slaughter on 2013-08-07
comment out these lines from your sources.list and it should take care of the problem
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse 
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner 
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

---

### Post by spencer2 on 2013-08-13
i ran the lines that you posted and each time i got "deb-src: command not found" .
its very possible that i'm just missing a command or something. I'll confess that I'm not sure what you mean by "comment" out the lines. i tried using both 'bash' and 'sudo' before the lines but still got the same and when i used that i got "no such file or directory". 

On top of it all, after running the last 'cat' command, all my desktop icons have disappeared and my menu bar of programs is no longer visible either. When i go into the terminal and look at the desktop, stuff is there - i just can't seem to access any of it. 

So, i guess i need to know how to 'comment' a line out?

---

### Post by bapoumba on 2013-08-13
That means either editing the sources.list to have a # at the beginning of the line. It will be interpreted as a "comment" for users reading the file and not a command for applications using it. Or you can go to the Software Sources and untick the 3 Maverick repos : [https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

Then "Reload" to update the sources.list reading by the package manager.

---

