---
title: "Upgrade 10.04 LTS to 12.04 LTS failure"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by n4pgw on 2013-02-10
> 
buck@Racoon:~$ do-release-upgrade -d
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
Failed to fetch
Fetching the upgrade failed. There may be a network problem. 
buck@Racoon:~$ 


I am trying to upgrade, but I can't seem to get past this  message.  There is no network problem here and I have tried the main,  italian, and duke repositories.  

The above message came from the command line, but I also get the error using the graphic update manager.

When I look in the update manager, I see 10.10 available, but then get a  warning message that it is no longer supported, but I can upgrade to  get to other upgrades.  However, it always fails as printed above.

I have burned a copy of 12.04 and ran it live to see if there were any  problems.  The only difference was the settings on one of my monitors  which could have more choices, but doesn't in that setting.  I'll worry  about that after I get done with the upgrade.

Is it possible to UPGRADE from the CD-ROM?  I could only find a new  install and I really don't want to start over from scratch like I were  on windows.

---

### Post by dino99 on 2013-02-10
before dist-upgrading, its a good idea to:

- check /etc/apt/sources.list & comment out all the non genuine repo (ppa, ...)
- update
- clean the system: clean/autoclean/autoremove/gtkorphan/bleachbit

then if the command line fail again, you can change to "precise" inside the sources.list (sudo gedit /etc/apt/sources.list) then update/upgrade

---

### Post by n4pgw on 2013-02-10
> **dino99 said:**
> before dist-upgrading, its a good idea to:

- check /etc/apt/sources.list & comment out all the non genuine repo (ppa, ...)
- update
- clean the system: clean/autoclean/autoremove/gtkorphan/bleachbit

then if the command line fail again, you can change to "precise" inside the sources.list (sudo gedit /etc/apt/sources.list) then update/upgrade

Rather than edit the .list, I unchecked the repositories in Synaptic Package Manager.  

I ran the update

I had to install bleachbit and was able to check the options - clean, autoclean and autoremove. 

I had 166 files and 2 special files. It was unable to delete.

> [Errno 13] Permission denied: '/var/cache/apt/archives/software-properties-kde_0.75.10.3_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libreoffice-style-tango_1%3a3.5.7-0ubuntu1~lucid1_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/python-uno_1%3a3.5.7-0ubuntu1~lucid1_amd64.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libcommons-collections3-java_3.2.1-4_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/uno-libs3_3.5.7-0ubuntu1~lucid1_amd64.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/gpgv_1.4.10-2ubuntu1.2_amd64.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libavfilter-extra-0_4%3a0.5.9-0ubuntu0.10.04.3+medibuntu1_amd64.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/firefox-locale-en_18.0.2+build1-0ubuntu0.10.04.1_amd64.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libboost-program-options1.40.0_1.40.0-4ubuntu4_amd64.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libreoffice-draw_1%3a3.5.7-0ubuntu1~lucid1_amd64.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libc6-prof_2.11.1-0ubuntu7.12_amd64.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/kompozer-data_1%3a0.8~b1-2_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/bogofilter-bdb_1.2.1-0ubuntu1.2_amd64.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libavformat-extra-52_4%3a0.5.9-0ubuntu0.10.04.3+medibuntu1_amd64.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/oxygen-icon-theme_4%3a4.4.5-0ubuntu1_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/kompozer_1%3a0.8~b1-2_amd64.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/openclipart-png_2.0-1ubuntu1~lucid1_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libjline-java_0.9.94-5_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/shared-desktop-ontologies_0.3-1_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libreoffice_1%3a3.5.7-0ubuntu1~lucid1_amd64.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/install-package_0.5.2_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libjtidy-java_7+svn20070309-4_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libmysqlclient16_5.1.67-0ubuntu0.10.04.1_amd64.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/fldigi_3.21.68-1~kamal~lucid_amd64.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/python-kde4_4%3a4.4.5-0ubuntu1.2_amd64.deb'

---

### Post by n4pgw on 2013-02-10
I ran update manager.  It gives the following error: > Not all updates can be installed: Run a partial upgrade...Then I get this message: > Changes for the versions:
9.5.1-1lucid1
9.5.1-1precise1

This change is not coming from a source that supports changelogs.

Nothing seems to update and I get the same error trying to upgrade.

---

### Post by grahammechanical on 2013-02-10
As you are running 10.04 you should be able to upgrade to 12.04. From one LTS to the next LTS.

In Synaptic settings you need to set to be notified about the next LTS release. Then you should get a button inviting you to upgrade.

If you have set it to never, then you will not get a notification. If it is set to the next release, then you will not get a notification because the next release is out of life. 

Regards.

---

### Post by n4pgw on 2013-02-16
The problem I had seems to be related to either the servers I tried, or more likely, it has something to do with the files available to perform the upgrade.  

> do-release-upgrade -d
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
Failed to fetch
Fetching the upgrade failed. There may be a network problem.When loading the CD-ROM while in 10.04, I had no options for upgrading.  However, when I did boot on the 12.04 disc, I was given the option to upgrade.  However, by that time I had damaged my system so I decided to perform a full install instead. 

I had no network problem, so either the files are no longer available or they are no longer compatible.

I am glad this newer LTS lasts five years, with four remaining.  

This release of Ubuntu has been the worst upgrade experience I have every had including all my experiences with Windows.  

I am very disappointed with the team responsible for releasing this version of Ubuntu.

---

