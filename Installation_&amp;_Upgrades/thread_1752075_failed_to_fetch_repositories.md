---
title: "failed to fetch repositories"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by Pragu on 2011-05-07
hey there, I upgraded to natty on release day and everything went fine, but about three days ago when I went to update my sources, I get this
```
 sudo apt-get update 
```
```
 W: Failed to fetch http://ppa.launchpad.net///ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net///ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead. 
```
I've looked through the forums, but similar problems are always tied to the mozilla repo, not this one. It seems important, so i'm not sure if i should just delete it or what. My sources.list looks like this:
```
 # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse 
```

any thoughts on what to delete and/or replace?

---

### Post by dino99 on 2011-05-07
the "source" probably dont exist for the ppa, remove it from sources.list (and the other deb-src too)

---

### Post by Not unique on 2011-05-07
There's still some Maverick lines in there too will that matter? can you just change Maverick to Natty?

---

### Post by Pragu on 2011-05-07
Which source(s) should I remove? None of them in sources.list match exactly ubuntu/dists/natty/main/sources, so what I really want to know is what that equates to within the file.

As to the Maverick lines, perhaps I upgraded incorrectly? In Maverick I launched "update-manager -d" to get the Beta 2, then on launch day i upgraded all my sources and packages, and "lsb_release -a" changed from '11.04 development' to '11.04' so I assumed I was running the final release.

---

### Post by dino99 on 2011-05-07
every one of: deb-scr (in the sources.list), comment the line

---

### Post by Not unique on 2011-05-07
To my understanding all the lines with Maverick near the end need to go or you could find and replace all Mavericks with Natty i.e. 

deb [http://ppa.launchpad.net/mozillateam/ubuntu](http://ppa.launchpad.net/mozillateam/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/mozillateam/ubuntu](http://ppa.launchpad.net/mozillateam/ubuntu) maverick main

to-

deb [http://ppa.launchpad.net/mozillateam/ubuntu](http://ppa.launchpad.net/mozillateam/ubuntu) natty main
deb-src [http://ppa.launchpad.net/mozillateam/ubuntu](http://ppa.launchpad.net/mozillateam/ubuntu) natty main

---

### Post by matt_symes on 2011-05-07
Hi

> **Pragu said:**
> Which source(s) should I remove? None of them in sources.list match exactly ubuntu/dists/natty/main/sources, so what I really want to know is what that equates to within the file.

As to the Maverick lines, perhaps I upgraded incorrectly? In Maverick I launched "update-manager -d" to get the Beta 2, then on launch day i upgraded all my sources and packages, and "lsb_release -a" changed from '11.04 development' to '11.04' so I assumed I was running the final release.

The offendiing lines are in your apt sub folder. To find them open a terminal and type (case sensitive)

```
grep -R "http://ppa.launchpad.net///ubuntu/dists/natty/main" /etc/apt/*
```

The easiest way is to copy and paste this into a terminal.

If you post the output back here we can help you delete them. You have to delete them as they are not valid. Changing them to natty will not fix your issue.

Kind regards

---

### Post by Pragu on 2011-05-07
thanks for the reply matt, but when I run the grep, it says ```
 grep: /etc/apt/secring.gpg: Permission denied
grep: /etc/apt/trustdb.gpg: Permission denied

```
and when I run it with sudo, there is no output. I looked at the two files individually, and secring.gpg has nothing in it and trustdb.gpg just reads "@^@^@^@^..."

---

### Post by Not unique on 2011-05-07
Can he not do it manually Matt? via the software sources or terminal?

---

### Post by matt_symes on 2011-05-07
Hi

What's the output of

```
ls -l /etc/apt/sources.list.d/
```

That is as small L above after ls.

Kind regards

---

### Post by Pragu on 2011-05-07
```
 

total 112
-rw-r--r-- 1 root root  66 2011-04-30 13:47 chromium-daily-ppa-natty.list
-rw-r--r-- 1 root root  66 2011-04-30 13:47 chromium-daily-ppa-natty.list.save
-rw-r--r-- 1 root root  72 2011-04-30 13:47 globalmenu-team-ppa-maverick.list
-rw-r--r-- 1 root root  72 2011-04-17 11:04 globalmenu-team-ppa-maverick.list.distUpgrade
-rw-r--r-- 1 root root  72 2011-04-30 13:47 globalmenu-team-ppa-maverick.list.save
-rw-r--r-- 1 root root  70 2011-04-09 12:59 gnome-globalmenu.list.save
-rw-r--r-- 1 root root 176 2011-04-30 13:47 google-chrome.list
-rw-r--r-- 1 root root 176 2011-04-17 11:04 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 176 2011-04-30 13:47 google-chrome.list.save
-rw-r--r-- 1 root root  57 2011-04-30 13:47 google-stable.list
-rw-r--r-- 1 root root  57 2011-04-30 13:47 google-stable.list.save
-rw-r--r-- 1 root root 142 2011-04-17 11:04 iaz-battery-status-maverick.list.distUpgrade
-rw-r--r-- 1 root root 142 2011-04-15 17:37 iaz-battery-status-maverick.list.save
-rw-r--r-- 1 root root 202 2011-04-30 13:47 iaz-battery-status-natty.list
-rw-r--r-- 1 root root 202 2011-04-30 13:47 iaz-battery-status-natty.list.save
-rw-r--r-- 1 root root 102 2011-04-30 13:47 --natty.list
-rw-r--r-- 1 root root 102 2011-04-30 13:47 --natty.list.save
-rw-r--r-- 1 root root  92 2011-04-17 11:04 tualatrix-ppa-maverick.list.distUpgrade
-rw-r--r-- 1 root root  92 2011-04-15 17:37 tualatrix-ppa-maverick.list.save
-rw-r--r-- 1 root root 118 2011-04-30 13:47 tualatrix-ppa-natty.list
-rw-r--r-- 1 root root 118 2011-04-30 13:47 tualatrix-ppa-natty.list.save
-rw-r--r-- 1 root root  92 2011-04-09 12:59 ubuntu-tweak-stable.list.save
-rw-r--r-- 1 root root 154 2011-04-17 11:04 ubuntu-tweak-testing-ppa-maverick.list.distUpgrade
-rw-r--r-- 1 root root 154 2011-04-15 17:37 ubuntu-tweak-testing-ppa-maverick.list.save
-rw-r--r-- 1 root root 214 2011-04-30 13:47 ubuntu-tweak-testing-ppa-natty.list
-rw-r--r-- 1 root root 214 2011-04-30 13:47 ubuntu-tweak-testing-ppa-natty.list.save
-rw-r--r-- 1 root root 130 2011-04-30 13:47 ubuntu-wine-ppa-natty.list
-rw-r--r-- 1 root root 130 2011-04-30 13:47 ubuntu-wine-ppa-natty.list.save
jack@jack-1001PXD:~$ cd ~
jack@jack-1001PXD:~$ 
jack@jack-1001PXD:~$ ls -l /etc/apt/sources.list.d/
total 112
-rw-r--r-- 1 root root  66 2011-04-30 13:47 chromium-daily-ppa-natty.list
-rw-r--r-- 1 root root  66 2011-04-30 13:47 chromium-daily-ppa-natty.list.save
-rw-r--r-- 1 root root  72 2011-04-30 13:47 globalmenu-team-ppa-maverick.list
-rw-r--r-- 1 root root  72 2011-04-17 11:04 globalmenu-team-ppa-maverick.list.distUpgrade
-rw-r--r-- 1 root root  72 2011-04-30 13:47 globalmenu-team-ppa-maverick.list.save
-rw-r--r-- 1 root root  70 2011-04-09 12:59 gnome-globalmenu.list.save
-rw-r--r-- 1 root root 176 2011-04-30 13:47 google-chrome.list
-rw-r--r-- 1 root root 176 2011-04-17 11:04 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 176 2011-04-30 13:47 google-chrome.list.save
-rw-r--r-- 1 root root  57 2011-04-30 13:47 google-stable.list
-rw-r--r-- 1 root root  57 2011-04-30 13:47 google-stable.list.save
-rw-r--r-- 1 root root 142 2011-04-17 11:04 iaz-battery-status-maverick.list.distUpgrade
-rw-r--r-- 1 root root 142 2011-04-15 17:37 iaz-battery-status-maverick.list.save
-rw-r--r-- 1 root root 202 2011-04-30 13:47 iaz-battery-status-natty.list
-rw-r--r-- 1 root root 202 2011-04-30 13:47 iaz-battery-status-natty.list.save
-rw-r--r-- 1 root root 102 2011-04-30 13:47 --natty.list
-rw-r--r-- 1 root root 102 2011-04-30 13:47 --natty.list.save
-rw-r--r-- 1 root root  92 2011-04-17 11:04 tualatrix-ppa-maverick.list.distUpgrade
-rw-r--r-- 1 root root  92 2011-04-15 17:37 tualatrix-ppa-maverick.list.save
-rw-r--r-- 1 root root 118 2011-04-30 13:47 tualatrix-ppa-natty.list
-rw-r--r-- 1 root root 118 2011-04-30 13:47 tualatrix-ppa-natty.list.save
-rw-r--r-- 1 root root  92 2011-04-09 12:59 ubuntu-tweak-stable.list.save
-rw-r--r-- 1 root root 154 2011-04-17 11:04 ubuntu-tweak-testing-ppa-maverick.list.distUpgrade
-rw-r--r-- 1 root root 154 2011-04-15 17:37 ubuntu-tweak-testing-ppa-maverick.list.save
-rw-r--r-- 1 root root 214 2011-04-30 13:47 ubuntu-tweak-testing-ppa-natty.list
-rw-r--r-- 1 root root 214 2011-04-30 13:47 ubuntu-tweak-testing-ppa-natty.list.save
-rw-r--r-- 1 root root 130 2011-04-30 13:47 ubuntu-wine-ppa-natty.list
-rw-r--r-- 1 root root 130 2011-04-30 13:47 ubuntu-wine-ppa-natty.list.save

```

---

### Post by Pragu on 2011-05-07
After a restart, both offending ppa's showed up in the software sources manager, all I had to do was uncheck them and the error went away. I'll have to wait to make sure I still get all the necessary updates, but I think it'll be alright. I'm not sure why this happened but no harm done I suppose

thanks everyone!

---

