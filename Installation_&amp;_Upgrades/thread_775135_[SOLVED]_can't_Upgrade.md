---
title: "[SOLVED] can't Upgrade"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by Just-trevor on 2008-04-29
I'm trying to upgrade from 7.10 to 8.04 and I got this error message while my comp was fetching the last 4 files:

"A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

"Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Release) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)"

When I upgraded to Gutsy a while ago it worked fine, if that matters.

thanks in advance

---

### Post by CAsurfer on 2008-04-29
Can you confirm that this is not in fact a network problem? Even if you can connect to the internet, it may be that the repositories are being hit hard right now.

---

### Post by Just-trevor on 2008-04-29
I tried installing it a couple weeks or so ago, and a couple more times within a week, and I got the same error all those other times too.

I'd have to have some BAD luck for that to be it.

---

### Post by Just-trevor on 2008-04-29
Got to go to sleep sorry when I don't reply

---

### Post by CAsurfer on 2008-04-29
It looks like other people have had this problem, and that it may have to do with update-manager bugginess (so upgrade update-manager) or a bad sources.list:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/222117](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/222117)
[http://ubuntuforums.org/showthread.php?t=603418](http://ubuntuforums.org/showthread.php?t=603418)
[http://ubuntuforums.org/showthread.php?t=688255](http://ubuntuforums.org/showthread.php?t=688255)

---

### Post by Just-trevor on 2008-04-30
On the last link a guy said that eventually the update manager would do a Partial Upgrade so I did one and this is the error I got:

"Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport."

---

### Post by CAsurfer on 2008-05-01
Could you post your sources.list?

A workaround is to upgrade via the Hardy alternate installation disk. Instructions are here: [http://www.ubuntu.com/getubuntu/upgrading#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d](http://www.ubuntu.com/getubuntu/upgrading#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d)

---

### Post by Partyboi2 on 2008-05-01
deleted

---

### Post by tetsuc on 2008-05-04
I have this same issue but it happens both when I try to upgrade via the net and via the alternate CD...

---

### Post by CAsurfer on 2008-05-04
Every source in your sources.list is a Gutsy repository, except the first, which is a Hardy repository. Maybe commenting that repo out would help? (Honestly, I have no idea).

---

### Post by tetsuc on 2008-05-04
Yep, that did it! However I just hooped my install by running a chown -R / ... oops. Was trying to change ownership of some copied backup files but now I can't even boot into 8.04. Lets see if the gparted does what it is supposed to... (but that is a story for another thread :) )

Cheers!

---

### Post by CAsurfer on 2008-05-06
Wow, I just had some fun with UrbanDictionary and "hooped". You learn something new every day...

I think using gparted is a bit overkill in this case. I took a look at some files on my system, and it looks like everything is owned by either "root" or "eric" (me!). So my hypothesis is that if you chown all files that aren't in your home directory to "root", and the ones in your home directory to your username, you'll be good.

---

### Post by Just-trevor on 2008-05-12
sorry I haven't replied, I forgot to check to see if I got any replies with school and all
I... don't know what a sources.list is 
and my CD drive doesn't work so I can't just use that...
but that's for another thread

Sorry again I didn't check this again,
thanks in advance

---

### Post by Partyboi2 on 2008-05-13
> **Just-trevor said:**
> sorry I haven't replied, I forgot to check to see if I got any replies with school and all
I... don't know what a sources.list is 
and my CD drive doesn't work so I can't just use that...
but that's for another thread

Sorry again I didn't check this again,
thanks in advance
You can view your sources.list by opening a terminal (Applications>Accessories>Terminal) and typing:
```
cat /etc/apt/sources.list
``` or you can view it in a text editor like gedit
```
gedit /etc/apt/sources.list
```here is a brief explation of what a sources.list is:
> The sources.list file is a key factor in adding or upgrading applications to your Ubuntu installation. This is also used by your system for system updates. The file is basically the roadmap for your system to know where it may download programs for installation or upgrade.

---

### Post by Just-trevor on 2008-05-14
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted web
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted web
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted web
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

#AUTOMATIX REPOS START

# deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse web

deb http://archive.ubuntu.com/ubuntu hardy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://archive.ubuntu.com/ubuntu/ gutsy universe multiverse
# deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu gutsy/
```

ok... now what...

---

### Post by Partyboi2 on 2008-05-14
Open you sources.list with admin privileges. Open a terminal
```
gksudo gedit /etc/apt/sources.list
```then look for all the lines that have the word [COLOR=Red]web[/COLOR] and remove the web word. So for example:
```
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted [COLOR=Red]web[/COLOR] 
```would become
```
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
```After you have finished making the changes and have saved, back in the terminal type:
```
sudo apt-get update
``````
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted [COLOR=Red]web[/COLOR]
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted [COLOR=Red]web[/COLOR]
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted [COLOR=Red]web[/COLOR]
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

#AUTOMATIX REPOS START

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse web

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse
# deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/
```

---

### Post by Just-trevor on 2008-05-14
thx, it worked

quick question, did everyone have to do this at one point or is my computer just dumb?

thanks again

---

### Post by Partyboi2 on 2008-05-14
It seems to happen at ramdom, I personally have never had the problem.

---

### Post by burnfromwithin on 2008-05-15
Thanks, I had the same issue, but after removing the 'web' part, it all updated!

---

