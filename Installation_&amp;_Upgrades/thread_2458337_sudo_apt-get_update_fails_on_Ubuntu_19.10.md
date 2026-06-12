---
title: "sudo apt-get update fails on Ubuntu 19.10"
date: 2021-02-22
forum: Installation &amp; Upgrades
---

### Post by boschma1 on 2021-02-22
Hi there:

I need to upgrade my Ubuntu 19.10 to 20.10. I intended to 
$ sudo apt update 
$ sudo apt upgrade
$ sudo apt dist-upgrade

But already the first step fails: sudo apt update results in 

```
Hit:1 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) eoan InRelease
Ign:2 [http://azure.archive.ubuntu.com/ubuntu](http://azure.archive.ubuntu.com/ubuntu) eoan InRelease
Ign:3 [http://azure.archive.ubuntu.com/ubuntu](http://azure.archive.ubuntu.com/ubuntu) eoan-updates InRelease
Ign:4 [http://azure.archive.ubuntu.com/ubuntu](http://azure.archive.ubuntu.com/ubuntu) eoan-backports InRelease
Err:5 [http://azure.archive.ubuntu.com/ubuntu](http://azure.archive.ubuntu.com/ubuntu) eoan Release
  404  Not Found [IP: 20.54.144.51 80]
Err:6 [http://azure.archive.ubuntu.com/ubuntu](http://azure.archive.ubuntu.com/ubuntu) eoan-updates Release
  404  Not Found [IP: 20.54.144.51 80]
Hit:7 [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty InRelease
Ign:8 [http://download.opensuse.org/repositories/home:/strycore/xUbuntu_16.04](http://download.opensuse.org/repositories/home:/strycore/xUbuntu_16.04)  InRelease
Err:9 [http://azure.archive.ubuntu.com/ubuntu](http://azure.archive.ubuntu.com/ubuntu) eoan-backports Release
  404  Not Found [IP: 20.54.144.51 80]
Err:10 [http://download.opensuse.org/repositories/home:/strycore/xUbuntu_16.04](http://download.opensuse.org/repositories/home:/strycore/xUbuntu_16.04)  Release
  404  Not Found [IP: 195.135.221.134 80]
Ign:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security InRelease
Err:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security Release
  404  Not Found [IP: 91.189.91.38 80]
Reading package lists... Done
E: The repository 'http://azure.archive.ubuntu.com/ubuntu eoan Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://azure.archive.ubuntu.com/ubuntu eoan-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://azure.archive.ubuntu.com/ubuntu eoan-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://download.opensuse.org/repositories/home:/strycore/xUbuntu_16.04  Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu eoan-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```
Any idea how to fix this?

Thanks

---

### Post by Impavidus on 2021-02-22
19.10 reached end of life in July 2020. You should have upgraded to 20.04 before that. That's the idea behind non-LTS releases. You could try an [EOL upgrade](https://help.ubuntu.com/community/EOLUpgrades), but a fresh install may give better results. If you wish to go to 20.10, better use a fresh install instead of a double upgrade. If you don't really need 20.10, it's easier to stay at 20.04 LTS. 20.10 will be supported until July this year, 20.04 until April 2025.

---

### Post by TheFu on 2021-02-22
Don't use non-LTS releases if you can't 100% know that loading a new version every 6 months will happen.
Load 20.04 and stay with that for 2-3 yrs, then move to 22.04.  
LTS releases happen
[LIST]
[*]even years - 12, 14, 16, 18, 20, 22, 24, 26 .....
[*]in April - 04
[/LIST]

Hence the 20.04.

Don't dally too long when support is ending.  Support dates are published over a year in advance - often they are published with the initial release.

BTW, on Ubuntu, the **sudo apt dist-upgrade** doesn't do what you seem to think it does.  It will not change 19.10 --> 20.anything. Never would.  Ubuntu uses **do-release-upgrade** for that process while the current system is still supported.  So ... around May-Jule of 2020, would have been the latest time to 'do-release-upgrade' successfully to get 20.04 loaded.

At this point, you are stuck. There's the 100% certain way and their the hope-n-pray method.

Prerequisites for both:
[LIST]
[*]Backup so you can restore with 100% certainty
[*]The 19.10 system must have been maintained properly with weekly patches until the EoL happened. Often the last few weeks of patching will include updates that clean up stuff for the next release.
[*]Create a 20.04 ISO boot flash drive with a Try Ubuntu environment on it. I've needed this post release upgrade on 2 systems in the last month.
[/LIST]
If you aren't 100% certain both of those are true, you shouldn't even attempt the forced upgrade.  Just copy the data you have off and do a fresh 20.04 install. Then manually setup everything.

If you are 100% certain you have backups and did get all the patches, including the last few weeks by doing 
```
sudo apt update
sudo apt full-upgrade
```
those last weeks, then you can 
[LIST=1]
[*]Ensure /boot has sufficient storage available for 2 more kernels
[*]Ensure / has sufficient storage for a new OS - about 5G seems to be the minimum needed during the upgrade based on my recent experiences.
[*]manually modify all the sources in /etc/apt/sources.list to point to the new 20.04 release repos. Usually that means just changing the release code-name.
[*]rename all the PPAs in /etc/apt/sources.list.d/* to end in .save so those are ignored. Never do an upgrade with any PPAs involved.
[*]run **sudo apt update** - see that all the sources are found. If not, remove those that aren't core repos provided by canonical.
[*]run **sudo apt full-upgrade** - this will take hours - 1 - 4 hrs.  There will be questions asked from time to time, so you can't just walk away. You need to watch the screen and answer between 2 and 20 questions. Most will be about modified config files and whether you want to use the new ones or keep the old ones.
[*]re-run  **sudo apt full-upgrade** to ensure stuff is all updated
[*]reboot
[/LIST]
Hopefully, it will reboot into the new OS. After all, that's why we did this taking hours instead of doing a 15 minute fresh install which is 100x easier, removes any personal cruft, etc.
Check the kernel - **uname -r**
Check the release - **lsb_release -d**
Check that major stuff you need is working. Take 30 minutes. Fix the little problems.
Now it is time to clean up old packages off the system.
```
sudo apt autoclean
sudo apt autoremove

```
Lots of stuff should be removed and deleted. Perhaps a full page worth.  Probably should reboot again.  Hopefully, the most important things are still working, but perhaps not.  There is likely to be some old kernels and other packages left over from 19.10 installed.  You can find those using 
```
dpkg -l *19.10*
```
Be aware of those, but you probably don't want to remove them yet.  See if newer versions are available. The newer version of each might have a 20.04 in the name or not.  Can't hurt to force a reinstall of the generic package name. In theory, that should pick up the 20.04 version.

Of the 5 systems I've recently upgraded, 2 refused to boot post upgrade. All had issues of some sort. None had the same issues, but my systems are all snowflakes - slightly different.  Some things I expected to fail worked perfect post-upgrade. That was surprising to me.

Good luck.



It really would be much easier to do a fresh install of 20.04.

---

### Post by Hagar Delest on 2021-02-22
Personally, I've several partitions, including 2 for the system. Meaning that I install the / on one partition and when I upgrade, I install on the other one. At each upgrade, you overwrite the next to last version. Thus you have a brand new system, no risk that a former configuration item confuses the new version. And if something goes wrong, you still have the last version at hand.
Note that it means that you've other partitions at least for your documents.
Sounds complex but it may prevent such situation.

---

