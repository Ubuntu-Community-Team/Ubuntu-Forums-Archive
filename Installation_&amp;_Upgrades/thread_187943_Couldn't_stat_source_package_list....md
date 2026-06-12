---
title: "Couldn't stat source package list... ?"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by skelooth on 2006-06-03
I get this error when using synaptic ... the upgrade 'seems' to have worked right.... ?? Could someone explain what these hieroglyphics mean, and how i can fix them?

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by hod139 on 2006-06-03
Looks like someting is wrong with your sources.list file.  Did you edit it by hand?

Anyways, I have attached my sources.list which is a standard Dapper version.  You should be able to replace /etc/apt/sources.list with mine.  Back up your current list if you are nervous.

```

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by skelooth on 2006-06-03
hmm, here's mine, let's have a look :D

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted


deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

 # Wine Official Package Mirror
#deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
#deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

---

### Post by skelooth on 2006-06-03
ahhhh what the hell posessed me to try and upgrade???

```
E: /var/cache/apt/archives/knetworkconf_4-0x1.2fcf500000072p-1363.5.2-0ubuntu8_i386.deb:  trying to overwrite `/usr/lib/pkgconfig/system-tools-backends.pc', which is also in package system-tools-backends
```

Realy, I don't know wtf is going on. I have 120 broken packages... it won't let me reinstall any, and some of them are system critical...  I get errors like that.

copy pasting the sources list above did help btw...

---

### Post by skelooth on 2006-06-03
okay, i deleted/removed all broken packages and I'm smart updating again. Apparently everything kde related was broken + a few odds and ends like the shared c libraries, cvs, etc etc... 

I'll just reinstall anything I 'need' after. Here's to crossing my fingers. Damn you dapper for sucking up all of my time today.

edit, this sucks sitting here babysitting synaptic.... this is wasting my entire day off....

---

### Post by skelooth on 2006-06-03
*a million hours later*

LVM2 is the ONLY package I can't seem to upgrade/update.... is it safe to remove it?!?!? I get this error

E: /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1_i386.deb:  subprocess pre-installation script returned error exit status 10

---

### Post by hod139 on 2006-06-03
I don't think you can remove that package safely.  If you open a terminal and type 
```
sudo apt-get dist-upgrade
```
you might get better error messages.  You may be able to force the insallation of that package by typing
```
sudo apt-get install lvm2
```
I would also suggest you install ubuntu-desktop and kubuntu-desktop if you are also running kubuntu (you mentioned kde).
```
sudo apt-get install ubuntu-desktop
```

---

### Post by skelooth on 2006-06-03
thanks, i have cleared the issues in this thread, i have another thread now about GDM not working properly.... and something is going wrong with my java development. My programs are not jarring or running right...

---

### Post by ubuntu_demon on 2006-06-04
reading the stickies might help

good luck :)

---

