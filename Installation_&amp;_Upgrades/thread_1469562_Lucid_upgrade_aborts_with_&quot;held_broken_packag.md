---
title: "Lucid upgrade aborts with &quot;held broken packages&quot; message"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by yelvington on 2010-05-02
I'm trying to upgrade from Karmic to Lucid on my Acer 1410. The Lucid upgrade tool gets to the "Setting new software channels" stage and then spends about 10 minutes whacking the hard drive while reporting "Calculating the changes."

At the end of the process I get this error:

Could not calculate the  upgrade
An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.


I don't know what "held broken packages" it's complaining about, but I have done the following without success:

* Run Synaptic, clicked on Edit/Fix Broken Packages
* Run apt-get clean; apt-get autoclean;
* Run Synaptic and completely removed Boxee and Hulu.

What next?

---

### Post by Butterbelly on 2010-05-02
I had (or have?) similar problems.  In the end I donned my deer-stalker and picked up a magnifying glass and by tracking down the applications associated with the offending libraries (that failed to fetch) I completely removed those apps or libraries.  Eventually I got past the error messages but it was a pain!  Worryingly the apps I had to remove were a spell-checker and Tomboy and some Python libraries.

The install step is still running and as I write this I got a warning that some resources are missing, oo-er.....?

---

### Post by floogy on 2010-05-02
You can search for Packages with the staus 'hold':
aptitude search "~ahold" | grep "^.h"

> If you want to check which packages you had on hold for apt-get, you should use

# dpkg --get-selections | grep hold

If you changed and recompiled a package locally, and didn't rename it or put an epoch in the version, you must put it on hold to prevent it from being upgraded.

The “hold” package state for aptitude can be changed using:

# aptitude hold package_name

Replace hold with unhold to unset the “hold” state. 

[http://www.debian.org/releases/lenny/i386/release-notes/ch-upgrading.en.html#package-status](http://www.debian.org/releases/lenny/i386/release-notes/ch-upgrading.en.html#package-status)

---

### Post by yelvington on 2010-05-02
I managed to break the logjam by going to /var/log/dist-upgrade/ and looking in the most recent numbered directory for apt.log. The last few lines of the (very verbose) logfile read:


Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 1 as a solution to xserver-xorg-video-all 10005
Done

This seems to be the point at which everything failed. There was no such package in the system, nor do I have a clue as to why it wanted such a package (I don't have nvidia hardware). Manually installing video-nouveau allowed Update Manager to proceed to the rest of the installation process.

Hours later (!!!!) I had an upgraded, but broken, system. Again the problem was Xorg, which didn't see any input from the mouse OR the keyboard, so I couldn't log in.

After several false starts I rebooted into a shell, logged in as root, and had a working mouse. However, the keyboard was nonresponsive.

Synaptic recommended a series of major upgrades/deletions/changes to Xorg. I applied them (with some trepidation) and now the system is working again.

Overall, this is the worst successful upgrade experience I've had with Ubuntu, and quite a disappointment. My original installation of Ubuntu on this laptop took only 18 minutes, about the same time as first boot of Windows 7, and was nearly flawless. If I wasn't comfortable digging around in system files, this would have failed completely.

(I say "worst successful" because I have a desktop machine whose wireless networking was wiped out by an upgrade to Karmic, and I've never gotten around to fixing it because I need a network connection to get the drivers.)

---

