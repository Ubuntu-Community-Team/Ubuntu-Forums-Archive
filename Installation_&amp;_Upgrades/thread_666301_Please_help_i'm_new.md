---
title: "Please help i'm new"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by ThePigeonKeeper on 2008-01-13
Hey everyone who sees this post! 
I'm having difficulties doing pretty much anything. I'm trying to update ubuntu 7.10...errors.
I'm trying to get my nVidia 8500gt driver...error. I try to figure out how to do it myself but i dont know how to install something when a window comes up with 6 pages of code. Please help. All i want to do is enjoy ubuntu.

ThePigeonKeeper

---

### Post by chewearn on 2008-01-13
Try post your problem specifically, one-by-one, each in a different thread.  Describe what you are trying to do, what steps you follow and post the exact error messages (if any) or the failure symptoms.

---

### Post by ThePigeonKeeper on 2008-01-13
First of all I tried installing my graphic card driver.  I've got a 8500gt with 512mb and each time i try to install the driver (NVIDIA-Linux-x86-169.07-pkg1.run) and it opens up a page that shows this:

[I]
Could not open the file /home/chris/Desktop/NVID…Linux-x86-169.07-pkg1.run.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.[/I]

then theres a bar which i can use about 40 different character codings with arabic, hebrew and a whole lot more.  If i get to install the driver ill be able to get the visual effects up.

---

### Post by chewearn on 2008-01-13
> **ThePigeonKeeper said:**
> First of all I tried installing my graphic card driver.  I've got a 8500gt with 512mb and each time i try to install the driver (NVIDIA-Linux-x86-169.07-pkg1.run) and it opens up a page that shows this:

[I]
Could not open the file /home/chris/Desktop/NVID…Linux-x86-169.07-pkg1.run.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.[/I]

then theres a bar which i can use about 40 different character codings with arabic, hebrew and a whole lot more.  If i get to install the driver ill be able to get the visual effects up.

Try this instead:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It basically automates what you are trying to do.

---

### Post by ThePigeonKeeper on 2008-01-13
Thanks that helped.

But i just got another problem... is there a way to terminate a program that wont close and intterups other programs?

---

### Post by PmDematagoda on 2008-01-13
Open System Monitor in System>Administration>System Monitor. Then go to the Processes tab, that should allow you to see and terminate or kill any processes that may be frozen or whatever else it may be.

---

### Post by ThePigeonKeeper on 2008-01-13
I found where to go but i cant find the application to kill!

---

### Post by PmDematagoda on 2008-01-13
What is the application you are trying to kill?

---

### Post by ThePigeonKeeper on 2008-01-13
the envy package installer

---

### Post by chewearn on 2008-01-13
> **ThePigeonKeeper said:**
> I found where to go but i cant find the application to kill!

There is an panel applet that allow you to click on the "stuck" window to kill it.  Right click on the top panel, select "Add to panel", find "Force Quit".

---

### Post by PmDematagoda on 2008-01-13
You can also press the Close Window button located on the top-right part of the window and then press Force Quit, this will allow you to close the non-responding program very much faster than you ever could on Windows.

---

### Post by ThePigeonKeeper on 2008-01-13
what is this panel applet

---

### Post by PmDematagoda on 2008-01-13
It is named Force Quit.

---

### Post by ThePigeonKeeper on 2008-01-13
ok thanks alot.

my next problem consists of updating ubuntu and well when i do it says it'll only be a partial(thats ok) but the after loading everything it an error message appears saying:

[I]Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.[/I]

---

### Post by PmDematagoda on 2008-01-13
Please post the results of:-
```
cat /etc/lsb-release
```
and
```
cat /etc/apt/sources.list
```

By the way, if you want a stable system, do **not** do a partial upgrade since that could cause some problems.

---

### Post by ThePigeonKeeper on 2008-01-13
how do i post those results ( sorry im reallllllllly new with linux)

---

### Post by PmDematagoda on 2008-01-13
Open the terminal. The terminal can be found in Applications>Accessories>Terminal.

When the terminal is open, enter the commands, press enter and post the results, it is as simple as that:).

---

### Post by ThePigeonKeeper on 2008-01-13
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gusty
DISTRIB_DESCRIPTION="Ubuntu 7.10"

and

cat /etc/apt/sources.list
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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

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
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ftp.debian.org](http://ftp.debian.org) etch main

---

### Post by PmDematagoda on 2008-01-13
My goodness, you have a Debian repository and the proposed updates enabled, that is why you get the partial upgrade notice.

Using the terminal, open the sources.list file for editing using:-
```
gksudo gedit /etc/apt/sources.list
```
Then edit the file to make it look like this:-
```
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

After the editing is done, save the file and execute:-
```
sudo apt-get update
```
after that is completed, Update Manager should be able to work properly.

---

### Post by ThePigeonKeeper on 2008-01-13
Thanks alot you were great help... i couldn't have found that in my entire life. Thanks again.
if i have any other problems ill post them here

---

### Post by PmDematagoda on 2008-01-13
Glad we were able to help:).

> if i have any other problems ill post them here
Please do not hesitate to do so:).

---

