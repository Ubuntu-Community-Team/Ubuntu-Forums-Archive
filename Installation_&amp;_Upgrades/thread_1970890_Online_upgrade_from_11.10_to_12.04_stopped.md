---
title: "Online upgrade from 11.10 to 12.04 stopped"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by manickaselvam on 2012-05-01
Hi Guys,
             I have just upgraded from 11.04 to 11.10 online. Everything were went perfectly. 

But when i try to upgrade from 11.10 to 12.04 using the "Update Manager", it has come to the stages 1) Preparing to upgrade 2) Setting new software channels 3) Getting new packages (downloaded the entire package), 4) Installing the upgrades.....

But here my laptop is not continuing the upgrade at  "Preparing to configure libnih-dbus1".... No more progress from that stage...

In Terminal i can see the following message : 
locale: /lib/i386-linux-gnu/libc.so.6: version 'GLIBC_2.15' not found (required by locale)
Checking for services that may need to be restarted...
Checking init scripts...
Checking for services that may need to be restarted...
Checking init scripts...

Since the upgrade is in the half way, If i reboot i couldn't use this system anymore... Could you please suggest me what can i do now? I want to do something to continue this upgrade from there...

I"m using 
DELL INSPIRON 1525, 2GB RAM, 160 GB HDD, Intel Core 2 Duo, 1 Mbps internet connection. 


Waiting for your valuable suggestion please.

Regards
Manicks

---

### Post by NoBugs! on 2012-05-01
Did you try running "update-manager" command again?

---

### Post by manickaselvam on 2012-05-01
Thanks for the quick reply. 

No i didn't tried it. After your reply i'm doing this. It is warning me "Partial upgrade". But that too not continuing... "Unable to get excessive lock"... Aptitude is already running (please close that application first)....

How can i close the running "aptitude"...

Regards
Manicks

---

### Post by manickaselvam on 2012-05-01
I tried to stop the "aptitude"

sudo killall -9 apt-get sudo rm /var/lib/dpkg/lock

But with no success.

---

### Post by manickaselvam on 2012-05-01
Cool... I tried it again to start "update manager"... Now it has started, but i got this error 'The upgrade will continue but the 'libc6' package may not be in a working state. Please consider submitting a bug report about it.'

Package list libc6 is not ready for configuration current configuration 'half installed'

Seems to be a bug...

Will report it, now the installation is continuing...

---

### Post by manickaselvam on 2012-05-01
Also i'm getting one more error...

Could not install '/var/cache/apt/archives/libnih1_1.0.3-4ubuntu9_i386.deb'

The upgrade will continue but the '/var/cache/apt/archives/libnih1_1.0.3-4ubuntu9_i386.deb' package may not be in a working state. Please consider submitting a bug report about it.

---

### Post by manickaselvam on 2012-05-01
Still getting another Pre-dependancy problem....

Could not install '/var/cache/apt/archives/debianutils_4.2.1ubuntu2_i386.deb'

The upgrade will continue but the '/var/cache/apt/archives/debianutils_4.2.1ubuntu2_i386.deb' package may not be in a working state. Please consider submitting a bug report about it.

---

### Post by manickaselvam on 2012-05-01
I will document it here first (I dont have any backup drive - if it crashes in the half way then i do have nothing to recover it)

Another pre-dependancy error

Could not install 'debianutils'

The upgrade will continue but the 'debianutils' package may not be in a working state. Please consider submitting a bug report about it.

Could not install '/var/cache/apt/archives/libpam-modules_1.1.3-7ubuntu2_i386.deb'

The upgrade will continue but the '/var/cache/apt/archives/libpam-modules_1.1.3-7ubuntu2_i386.deb' package may not be in a working state. Please consider submitting a bug report about it.

Could not install 'libpam-modules'

The upgrade will continue but the 'libpam-modules' package may not be in a working state. Please consider submitting a bug report about it.

Could not install 'desktop-file-utils'

The upgrade will continue but the 'desktop-file-utils' package may not be in a working state. Please consider submitting a bug report about it.

Could not install '/var/cache/apt/archives/perl-base_5.14.2-6ubuntu2_i386.deb'

The upgrade will continue but the '/var/cache/apt/archives/perl-base_5.14.2-6ubuntu2_i386.deb' package may not be in a working state. Please consider submitting a bug report about it.


I'm getting lot of pre-dependency error... expecting the installation to continue... Please suggest me what should i do if the upgrade is partial...

---

### Post by jadtech on 2012-05-01
did you read the upgrade documentation this is a know issue for some 
there was advice   to install apt python-apt before doing the upgrade for some it becomes an issue python-apt which is part of the upgrade can open late and cause this  problem ..

---

### Post by manickaselvam on 2012-05-01
Sorry i didn't read it. Will try to figure it out... Many packages are missing... Can i do it right now so that my upgrade will be successfull...

---

### Post by jadtech on 2012-05-01
you should be able to  update and install python-apt if it hasnt  in the end with the upgrade    and then continue the upgrade  I will warn you the side effect of this  after you reboot will be the lack of any actualy graphics icons  and such if its anything like my first upgrade attempt  several weeks ago

---

### Post by manickaselvam on 2012-05-01
Processing were halted because there were too many errors

---

### Post by jadtech on 2012-05-01
> **manickaselvam said:**
> Processing were halted because there were too many errors

well  hopefully that is to your good I wasnt as fortunate :)

---

### Post by The Rnegade on 2012-05-02
> **manickaselvam said:**
> Hi Guys,
             I have just upgraded from 11.04 to 11.10 online. Everything were went perfectly. 

But when i try to upgrade from 11.10 to 12.04 using the "Update Manager", it has come to the stages 1) Preparing to upgrade 2) Setting new software channels 3) Getting new packages (downloaded the entire package), 4) Installing the upgrades.....

But here my laptop is not continuing the upgrade at  "Preparing to configure libnih-dbus1".... No more progress from that stage...

In Terminal i can see the following message : 
locale: /lib/i386-linux-gnu/libc.so.6: version 'GLIBC_2.15' not found (required by locale)
Checking for services that may need to be restarted...
Checking init scripts...
Checking for services that may need to be restarted...
Checking init scripts...

Since the upgrade is in the half way, If i reboot i couldn't use this system anymore... Could you please suggest me what can i do now? I want to do something to continue this upgrade from there...

I"m using 
DELL INSPIRON 1525, 2GB RAM, 160 GB HDD, Intel Core 2 Duo, 1 Mbps internet connection. 


Waiting for your valuable suggestion please.

Regards
Manicks

every time a new ubuntu comes out there is a flood of threads like this one on this forum, advice, do not upgrade, do a fresh install, upgrades never work right. the only possible solution i can thing of is to switch the server in your software sources from main to the other one. if it already isnt set to main then switch it to main. what ever it is switch it to the opposite

---

### Post by QIII on 2012-05-02
> **The Rnegade said:**
> upgrades never work right.

This is patently untrue.  Many people use the ugrade route rather than installing fresh.

The problem with an absolute statement is that a single anecdotal example to the contrary renders it void.

I do fresh installs.  But I reserve a machine or two to test upgrading.  It worked just fine on the two machines I tried it on this time.

OP:  Before you attempted the upgrade, did you do a complete update?  It can be problematic if you don't.  Also, as above, you may have run afoul of the release notes. That is something to take a look at prior to the next round.

By chance did you remove a package you didn't think you wanted?  Sometimes that will remove other packages that may cause dependency issues later.  You may have seen "The following additional packages will be removed" in the command line or a lot of extra "To be removed" entries when doing it from your package manager.

---

