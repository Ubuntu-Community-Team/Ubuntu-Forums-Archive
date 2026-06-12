---
title: "Upgrade from yakkety to xenial not supported error"
date: 2016-10-28
forum: Installation &amp; Upgrades
---

### Post by ales on 2016-10-28
Hello,

I have received na error message after an upgrade from xenial to yakkety. Has someone the same issue. I could not find the solution to fix this.
[ATTACH=CONFIG]271826[/ATTACH][ATTACH=CONFIG]271827[/ATTACH][ATTACH=CONFIG]271828[/ATTACH]

If I press continue on upgrade after error message, it simply writes, that the system is up to date. If I choose partial upgrade, the error comes up. The fact is, that the upgrade from xenial was not flawless.....

---

### Post by oldos2er on 2016-10-28
From Yakkety (16.10) to Xenial (16.04) would be a downgrade, which is not supported. 

Don't run the partial upgrade, I seem to recall that there are problems involved in doing that.

> the upgrade from xenial was not flawless..... Any further information you can provide would help others to help you. Can we see your sources.list, and any other repositories you might have? ```
cat /etc/apt/sources.list

ll /etc/apt/sources.list.d/
```

---

### Post by ales on 2016-10-29
During the upgrade there was a problem, and I did partial, after that 16.10 was as the  new system runing, but when it starts to check updates again, it always shows that message.


> **oldos2er said:**
> From Yakkety (16.10) to Xenial (16.04) would be a downgrade, which is not supported. 

Don't run the partial upgrade, I seem to recall that there are problems involved in doing that.

 Any further information you can provide would help others to help you. Can we see your sources.list, and any other repositories you might have? **```
cat /etc/apt/sources.list**

dreamwalker@dreamwalker-System-Product-Name:~$ cat /etc/apt/sources.list

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://tux.rainside.sk/ubuntu/ yakkety main restricted
deb-src http://tux.rainside.sk/ubuntu/ yakkety main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://tux.rainside.sk/ubuntu/ yakkety-updates main restricted
deb-src http://tux.rainside.sk/ubuntu/ yakkety-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://tux.rainside.sk/ubuntu/ yakkety universe
deb-src http://tux.rainside.sk/ubuntu/ yakkety universe
deb http://tux.rainside.sk/ubuntu/ yakkety-updates universe
deb-src http://tux.rainside.sk/ubuntu/ yakkety-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://tux.rainside.sk/ubuntu/ yakkety multiverse
deb-src http://tux.rainside.sk/ubuntu/ yakkety multiverse
deb http://tux.rainside.sk/ubuntu/ yakkety-updates multiverse
deb-src http://tux.rainside.sk/ubuntu/ yakkety-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://tux.rainside.sk/ubuntu/ yakkety-security main restricted
deb-src http://tux.rainside.sk/ubuntu/ yakkety-security main restricted
deb http://tux.rainside.sk/ubuntu/ yakkety-security universe
deb-src http://tux.rainside.sk/ubuntu/ yakkety-security universe
deb http://tux.rainside.sk/ubuntu/ yakkety-security multiverse
deb-src http://tux.rainside.sk/ubuntu/ yakkety-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu wily partner
deb-src http://archive.canonical.com/ubuntu wily partner

**ll /etc/apt/sources.list.d/
```**

dreamwalker@dreamwalker-System-Product-Name:~$ ll /etc/apt/sources.list.d/
total 68
drwxr-xr-x 2 root root 4096 okt 23 00:51 ./
drwxr-xr-x 6 root root 4096 okt 22 23:58 ../
-rw-r--r-- 1 root root  189 okt 28 23:12 google-chrome.list
-rw-r--r-- 1 root root  191 okt 22 22:58 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root  189 okt 28 23:12 google-chrome.list.save
-rw-r--r-- 1 root root    0 jan 17  2016 libreoffice-ubuntu-libreoffice-4-2-wily.list
-rw-r--r-- 1 root root    0 jan 17  2016 libreoffice-ubuntu-libreoffice-4-2-wily.list.save
-rw-r--r-- 1 root root  212 okt 28 23:12 steam.list
-rw-r--r-- 1 root root  216 okt 22 22:58 steam.list.distUpgrade
-rw-r--r-- 1 root root  212 okt 28 23:12 steam.list.save
-rw-r--r-- 1 root root   96 okt 28 23:12 team-xbmc-ubuntu-ppa-xenial.list
-rw-r--r-- 1 root root  130 okt 22 22:58 team-xbmc-ubuntu-ppa-xenial.list.distUpgrade
-rw-r--r-- 1 root root   96 okt 28 23:12 team-xbmc-ubuntu-ppa-xenial.list.save
-rw-r--r-- 1 root root  100 okt 28 23:12 vfrico-ubuntu-cambiadeso-xenial.list
-rw-r--r-- 1 root root  138 okt 22 22:58 vfrico-ubuntu-cambiadeso-xenial.list.distUpgrade
-rw-r--r-- 1 root root  100 okt 28 23:12 vfrico-ubuntu-cambiadeso-xenial.list.save
-rw-r--r-- 1 root root   96 okt 28 23:12 vfrico-ubuntu-stable-xenial.list
-rw-r--r-- 1 root root  130 okt 22 22:58 vfrico-ubuntu-stable-xenial.list.distUpgrade
-rw-r--r-- 1 root root   96 okt 28 23:12 vfrico-ubuntu-stable-xenial.list.save
dreamwalker@dreamwalker-System-Product-Name:~$

---

### Post by oldos2er on 2016-10-29
> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner 
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner These two lines in your sources.list should be deleted, commented out, or edited to say yakkety in place of wily.

Check the contents of the *.list files in /etc/apt/sources.list.d/ and be sure they are commented out or refer to yakkety. 

The blunt hammer approach to solving your problem would be to do a clean install of 16.10 (after backing up any sensitive data of course). We can try to fix the sources list errors first, but because you already ran the partial upgrade it might not be enough to fix your system.

---

### Post by ales on 2016-11-01
Hello,

so thanks for the effort, it seems, that something really went wrong during the upgrade. So I will reinstall it. It will be easier and faster for me.

Anyway, if it helps to someone in the future, I post some more screens.

[ATTACH=CONFIG]271905[/ATTACH][ATTACH=CONFIG]271906[/ATTACH][ATTACH=CONFIG]271907[/ATTACH][ATTACH=CONFIG]271908[/ATTACH][ATTACH=CONFIG]271909[/ATTACH]

Above you can see, that I am not able to run update and items in the list also cannot be selected/deselected, except for pre-selected. If I try partial upgrade, the windows for upgrade is blank.....

---

### Post by oldos2er on 2016-11-01
> So I will reinstall it. It will be easier and faster for me. Agreed.

Lesson learned: When offered a partial upgrade, never do it.

---

