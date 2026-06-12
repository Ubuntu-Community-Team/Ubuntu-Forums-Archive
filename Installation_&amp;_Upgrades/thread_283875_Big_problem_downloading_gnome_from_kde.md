---
title: "Big problem downloading gnome from kde"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by searayman on 2006-10-24
I am using kubuntu and want to switch to ubuntu without losing my files so i tried doing a sudo apt-get install gnome-desktop, i have tried all the variations of gnome-dekstop packages too and i always get this error:


mike@mike-desktop:~$ sudo apt-get install gnome-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting gnome-desktop-environment instead of gnome-desktop
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-desktop-environment: Depends: gnome-core (= 1:2.12.2.3) but it is not going to be installed
                             Depends: epiphany-browser (>= 1.8.3-2) but it is not going to be installed or
                                      galeon (>= 1.3.18) but it is not going to be installed or
                                      firefox-gnome-support but it is not going to be installed or
                                      mozilla-firefox-gnome-support but it is not installable
                             Depends: evolution (>= 2.4.1) but it is not going to be installed
                             Depends: file-roller (>= 2.12.2) but it is not going to be installed
                             Depends: gcalctool (>= 5.6.31) but it is not going to be installed
                             Depends: gconf-editor (>= 2.12.1) but it is not going to be installed
                             Depends: gdm (>= 2.8.0.6) but it is not going to be installed
                             Depends: evince (>= 0.4.0) but it is not going to be installed
                             Depends: gnome-about (>= 2.12.2) but it is not going to be installed
                             Depends: gnome-games (>= 1:2.12.2) but it is not going to be installed
                             Depends: gnome-keyring-manager (>= 2.12.0) but it is not going to be installed
                             Depends: gnome-media (>= 2.12.0-2) but it is not going to be installed
                             Depends: gnome-netstatus-applet (>= 2.12.0) but it is not going to be installed
                             Depends: gnome-system-monitor (>= 2.12.2) but it is not going to be installed
                             Depends: gnome-system-tools (>= 1.4.0) but it is not going to be installed
                             Depends: gnome-utils (>= 2.12.2-2) but it is not going to be installed
                             Depends: gnome-volume-manager (>= 1.4.0-2) but it is not going to be installed
                             Depends: ekiga but it is not going to be installed or
                                      gnomemeeting (>= 1.2.3-1experimental1) but it is not installable
                             Depends: gucharmap (>= 1.4.4) but it is not going to be installed
                             Depends: nautilus-cd-burner (>= 2.12.2) but it is not going to be installed
                             Depends: sound-juicer (>= 2.12.3) but it is not going to be installed
                             Depends: totem (>= 1.2.1) but it is not going to be installed
                             Depends: vino (>= 2.12.0) but it is not going to be installed
E: Broken packages
mike@mike-desktop:~$                                              




how can i fix it so i can easily and quickly switch to gome?

---

### Post by meng on 2006-10-24
The recommended package is ubuntu-desktop

sudo aptitude install ubuntu-desktop

(aptitude is better than apt-get for future UNinstallation)

---

### Post by searayman on 2006-10-24
i have tried this and it also does not work and goes to the end then tries to resolve dependencies, and tries and fails, then i tell it to try harder and it fails again and again

---

### Post by meng on 2006-10-24
What about
sudo aptitude -f install ubuntu-desktop

---

### Post by searayman on 2006-10-24
> **meng said:**
> What about
sudo aptitude -f install ubuntu-desktop

that also didnt work it returned the same results as if i did it without the -f

---

### Post by meng on 2006-10-24
I'm confused. Do either of these commands work?
sudo aptitude update
sudo aptitude upgrade

---

### Post by searayman on 2006-10-24
> **meng said:**
> I'm confused. Do either of these commands work?
sudo aptitude update
sudo aptitude upgrade

those commands give me this:

mike@mike-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 572B in 0s (881B/s)
Reading package lists... Done
mike@mike-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
mike@mike-desktop:~$

---

### Post by meng on 2006-10-24
After searching these forums and Google, I still don't know what is meant by Translation_en-US. So I suggest could you show your sources.list
cat /etc/apt/sources.list

---

### Post by searayman on 2006-10-24
> **meng said:**
> After searching these forums and Google, I still don't know what is meant by Translation_en-US. So I suggest could you show your sources.list
cat /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by meng on 2006-10-24
Have been searching again and can't find a solution posted. Sorry.
In any case, for whatever reason, apt-get is not connecting to all the repositories it needs to in order to recognize, download and install the packages you are interested in.

---

### Post by searayman on 2006-10-24
> **meng said:**
> Have been searching again and can't find a solution posted. Sorry.
In any case, for whatever reason, apt-get is not connecting to all the repositories it needs to in order to recognize, download and install the packages you are interested in.

this is very very frustrating, cause i dont want to do a complete re-install to get gnome cause then i would have to back up my computer and lose all my settings!

---

### Post by searayman on 2006-10-25
anyone else have any idease for me?

---

