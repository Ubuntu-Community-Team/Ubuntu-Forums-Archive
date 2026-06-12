---
title: "Installed Ubuntu 10.10 - Unable to Upgrade or Install Apps"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by Arc Angel on 2011-02-05
Hi all,

I'm new to Ubuntu.  I ran 10:10 off a CD and all was fine.  

I've installed onto a Dell XPS M1330 (erasing the drive) and I'm logged in fine.

However, I can't upgrade, install any applications, or drivers.  I get the following errors.

SystemError: Failed to lock/var/cache/aprt/archives/lock

**When I tried to install GIMP I received the following error:**

installArchives() failed: Selecting previously deselected package libgimp2.0. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60%dpkg: unrecoverable fatal error, aborting: 
 failed to read on buffer copy for files list for package `linux-headers-2.6.35-25-generic-pae': Input/output error 
[B]
When I tried to install the NVIDIA accelerated graphics drivers I got the following error:[/B]

SystemError: InstallArchives() failed

I run an Arts non-profit and we are thinking of using Ubuntu for some of our community programs (we develop creative learning programs in art, music, media) but this has got me stumped.

Any help greatly appreciated.

---

### Post by Old_Grey_Wolf on 2011-02-05
The error "SystemError: Failed to lock/var/cache/aprt/archives/lock" suggest you have more that one of the following in use Synaptic Package Manager, Ubuntu Software Center, or apt-get. You can only have one of them in use at a time.


Edit: If you have not updated the index of package before trying to install enter this in a terminal```
sudo apt-get update
```

---

### Post by Arc Angel on 2011-02-05
Thanks for the suggestion:

seraphim@seraphim-XPS-M1330:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick Release.gpg               
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_CA
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                    
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en    
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_CA 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates Release.gpg        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                        
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources        
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_CA
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates Release            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/main Sources               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Reading package lists... Done

How do I know if Synaptic is running?

When I try to open Synaptic I get the following error:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried running Synaptic  Package Manager to upgrade ....

I got ...

Reading database .... 60%dpkg: unrecoverable fatal error, aborting
failed to read on buffer copy for files list for package 'linux-headers-2.6-35-25-generic-pae': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

(then it hangs)

---

### Post by Arc Angel on 2011-02-05
If I try to use Ubuntu Software Centre to install GIMP I get:

installArchives() failed: Selecting previously deselected package libgimp2.0. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60%dpkg: unrecoverable fatal error, aborting: 
 failed to read on buffer copy for files list for package `linux-headers-2.6.35-25-generic-pae': Input/output error

---

### Post by arpanaut on 2011-02-05
Open a terminal and run:  (copy and paste works great)

```
sudo dpkg --configure -a
```Post back here if you get more errors.
If not try to install your program again.

---

### Post by Arc Angel on 2011-02-05
ran sudo dpkg --configure -a (OK)

Opened Ubuntu Software Centre

Tried to install a random app (in this case gCalculator)

installArchives() failed: Selecting previously deselected package galculator. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60%dpkg: unrecoverable fatal error, aborting: 
 failed to read on buffer copy for files list for package `linux-headers-2.6.35-25-generic-pae': Input/output error

---

### Post by Arc Angel on 2011-02-06
Can anyone help with his .....

---

### Post by dino99 on 2011-02-06
clean the sources:

sudo rm /var/cache/apt/archives/*

then into synaptic, choose the "main" server instead of "ca" (it might be down or not updated), then update, upgrade

---

### Post by Arc Angel on 2011-02-06
When I try sudo rm /var/cache/apt/archives/*

I get:

rm: cannot remove `/var/cache/apt/archives/partial': Is a directory

---

### Post by Old_Grey_Wolf on 2011-02-06
While in synaptic go to the Other Software tab and remove the check next to the entries that have "archive.ubuntu.com" in them.

---

### Post by Arc Angel on 2011-02-06
In both cases, the Entries for Canonical Partners were unchecked.

The entries for Independent ([http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu)) are checked.

---

### Post by Old_Grey_Wolf on 2011-02-06
Run this command in the terminal and post the output of the command so that we can see what repositories you are using```
cat /etc/apt/sources.list
```

---

### Post by Arc Angel on 2011-02-06
Thanks for your help so far.  Much appreciated:

cat /etc/apt/sources.list

#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
seraphim@seraphim-XPS-M1330:~$

---

### Post by Old_Grey_Wolf on 2011-02-06
Get into Synaptic then select "Other..." from the "Download from:" menu. Then click on the "Select Best Server" button. It will take some time for Synaptic to test the servers and give you a suggested server. When it does, click the "Choose Server button". Then follow the instructions to Reload.

It appears that you have used some tutorial for setting up your system; because, some of the repositories you have enabled are not enabled by default. Can you post a link to the tutorial you used?

AND, I am going to go to sleep soon. We must be in different time zones.

---

### Post by Arc Angel on 2011-02-06
Hi,

I haven't used a tutorial, simply installed from a 10.10 CD I burned.

Changed the server in Synaptic.

Downloaded the updates, but when trying to install updates, I got the following errors:

(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
failed to read on buffer copy for files list for package 'linux-headers-2.1.35-25-generic-pae': Input/ourput error

E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:

---

### Post by steveneddy on 2011-02-06
From where did you download this CD from?

Was it from the Ubuntu site?

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by Arc Angel on 2011-02-06
> **steveneddy said:**
> From where did you download this CD from?

Was it from the Ubuntu site?

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Yes, [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by Old_Grey_Wolf on 2011-02-06
> **Arc Angel said:**
> 'linux-headers-2.1.35-25-generic-pae'

Linux 2.1.35-25.
:lolflag:

---

### Post by Arc Angel on 2011-02-06
Sorry, typo :)

Reading database .... 60%dpkg: unrecoverable fatal error, aborting
failed to read on buffer copy for files list for package** 'linux-headers-2.6-35-25-generic-pae'**: Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

---

### Post by Arc Angel on 2011-02-07
Any ideas from anybody as to who I can solve this problem?

---

### Post by Old_Grey_Wolf on 2011-02-08
> **Arc Angel said:**
> Any ideas from anybody as to who I can solve this problem?

Your original post suggested that you were having problems with a fresh install; however, after looking at your sources.list, it looks like you have been making mods to your system. Some of the repositories in your sources.list are not enabled by default.

Without knowing exactly what you have done to your system, I don't know what to suggest.

---

