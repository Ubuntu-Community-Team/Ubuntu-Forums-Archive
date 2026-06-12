---
title: "partially upgraded, reboot, now login goes to sleep state"
date: 2020-04-16
forum: Installation &amp; Upgrades
---

### Post by srope01 on 2020-04-16
I have my settings on Software Updater to check for updates daily. Today, the update went a little strange. It got into a state where the Software Updater said that a partial upgrade was needed. So after clicking on the "Partial upgrade" button, it seems to have done its job and then it tells me to reboot. I get the login screen and after I enter my password, the screen blanks only showing the cursor for a few seconds. Then the computer turns completely off (including the fan) and goes into a hibernation or sleep state. If I hit return, it immediately activates and completes the login. The strange thing is that if I simply logout of my account and log back in, then it avoids going into the sleep state. But when I reboot and login, it always goes into this sleep state so that I have to hit the return to complete the login.

Does anyone know how I could solve this? I am running Ubuntu 18.04 (fresh install since January 2020).

---

### Post by mörgæs on 2020-04-16
Please run ```
sudo apt update
``` and ```
sudo apt dist-upgrade
``` and post their output in CODE tags.

About partial upgrades: 
[https://wiki.ubuntu.com/U%2B1/partial_upgrade](https://wiki.ubuntu.com/U%2B1/partial_upgrade)

---

### Post by srope01 on 2020-04-16
From sudo apt update
```
Hit:1 http://ch.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://ch.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Hit:3 http://ppa.launchpad.net/libreoffice/ppa/ubuntu bionic InRelease         
Get:4 http://ch.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Get:5 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]    
Get:6 http://ch.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [914 kB]
Get:7 http://ch.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [668 kB]
Get:8 http://ch.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [307 kB]
Get:9 http://ch.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [1,013 kB]
Get:10 http://ch.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1,065 kB]
Get:11 http://ch.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [273 kB]
Get:12 http://ch.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:13 http://ch.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [7,972 B]
Get:14 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [38.7 kB]
Get:15 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [42.1 kB]
Get:16 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Fetched 4,587 kB in 1s (3,389 kB/s)                                 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.
```

From sudo apt update
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

I just read the link on partial upgrades. Since I accepted the partial upgrade, I am not sure what was done. I have system backups and I can go back to a state before the partial upgrade.

---

### Post by srope01 on 2020-04-16
Some more info from tests.  

I made a backup of my current state so that I can try going back to the state before I had this problem (a backup from February 22). When I restored it, I then ran Software Updater and I get the dialog box attached: ```
Not all updates can be installed, run a partial upgrade, to install as many updates as possible.
``` As advised I choose not to do the partial upgrade and I just close the dialog box. When I reboot though, something must have happened as I have the problem of the login going into the sleep state again. 

 I then went back to the February 22 state. This time I do not run the Software Updater after login. I reboot immediately and I can login normally. Then I wait for awhile (I can hear my disk being accessed). I suspect the Software Updater is working. This seems to be the case as when I try to install software using the Software Centre, I get ```
Could not lock /var/lib/dpkg/lock-frontend -open Resource temporarily unavailable
```

After about two minutes, my disk is no longer being accessed and when I reboot, I have the sleep state problem again!  This seems to imply that something is being installed from upstream that messes up my system.

Any idea of what to do?

---

### Post by mörgæs on 2020-04-17
If you have backups in place I suggest that you don't spend more time on rescuing 18.04. A clean install of 20.04 is a faster and safer approach.

---

### Post by srope01 on 2020-04-17
Yes, the problem is not that serious as I can still login. I guess it is something that should be fixed as 18.04 will be supported to 2023. I won't be going to 20.04 immediately when it is released though so if anyone else sees this problem, please bump this thread back to the top.

---

### Post by dino99 on 2020-04-17
Why not using the terminal for upgrading instead of your blindly way ? Its easier to know which package(s) cant be upgraded (partial one(s) might be avoided)

---

