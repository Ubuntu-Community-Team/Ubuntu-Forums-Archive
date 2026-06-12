---
title: "firefox3 after upgrade to Hardy"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by getaboat on 2008-08-08
After upgrading from Dapper to Hardy Synaptic indicates I have FF2 and FF3 installed. I have two links in the applicatiosn/internet menu. However all links go to FF2. /usr/bin/firefox-3.0 goes to FF2. Ideally I just want my FF2 installation upgraded to FF3. I don't want to loose all my bookmarks etc so I have not tried an uninstll of FF2. C

Any pointers anyone?

---

### Post by cdtech on 2008-08-08
I had the same issue with my install. I just went to the "Synaptic Package Manger" and removed 2 that way. All of my bookmarks and history stayed intact.

---

### Post by silkstone on 2008-08-08
You bookmarks should be OK if you uninstall FF2, but just to be absolutely sure you could copy the folder in your Home folder called .mozilla/firefox/xxx.default to somewhere else as a backup.

---

### Post by aysiu on 2008-08-08
That's odd.

Can you paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) and post the output back here? ```
ls -l /usr/bin/firefox
cat /etc/lsb-release
cat /etc/apt/sources.list
```

---

### Post by getaboat on 2008-08-08
I uninstalled FF2 in Synaptic and after changing the launcher to /usr/bin/firefox-3.0 it now works with all my bookmarks etc! thanks. 

I'm still not sure why the default firefox command is picking up FF2 - which is still there (I didn't remove permamently in synaptic) - it ends up running the mozilla.sh script - I'm just not sure from where.

In answer to Aysiu's request this is what I get...

```

winfamu1@winfamu1:~$ ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 20 2007-02-13 22:50 /usr/bin/firefox -> /opt/firefox/firefox

winfamu1@winfamu1:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

winfamu1@winfamu1:~$ cat /etc/apt/sources.list

deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe main restricted multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by aysiu on 2008-08-08
> **getaboat said:**
> ```

winfamu1@winfamu1:~$ ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 20 2007-02-13 22:50 /usr/bin/firefox -> /opt/firefox/firefox
``` This is the problem right here.

At some point, you installed the Mozilla (not Ubuntu repositories) version of Firefox 2, and that's superceding the Ubuntu repositories version of Firefox 3.

Follow [these instructions](http://www.psychocats.net/ubuntu/firefox#remove), and you should be fine.

---

