---
title: "Ubuntu won't upgrade from 13.04 to 13.10"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by cdoebbler on 2013-10-28
Trying to upgrade from 13.04 to 13.10, but whether from Ubuntu update manage or Synatics also get error code that says my machine has to reset to 13.04. It seems to give a network error, but my network connection works fine. Here is the end of the terminal error message...what the upgrade process returns. Any assistance appreciated.  

> 

Ign [http://archive.ubuntu.csg.uzh.ch](http://archive.ubuntu.csg.uzh.ch) saucy-security/multiverse Translation-en_GB                                                                     
Ign [http://archive.ubuntu.csg.uzh.ch](http://archive.ubuntu.csg.uzh.ch) saucy-security/restricted Translation-en_GB                                                                     
Ign [http://archive.ubuntu.csg.uzh.ch](http://archive.ubuntu.csg.uzh.ch) saucy-security/universe Translation-en_GB                                                                       
Ign [http://archive.ubuntu.csg.uzh.ch](http://archive.ubuntu.csg.uzh.ch) saucy-backports/main Translation-en_GB                                                                          
Ign [http://archive.ubuntu.csg.uzh.ch](http://archive.ubuntu.csg.uzh.ch) saucy-backports/multiverse Translation-en_GB                                                                    
Ign [http://archive.ubuntu.csg.uzh.ch](http://archive.ubuntu.csg.uzh.ch) saucy-backports/restricted Translation-en_GB                                                                    
Ign [http://archive.ubuntu.csg.uzh.ch](http://archive.ubuntu.csg.uzh.ch) saucy-backports/universe Translation-en_GB                                                                      
Fetched 0 B in 6s (0 B/s)                                                                                                                            

Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
[http://ch.archive.ubuntu.com/ubuntu/dists/natty-backports/main/source/Sources](http://ch.archive.ubuntu.com/ubuntu/dists/natty-backports/main/source/Sources) 
404 Not Found [IP: 130.59.10.36 80] 
, W:Failed to fetch 
[http://ch.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/source/Sources](http://ch.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/source/Sources) 
404 Not Found [IP: 130.59.10.36 80] 
, W:Failed to fetch 
[http://ch.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/source/Sources](http://ch.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/source/Sources) 
404 Not Found [IP: 130.59.10.36 80] 
, W:Failed to fetch 
[http://ch.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/source/Sources](http://ch.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/source/Sources) 
404 Not Found [IP: 130.59.10.36 80] 
, E:Some index files failed to download. They have been ignored, or 
old ones used instead. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 
=== Command detached from window (Sun Oct 27 21:23:55 2013) ===
=== Command terminated with exit status 1 (Sun Oct 27 21:23:55 2013) ===



---

### Post by LuvLinuxOS on 2013-10-28
cdoebbler,

> Trying to upgrade from 13.04 to 13.10, but whether from Ubuntu update  manage or Synatics also get error code that says my machine has to reset  to 13.04. It seems to give a network error, but my network connection  works fine. Here is the end of the terminal error message...what the  upgrade process returns. Any assistance appreciated.  


have you tried the steps on this [page]("https://help.ubuntu.com/community/SaucyUpgrades")? And even though it does not mention it run those commands with sudo! I hope this helps!!!

Be Blessed...I Am!!!

---

### Post by coffeecat on 2013-10-28
Have a look at the full URL's for the four failed to fetch messages. Your system is trying to access Natty backports. Natty Narwhal, 11.04, is obsolete. It went end-of-life a year ago and the Natty repositories are closed. Hence the error messages.

Open Software Updater and click on the Settings button. Have a look through the various tabs and uncheck anything with "natty" in it. That will allow you to upgrade.

---

### Post by cdoebbler on 2013-10-29
Yes, that is how I got the error message I sent you.

---

### Post by cdoebbler on 2013-10-29
It checks Natty backports (not sure why as no Natty repositories are checked), but in any event it just goes on and then says it can't complete upgrade and reverts back to 13.04.

---

### Post by coffeecat on 2013-10-29
There must be a reason why it is checking Natty repositories. Post the contents of your /etc/apt/sources.list file.

---

### Post by cdoebbler on 2013-10-29
contents of /etc/apt/sources.list file. 

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.csg.uzh.ch/ubuntu/](http://archive.ubuntu.csg.uzh.ch/ubuntu/) raring main restricted
deb-src [http://archive.ubuntu.csg.uzh.ch/ubuntu/](http://archive.ubuntu.csg.uzh.ch/ubuntu/) raring restricted main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.csg.uzh.ch/ubuntu/](http://archive.ubuntu.csg.uzh.ch/ubuntu/) raring-updates main restricted
deb-src [http://archive.ubuntu.csg.uzh.ch/ubuntu/](http://archive.ubuntu.csg.uzh.ch/ubuntu/) raring-updates restricted main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.csg.uzh.ch/ubuntu/](http://archive.ubuntu.csg.uzh.ch/ubuntu/) raring universe
deb [http://archive.ubuntu.csg.uzh.ch/ubuntu/](http://archive.ubuntu.csg.uzh.ch/ubuntu/) raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://archive.ubuntu.csg.uzh.ch/ubuntu/](http://archive.ubuntu.csg.uzh.ch/ubuntu/) raring-security main restricted
deb-src [http://archive.ubuntu.csg.uzh.ch/ubuntu/](http://archive.ubuntu.csg.uzh.ch/ubuntu/) raring-security restricted main universe #Added by software-properties
deb [http://archive.ubuntu.csg.uzh.ch/ubuntu/](http://archive.ubuntu.csg.uzh.ch/ubuntu/) raring-security universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb [http://archive.ubuntu.csg.uzh.ch/ubuntu/](http://archive.ubuntu.csg.uzh.ch/ubuntu/) raring-backports restricted main universe
deb-src [http://archive.ubuntu.csg.uzh.ch/ubuntu/](http://archive.ubuntu.csg.uzh.ch/ubuntu/) raring-backports restricted main universe #Added by software-properties
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
deb [http://archive.ubuntu.csg.uzh.ch/ubuntu/](http://archive.ubuntu.csg.uzh.ch/ubuntu/) raring-proposed universe restricted main

---

### Post by coffeecat on 2013-10-29
There are four lines in your sources.list file with natty repositories, two for natty-backports and two for natty partner. You can ignore the dev cdrom line near the beginning for natty - that is already commented and thus disabled.

You have a choice. Either go back into Software Updater -> Settings and have another look for natty entries. I'm sure they'll be there. You can also open the Software & Updates window with the sources from Synaptic -> Settings -> Repositories. Have a look under the Other Software and Updates tabs. Uncheck any natty entries you see. 

The alternative to using the GUI is manually, by editing the sources.list file. Make a backup copy first in case of errors, with this terminal command:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

Now edit the sources.list file. From the terminal:

```
sudo nano -w /etc/apt/sources.list
``` 

Take care. It's a basic text editor. Place a # character at the beginning of each of the four lines with natty in them. Now press ctrl-o to save the file. Ctrl-x to exit nano.

---

### Post by cdoebbler on 2013-10-31
This worked. Many thanks.

---

### Post by cdoebbler on 2013-11-06
Upgraded but not 13.10 and for a time my machine (HP Elite 7100, i7, 2.8 GHz, 8 GB RAM) was bricked, but I just kept rebooting until it finally booted...but now it run much slower than before. Takes up to 30 minutes to boot, often apparently hanging after BIOS check with message "Press <F10> to enter Setup..." displayed on screen for about 30 minutes.

---

