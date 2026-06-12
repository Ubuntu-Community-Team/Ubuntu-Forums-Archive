---
title: "Update from 10.04 to 10.10 failed"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by rainbow99984 on 2010-10-27
Hi, My System spec is::Ubuntu 10.04/Kernel 2.6.32-25-generic #45-Ubuntu i686 GNU/Linux gnome::2.30.2. Laptop - Dell E6400. 
I tried updating to 10.10 by update manager,first msg:Third party sources disabled, then
" Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report."and  failed .

I tried from console as apt-get upgrade  got::

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Please guide me how to proceed from here.
Thanks
Rahul

---

### Post by cogier on 2010-10-27
The message "...this may be caused by held packages." could be a clue.
I would try the following commands in Terminal
```
 sudo apt-get install -f
```
```
 sudo apt-get autoremove
```
```
 sudo apt-get clean
```
```
 sudo apt-get update
```

Then run Update Manager (not the upgrade to 10.10), reboot if requested then try the upgrade to 10.10 again.

---

### Post by TBABill on 2010-10-27
+1. The upgrade depends on your current 10.04 to be fully updated and ready for the upgrade. And if you have installed many items outside the repos you will want to backup (if you didn't already) anything you may want available to put back into 10.10 in the event it does not upgrade properly. And note that the upgrade takes significantly longer than a fresh install (couple hours).

---

### Post by linux-hack on 2010-10-27
I advise to save everything and make a new install ... This way is more clean ...

---

### Post by mörgæs on 2010-10-27
Here is more on the fresh install, if you choose this way:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by rainbow99984 on 2010-10-28
@cogier
 Although i used apt-get install -f , Clean, update it does nothing gives the same message that i give in my problem part below the "apt-get upgrade"
have not used autoclean will try and let you guys know .
As of New/Fresh Install, I can't do that cause its my work Laptop and I'm in middle of it. have many things that i can't risk at the moment may be after some time i will give it a try.
Thanks.

---

### Post by sitex on 2010-10-30
If your system will not detect new upgrades to ubuntu 10.10, you should edit a file in /etc/update-manager/release-upgrades. 

Then you will notice new upgrades to Ubuntu 10.10 on your Ubuntu 10.04 system.. Solutionz.yolasite will guide to do it..
[Click here to fix this with related screen shots and details]("http://solutionz.yolasite.com/linux/problem-with-the-upgrade-ubuntu-10-04-to-10-10")

---

### Post by rainbow99984 on 2010-11-01
Hi All, Thanks for all Help, Finally I upgraded my system from 10.04 to 10.10. The error I got was due to Software Source settings, In my settings Pre-Released and Unsupported updates was disabled,Yesterday I enabled them and tried once again with update Manager. First i updated the 10.04 files as there's some. then I click on Upgrade and it does. Finally running and writing to you all from 10.10 :) . So far No PROBLEM :) .
Thanks a Bunch to Every One

---

### Post by thoreauthesis on 2011-01-23
Hi all,

Had the same problem for days, and all I had to do was open up Synaptic Package Manager and remove the xserver-xorg-video-nouveau (which also removed the xserver-xorg-video-all package).  After that, the upgrade went through without a hitch.  Found the solution here: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652)

Hope that helps.

---

