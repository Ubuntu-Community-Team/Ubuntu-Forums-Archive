---
title: "unable to upgrade to 13.10 becuse of package 'unity'"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by Moses_Moore on 2013-10-18
```
$ sudo do-release-upgrade
...
Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 
```

**First problem**: it doesn't tell me what the problem is, only some guesses at what the problem might be.

**Second problem**: None of these guesses are correct.  I found out via the forums (not by any message from the software nor by reading `man do-release-upgrade` or any files in /usr/share/doc/ubuntu-release-upgrader-core/* )(which I might call a problem first-and-a-half) that a log file is written to /var/log/dist-upgrade/main.log

```
$ grep -C3 ' ERROR ' /var/log/dist-upgrade/main.log 
2013-10-18 09:26:15,596 DEBUG Marking 'xubuntu-desktop' for upgrade
2013-10-18 09:26:15,702 DEBUG blacklist expr 'unity$' matches 'unity'
2013-10-18 09:26:15,702 DEBUG The package 'unity' is marked for removal but it's in the removal blacklist
**2013-10-18 09:26:15,789 ERROR Dist-upgrade failed: 'The package 'unity' is marked for removal but it is in the removal blacklist.'**
2013-10-18 09:26:15,790 DEBUG abort called
2013-10-18 09:26:15,791 DEBUG openCache()
2013-10-18 09:26:15,791 DEBUG failed to SystemUnLock() (E:Not locked) 

```

[B]Third (actual) problem: do-release-upgrade wants to remove 'unity' and wants not to remove 'unity' at the same time, halting the upgrade.
[/B]
How do I resolve this?

I'm pretty sure I didn't manually forbid unity from being installed:
```
$ dpkg --get-selections |grep unity
gir1.2-unity-5.0:i386                install
gnome-control-center-unity            install
libunity-common                    install
libunity-core-6.0-5                install
libunity-misc4                    install
libunity-protocol-private0:i386            install
libunity-webapps0                install
libunity9:i386                    install
unity                        install
unity-asset-pool                install
unity-common                    install
unity-lens-applications                deinstall
unity-services                    install
unity-webapps-service                install

```
... I don't see a 'hold' on unity packages.  
(and while I'm looking at the preview, why aren't \[code\] blocks using a monospace font for whitespace characters?)

---

### Post by evolutionv8-5 on 2013-10-18
why don't you remove unity before upgrade and install it again after that?

---

### Post by Moses_Moore on 2013-10-18
Seems odd since Canonical itself says that 13.10 is mostly improvements to Unity:
[http://help.ubuntu.com/13.10/ubuntu-help/whats-new.html](http://help.ubuntu.com/13.10/ubuntu-help/whats-new.html)
... but I'll give it a try.

```
sudo apt-get remove unity
```

EDIT:
Does not error out this time, though it does want to remove package 'libunity-common'.  Curious.

I still wish that `do-release-upgrade` told me what the error message was was, instead of me needing to go to the forums to find out where a logfile is.

---

### Post by IvarSnaaijer on 2013-10-18
I had problems upgrading kubuntu from 13.04 to 13.10 (It started out as kubuntu 12.10, but upgraded in april). I might have accidentally installed unity in the past. 

I did get the same error ´An unresolvable problem occurred while calculating the upgrade.´ from GUI version and no clear indication of any specific problem.
I removed all third party stuff (like Medibuntu remnants and Intel driver updates) and today I almost created a bugreport because it was easier to do from the UI, but I changed my mind and found your effords, Thanks ! 

For posterity :
My logfile (/var/log/dist-upgrade/main.log) showed the same message about unity:
2013-10-18 20:12:40,860 DEBUG The package 'unity' is marked for removal but it's in the removal blacklist

But it was not preceded by ERROR. So for other people I advice to use 

[FONT=courier new]tail /var/log/dist-upgrade/main.log[/FONT]

Just after the update failed.

I did 
[FONT=courier new]sudo apt-get remove unity[/FONT]

and now I'm updating to 13.10

---

