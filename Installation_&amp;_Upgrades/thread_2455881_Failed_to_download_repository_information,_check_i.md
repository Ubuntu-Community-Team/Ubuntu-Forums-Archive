---
title: "Failed to download repository information, check internet connection"
date: 2020-12-29
forum: Installation &amp; Upgrades
---

### Post by peterg17 on 2020-12-29
I have been getting this error attempting to upgrade to 20.04 on the software-updater. Repeated "Try Again" presses fails to resolve it.

I can easily get around it. I simply click on settings (in the software-updater window), close, and I then have the option to upgrade.

This behaviour is identical on two different repositories, including the master repository.

I am up to date with 18.04, according to the software-updater.

My internet connection is USB tethering through my mobile phone.

Also when I attempt to upgrade, I have 458 broken amd64 packages, out of 3229 amd64 installed packages, total installed packages 4641. (Not reporting as a problem here, just a feature of the issue.) Otherwise my system appears to be OK.

Very quirky.

---

### Post by dino99 on 2020-12-30
So start to clean the system first, via disabling all external sources (ppa,...) and running 'sudo apt-get autoremove'. Then update again.

---

### Post by peterg17 on 2020-12-30
I started working on the broken packages with "conflicts" and removed two packages, consolekit and libpam-ck-connector. Now the error no longer occurs. Do not know which one caused the issue.

---

### Post by rsteinmetz70112 on 2020-12-30
Glad you resolved the error. We you able to successfully upgrade?

The broken packages most likely caused the error although using a tethered internet could create problems with connecting to the repositories. Was the phone connected via WiFI or via the phone network?. Before upgrading you should always make sure all packages are up to date and fully configured. PPAs and alternate repositories can cause the upgrade to fail.
The large number of "broken" packages indicate some basic package has an issue, possible from incompatible version or build not obtained from the Ubuntu repositories.

---

### Post by GhX6GZMB on 2020-12-30
I had this a couple of weeks ago, where a broken link to a PPA caused trouble. Interestingly, the broken PPA was not listed as the error, but two other PPAs that were fully OK.

So yes, update/upgrade and clean up your PPAs first.

---

### Post by peterg17 on 2020-12-30
The usb-tethered phone is via the phone network.
I did have a launchpad ppa, but had not yet installed anything, and purging it did not change the upgrade failure.

Starting with the conflicts in apt.log, as there are only two of them, I note that libsensors4 is conflicted, as this quote from apt.log shows:
**$ grep libsensors4 apt.log**
**Broken libsensors-config:amd64 Conflicts on libsensors4:amd64 < 1:3.4.0-4 @ii mK >**
**  Considering libsensors4:amd64 10 as a solution to libsensors-config:amd64 0**
**  Holding Back libsensors-config:amd64 rather than change libsensors4:amd64**

When I used dpkg to investigate libsensors4, it confirms the version:
[B]$ dpkg -p libsensors4
Package: libsensors4
Priority: optional
Section: libs
Installed-Size: 142
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: same
Source: lm-sensors
Version: 1:3.3.4-2ubuntu1
.
.

[/B]However when i try apt-get install to check the package installation, the following occurs:
**$ sudo apt-get install libsensors4**
**[sudo] password for garrone: **
**Reading package lists... Done**
**Building dependency tree       **
**Reading state information... Done**
**libsensors4 is already the newest version (1:3.4.0-4).**
**0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.**

So apt is reporting libsensors4 as 1:3.4.0-4, and dpkg is reporting it as 1.:3.3.4-2, which is breaking the upgrade.
Any explanation/remedy appreciated.

---

### Post by dino99 on 2020-12-31
1) check /etc/apt/sources.list for possible mixed releases entrie(s)
2) purge /var/cache/apt/archives/
3) update again

---

### Post by peterg17 on 2020-12-31
Thanks Dino99. Unfortunately your suggestion was unproductive. The sources.list looked entirely reasonable. I removed all files within /var/cache/apt/archives. I ran the software update tool for absolutely the same result. Here is my sources.list sans comments etc.
```

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic-updates universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic-security main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic-security main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic-security universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic-security universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic-security multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic-security multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
```

---

### Post by dino99 on 2020-12-31
maybe the 'au' archive is actually down; try the main one (without 'au') and you can remove all the deb-src entries if you never compile softs

note that bionic is near end of life in a few months ahead  [https://help.ubuntu.com/community/EOL](https://help.ubuntu.com/community/EOL)  so why not moving to a more recent LTS release ?

Myself i use 'synaptic' to get an easier experience to resolve such broken download, rather than the obscure sofware-updater.

---

### Post by rsteinmetz70112 on 2020-12-31
What happens with 

```
sudo dpkg --configure -a
```

and

```
sudo apt install -f
```

---

### Post by peterg17 on 2020-12-31
In response to the query as to why I am not moving to a more recent LTS release, I am attempting to upgrade to 20.04.
I tried changing to the US master, but no difference.
Usually I update from the command line, apt-get upgrade and apt-get dist-upgrade. These report my system is fully up to date. Only the software updater is attempting to change to 20.04.
I had tried reconfiguring particular packages, no difference. Running dpkg --configure -a and apt install -f did nothing.

The particular problem I have been trying to identify is why dpkg and apt report different versions of an installed package.
 The installed version, from inspection of /usr/share/doc/libsensors4, is 1:3.4.0, while the version reported by dpkg -p is 1:3.3.4. 
This old version is being used by the software updater, and as it is so old, causes dependent packages to fail. However the installed version is in fact adequate.

So apt and dpkg are using different archives. I am hunting for where the old version is stored, using grep and strace. The new version is in /var/lib/dpkg/status. Doing something else today. Happy new year.

---

### Post by peterg17 on 2020-12-31
Raining, so back onto this.

dpkg uses the file **/var/lib/dpkg/available**. This file references the old version of libsensors4. This file has not been updated on the system since  2016. It contains the version reported by dpkg -p.

I have managed to get an strace of the software updater. The command to do this is:

 $ **sudo strace -e file -f -o xxx.tr /usr/bin/python3 /usr/bin/update-manager**

This is a python program, and it makes 168 calls to dpkg and 157 calls to apt.

Due to the reporting error by dpkg, strongly suspect that dpkg is causing the issue, particularly because its data file has not been updated correctly.
 To fix the system, probably have to get a version of dpkg that works, and install it in /usr/local, as update-manager searches there first.

---

### Post by peterg17 on 2021-01-01
No the update manager does not appear to access the /var/lib/dpkg/available file. It is just sitting there unmodified and unused, unless one runs dpkg -p, in which case it shows the wrong version information.

So now I am stuck on this line in apt.log
**Broken libsensors-config:amd64 Conflicts on libsensors4:amd64 < 1:3.4.0-4 @ii mK >**

What it means exactly I cannot say. The actual currently installed version is 1:3.4.0-4. Does it require an earlier version? Who can say, I certainly cannot, all I know is it is conflicted about libsensors version somehow.
Looking at libsensors-config online, from *[https://packages.ubuntu.com/focal/libsensors-config](https://packages.ubuntu.com/focal/libsensors-config)*, it has no dependencies, only suggests lm-sensors, which is apparently its source as well. So dead end here.

---

### Post by dino99 on 2021-01-02
i suppose you have installed non genuine package/app from ppa/... that still need to use the old libsensors4. So be sure to deactivate/purge this(these) app(s) and downgrade their dependencies if needed; then run autoremove and update again.

[https://launchpad.net/ubuntu/+source/lm-sensors](https://launchpad.net/ubuntu/+source/lm-sensors)

---

### Post by peterg17 on 2021-01-03
I assume that the unmaintained file /var/lib/dpkg/available is not causing the problem because it is not accessed during the upgrade attempt, although it will provide incorrect information if dpkg -p is run.
I used "$ **aptitude search '~o'**" to discover orphan packages. I have 318 of these installed.
Many of these have dependencies not met by the new distribution.
I assume that these 318 installed packages, some dating back to early 2000's, are causing some upgrade problems.
I think I will have to check these orphans individually and work out if I need them or not, possibly come up with a more effective maintenance procedure to avoid crud accruing in my system, to avoid this problem with future upgrades.

---

### Post by peterg17 on 2021-01-04
I gave up somewhat with my aptitude search. Instead I grepped all the broken packages in apt.log, did an "apt show" on them, and started removing all the manually installed ones that didn't seem really important. I think I should have restricted myself to packages not present in the manifest of the version to which I was upgrading. After removing a dozen or so, **the upgrade worked**. I think some old graphics packages did the trick, cinelerra and inkscape. I kept a record of the ones I removed in case they did something vital, so I can reinstall them later.

---

