---
title: "Installation Everything"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by curryjl on 2007-11-07
Ok I have a few questions first one to start with is installing WoW i can't get the tray to eject thru the Wine interface.. says a program is not allowing it to eject... and for the more important one all the programs in ubuntu from the add/remove section wont install i get the error ... for example
Xchat-GNOME IRC Chat cannot be installed on your computer type (i386)
either the application requires special hardware features or the vendor decided to not support your computer type ...


but that error comes along with all the programs i try to install any help would be greatly appreciated

---

### Post by PmDematagoda on 2007-11-07
I don't believe you can open the CD tray using through WoW running through Wine since it is just the Windows emulator for basic stuff and the CD-ROM path for Linux is different when compared with that of Windows, so I do not think there is an easy solution for your WoW problem. 

But about your architecture problem, could you please tell the result of:-
```

uname -a
```

---

### Post by curryjl on 2007-11-07
How would u go about installing WoW then???  

james@james-laptop:~$ sudo get-apt install xchat
sudo: get-apt: command not found
james@james-laptop:~$ sudo apt-get install xchat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xchat: Depends: tcl8.4 (>= 8.4.5) but it is not installable
E: Broken packages
james@james-laptop:~$

---

### Post by SpiritIsReality on 2007-11-07
howdy
from here [http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html)
you could try
> 
If an installation breaks in the middle of the process and you find that it's no longer possible to install or remove packages, try running these two commands:

     # apt-get -f install
     # dpkg --configure -a

And then try again. It may be necessary to run the second of the above commands more than once.

so that would be 
sudo apt-get -f install
sudo dpkg --configure -a
trails
	
PmDematagoda ... you're right. should check uname -a

---

### Post by curryjl on 2007-11-07
The following packages have unmet dependencies:
  xchat: Depends: tcl8.4 (>= 8.4.5) but it is not installable
that error right there is telling me i need the file tcl8.4 which i downloaded but i cant seem to correctly install any guidance would be appreciated :)

---

### Post by curryjl on 2007-11-07
Linux james-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux



how come i get the feeling its suppose to say i386

---

### Post by SpiritIsReality on 2007-11-07
howdy
fred@piii:~$ uname -a 
Linux piii 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
looks ok
trails

---

### Post by curryjl on 2007-11-07
so how would u go about installing WoW still using Wine... and hows the figuring out whats up with the error of mine up above i downloaded that specific file the tcl8.4  but i dont know what to do with it

---

### Post by SpiritIsReality on 2007-11-07
howdy
You could try running these ?
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg --configure -a
trails
that's two - in front of configure.

---

### Post by curryjl on 2007-11-07
still nothing :(

---

### Post by SpiritIsReality on 2007-11-07
could you post the result of?
cat /etc/apt/sources.list

any help here?
[http://ubuntuforums.org/archive/index.php/t-339436.html](http://ubuntuforums.org/archive/index.php/t-339436.html)

---

### Post by curryjl on 2007-11-07
james@james-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main restricted
james@james-laptop:~$ 



thanks for all the help

---

### Post by SpiritIsReality on 2007-11-07
howdy
Please see Post # 14.

This is the /etc/apt/sources.list file from this rig

# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


--------------------
You could type Alt-F2 (hold down Alt key, and tap F2 key)
Then in the run box, type
gksudo gedit /etc/apt/sources.list
and run it.
In the gedit window that opens, you will see your /etc/apt/sources.list
Highlight the whole thing and then press the backspace key to delete it.
(or click Edit -> Select All and then tap the backspace key)
Copy the etc/apt/sources.list from this post,
and Paste it into your empty gedit window.
Save it and Close.

run in terminal
apt-get update
apt-get upgrade
apt-get install xchat

if that doesn't work, run
apt-get update
apt-get dist-upgrade
apt-get install xchat

hope it all goes well
trails
8600m gs
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22nvidia+8600m+gs%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22nvidia+8600m+gs%22&btnG=Google+Search&meta=)

---

### Post by PmDematagoda on 2007-11-07
I would suggest you to try and find the source of the problem, as it is there is something wrong which may not be fixed simply by copying and pasting.

First try and reactivate the sources by going to System>Administration>Software Sources, then select all the choices in the Ubuntu Software tab and the Important Security Updates, Recommended Updates and Unsupported Updates in the Updates tab.

When you are going to close it(There will be no necessity of saving it, it will be done automatically) it will ask you to reload all records of the repos, reload them and see if you can do that successfully.

After what you get as a result we can decide what can be done next.

---

### Post by curryjl on 2007-11-07
I need help installing a nvidia 8600m gs driver for linux now the correct one so i can run WoW thru wine i cant seem to get it to work tho... any help would be greatly appreciated

---

### Post by PmDematagoda on 2007-11-07
Did you try :-

```
sudo dpkg-reconfigure xserver-xorg
```

When you reach configuration select the driver to be nvidia and any other choices you believe are right.

After configuration, to try and get your GUI, do:-

```
startx
```

---

### Post by curryjl on 2007-11-07
I have a really low framerate for WoW at the login screen i imagine about a 1fps or maybe less :( is there a reason for that....

---

