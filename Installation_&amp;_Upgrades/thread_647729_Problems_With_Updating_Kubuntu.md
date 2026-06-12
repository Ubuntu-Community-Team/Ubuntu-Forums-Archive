---
title: "Problems With Updating Kubuntu"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by inzi2u on 2007-12-22
hi everyone,

I just installed Kubuntu, And i can't seem to update from the adept manager.
every time i press the fetch updates button. and another upgrade button lights up.. i click on that to upgrade.. and it downloads something.. Tries to install and then gives an error saying about adept manager couldnot be upgraded.
I can't seem to update anything.. has anyone faced this same problem.. how did u solve it?
Please help me. i am a noob at this stuff..

`inzi

---

### Post by eternicode on 2007-12-22
What packages is it unable to update?  Can you post the error message(s)?

Might also try aptitude (command line updater): ```
sudo aptitude dist-upgrade
```

---

### Post by inzi2u on 2007-12-23
It is unable to update any packages....especially using adept manager... so i removed adept manager.. 
I prefer using synaptic from ubuntu.. but i don't know how to install it.. when i want to install synaptic using this command

```
 sudo apt-get install synaptic
```

it gives me this error

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate
```

do i need to add it to my sources list.. could you please help me out.. wat do i need to add to my sources list so that i can download synaptic..

---

### Post by inzi2u on 2008-01-22
How come noone replied to this thread.. so i just wanted to know. if anyone has a solution for this problem please share the info.

---

### Post by Partyboi2 on 2008-01-22
can you post your sources.list
```
cat /etc/apt/sources.list
```

---

### Post by tptbz on 2008-01-23
Hello,

Thought I'd jump in because I just installed Kubuntu 7.10 on my Dell Vostro 200 Desktop.

Everything went well and worked well after installation.

But, when I clicked the icon indicating that there were about 127 updates available things went wrong.

The complete error:
Could not commit changes - Adept Manager
There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.
OK

I'm new to Kubuntu and it sounds like all the updates have failed and all that's left is a broken OS.

Can someone shed light onto this?  Is my OS now broken due to the error message I encountered during the OS updates?  Is adept broken?  This is the second time I installed because of this error.

Partyboi2 asked for a sources.list.  Mine is:
***start sources.list***
# 
# deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.2)]/
 gutsy main restricted

deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.2)]/
 gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade
 to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main
 restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the
 Ubuntu
## team, and may not be under a free licence. Please satisfy yourself
 as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu
 security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the
 Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself
 as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the
 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it
 includes
## newer versions of some applications which may provide useful
 features.
## Also, please note that software in backports WILL NOT receive any
 review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main
 restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main
 restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to
 Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main
 restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
***end sources.list***

Thank you.

TPB

---

### Post by eternicode on 2008-01-23
In my experience, a "committing" error in adept is usually due to erroneous downloaded packages.

First off, unless you're using the Kubuntu installation CD to install/upgrade programs, you should probably comment out the sources.list line referring to the cdrom:

```

change

deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.2)]/ gutsy main restricted

to

# deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.2)]/ gutsy main restricted

```

After that run
```
sudo aptitude update
```
in a terminal, to update your sources, then
```
sudo aptitude clean
```
to get rid of any downloaded packages.  This won't uninstall anything, it'll just get rid of the erroneous files that were downloaded.

---

### Post by DMK62 on 2008-01-23
I have run into the packages not committing problem with updating Kubuntu. It seems that there are several updates dependant on qt3-mt ( not positive ) and adept is one of them so it spews a ton of error messages. I just let adept run until it had finished and listed the packages that could not be updated. I closed adept and rebooted and from konsole i ran sudo apt-get update and then sudo apt-get upgrade and selected N for default when prompted. The packages that could not be committed before in adept were all upgraded. Did another reboot after the update.

hth 

Dale

---

### Post by tptbz on 2008-01-23
Hi eternicod,

Thank you for responding.  I did as you suggested and only issue is
 shown below in step 3.  Everything worked successfully.  After completing
 all that's show below would you suggest I continue to use Adept
 Manager?  Or would you suggest another program such as apt from the command
 line?  I believe I read somewhere that Adept Manager is a nice gui front
 end to apt so I guess using Adept is using apt.  So, would you
 recommend I just keep using this?

Below you can see the steps I took with the output as I followed your
 recommmendations:

1) As you suggested I changed the deb cdrom line to read:

# deb cdrom...

2) And then ran:

sudo aptitude update

3) But "sudo aptitude update" finished with the following errors:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to
 correct                                       the problem.
E: Couldn't rebuild package cache

4) So, I ran what was suggested above and selected [default=N] for
 "/etc/qt3/qt_plugins_3.3rc" :

$ sudo dpkg --configure -a
Setting up libc6 (2.6.1-1ubuntu10) ...

Setting up libqt3-mt (3:3.3.8really3.3.7-0ubuntu11.1) ...

Configuration file `/etc/qt3/qt_plugins_3.3rc'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** qt_plugins_3.3rc (Y/I/N/O/D/Z) [default=N] ?

Setting up libavahi-qt3-1 (0.6.20-2ubuntu3.2) ...

Setting up kdelibs4c2a (4:3.5.8-0ubuntu3.1) ...

Setting up konsole (4:3.5.8-0ubuntu2.1) ...

Setting up kdesudo (1.1-0ubuntu2.2) ...
Setting up adept-common (2.1.3ubuntu17.1) ...

Setting up kdebase-bin (4:3.5.8-0ubuntu2.1) ...

Setting up libkonq4 (4:3.5.8-0ubuntu2.1) ...

Setting up kate (4:3.5.8-0ubuntu2.1) ...

Setting up adept-updater (2.1.3ubuntu17.1) ...

Setting up kmenuedit (4:3.5.8-0ubuntu2.1) ...

Setting up kdeprint (4:3.5.8-0ubuntu2.1) ...

Setting up ksplash (4:3.5.8-0ubuntu2.1) ...

Setting up kfind (4:3.5.8-0ubuntu2.1) ...

Setting up kdesktop (4:3.5.8-0ubuntu2.1) ...

Setting up khelpcenter (4:3.5.8-0ubuntu2.1) ...

Setting up ksysguard (4:3.5.8-0ubuntu2.1) ...

Setting up adept-installer (2.1.3ubuntu17.1) ...

Setting up kwin (4:3.5.8-0ubuntu2.1) ...

Setting up adept-manager (2.1.3ubuntu17.1) ...

Setting up kdebase-kio-plugins (4:3.5.8-0ubuntu2.1) ...

Setting up kdm (4:3.5.8-0ubuntu2.1) ...

Setting up openoffice.org-kde (1:2.3.0-1ubuntu5.3) ...

Setting up kicker (4:3.5.8-0ubuntu2.1) ...

Setting up klipper (4:3.5.8-0ubuntu2.1) ...

Setting up adept-batch (2.1.3ubuntu17.1) ...
Setting up kdepasswd (4:3.5.8-0ubuntu2.1) ...

Setting up adept-notifier (2.1.3ubuntu17.1) ...
Setting up adept (2.1.3ubuntu17.1) ...
Setting up ksmserver (4:3.5.8-0ubuntu2.1) ...

Setting up kcontrol (4:3.5.8-0ubuntu2.1) ...

Setting up konqueror (4:3.5.8-0ubuntu2.1) ...

Setting up konqueror-nsplugins (4:3.5.8-0ubuntu2.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

5) Next, I ran:

sudo aptitude update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted
 Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe
 Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse
 Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted
 Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe
 Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse
 Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 3B in 0s (4B/s)
Reading package lists... Done

6) Finally running:
$ sudo aptitude clean
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

At this point would you consider the computer to be in a stable state?
Would you recommend I just keep using the Adpet Manager?

Thanks, TPB

---

### Post by Partyboi2 on 2008-01-23
tptbz,
from the looks of everything you posted in your last post the problem has now been fixed and you system should be ok again.:):)

---

### Post by DMK62 on 2008-01-23
tptbz,

Your system should be fine now. Just my personal preference ... I use Adept for updates as Kubuntu uses it as the default update manager. I use synaptic for installing packages  ( when I am too lazy to use terminal or need to search for a package ). I haven't run into any problems with having them both on my system. From previous versions of Kubuntu and adept I have found adept to be troublesome at times and often crashed. Install synaptic and see which you prefer. Adept as a gui front end does offer more options than synaptic.

I may be wrong but I think when it comes to something like a dist-upgrade you would need to use adept. Familiarize yourself with both of them and you can't lose.

Hope you can now get to enjoying your Kubuntu install. Feel free to ask as many questions as you need. It helps you and others that will read your posts.

Dale

---

### Post by tptbz on 2008-01-23
Thanks for your help!

---

