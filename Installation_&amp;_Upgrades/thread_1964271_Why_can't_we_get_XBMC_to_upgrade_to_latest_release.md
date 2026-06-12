---
title: "Why can't we get XBMC to upgrade to latest release version?"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by Bullwinkle_Moose on 2012-04-23
We tried asking this in the XBMC forum and got no responses, but it might be more appropriate in this forum anyway.  For some reason we're unable to upgrade XBMC on a system running Ubuntu Natty to the current release version (XBMC Eden). When we first built the system, Natty had just come out (might even have still been in beta) and there were no official versions of XBMC available that would work on Natty (pre-release or otherwise), however, someone pointed us to an unofficial repository at [https://launchpad.net/~easy-vdr4you/+archive/stable-vdr-natty](https://launchpad.net/~easy-vdr4you/+archive/stable-vdr-natty) that offered an early pre-release version of Eden, and we installed from there, because at the time it was the only version we could get to work.

Flash forward to today, and the problem is that even though we have disabled that repository in Synaptic, and added the official team-xbmc repository, Synaptic insists that the pre-release version we already have is the latest version of XBMC available, and will not even offer the final release version. We can't figure out what we're doing wrong.

One thing we very much do NOT want to to have happen is that we lose our current XBMC settings, so for that reason we're very reluctant to simply remove the current pre-release version of XBMC using Synaptic.  Besides, even if we did that, we're not entirely convinced that it wouldn't continue to find the other version from the VDR4YOU site, because it seems to still be saying the latest version is the same as the installed version, even though we've disabled those repos!

Even when we tried to force it to use the team-xbmc repository (which is where the current release version is located) using apt-get it doesn't work:

[B]~$ sudo apt-get install -t team-xbmc xbmc
Reading package lists... Done
Building dependency tree
Reading state information... Done
xbmc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
[/B]
All we want to know is, how can we force it to upgrade XBMC from the official team-xbmc site, WITHOUT first removing the current pre-release beta version and risking the loss of all our settings?  The weird part is we don't even see the new release version of XBMC in Synaptic, and we don't know why.

---

### Post by papibe on 2012-04-23
Hi Bullwinkle_Moose.

All database and personal settings are store in your home directory under this directory:
```
~/.xbmc
```
I have installed, uninstalled and installed again, and I always keep my settings. As a precaution you may backup the directory:
```
cp -rp  ~/.xbmc  ~/.xbmc.backup
```

Let's check what version you have installed and from what repository. Could you post the result of this command?
```
apt-cache policy xbmc
```
Regards.

---

### Post by jawilljr on 2012-04-23
Below is tha latest version for Oneiric:

```
2:11.0~git20120321.14feb09-0ubuntu1~ppa1~oneiric
```

Change Oneiric to Natty or Maverick or whatever.

[Source.](https://launchpad.net/~team-xbmc/+archive/ppa)

Jerry

---

### Post by Bullwinkle_Moose on 2012-04-24
> **papibe said:**
> Hi Bullwinkle_Moose.

All database and personal settings are store in your home directory under this directory:
```
~/.xbmc
```
I have installed, uninstalled and installed again, and I always keep my settings. As a precaution you may backup the directory:
```
cp -rp  ~/.xbmc  ~/.xbmc.backup
```

Let's check what version you have installed and from what repository. Could you post the result of this command?
```
apt-cache policy xbmc
```
Regards.

Thanks for this information.  Here's the result:

[B]~$ apt-cache policy xbmc
xbmc:
  Installed: 2:11.0-pvr+odk28~git20110419.3513480-1vdr4you0
  Candidate: 2:11.0-pvr+odk28~git20110419.3513480-1vdr4you0
  Version table:
 *** 2:11.0-pvr+odk28~git20110419.3513480-1vdr4you0 0
        100 /var/lib/dpkg/status
     2:11.0~git20120321.14feb09-0ubuntu1~ppa1~natty 0
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) natty/main i386 Packages[/B]

Note the installed and candidate versions are the same and both end in -1vdr4you0.  But the one we want to install would be the one from the team-xbmc repository, and I don't understand why it won't use that one for the upgrade.

---

### Post by Bullwinkle_Moose on 2012-04-24
> **jawilljr said:**
> Below is tha latest version for Oneiric:

```
2:11.0~git20120321.14feb09-0ubuntu1~ppa1~oneiric
```

Change Oneiric to Natty or Maverick or whatever.

[Source.](https://launchpad.net/~team-xbmc/+archive/ppa)

Jerry

Yep, that's exactly the repository we added using the instructions on that page (using the one for Natty, of course), but for some reason Synaptic totally ignores it (even though it shows the repository in the repositories list, and it appears to be enabled).

---

### Post by papibe on 2012-04-24
I haven't faced a situation like this, so I can only offer you my advice on what I would do in such a dilemma. 

First I would backup my xbmc directory (just in case):
```
cp -rp  ~/.xbmc  ~/.xbmc.backup
```
Then I see 2 alternatives:

1. Remove the package, and reinstall. This should work:
```
sudo apt-get remove xbmc

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install xbmc
```

2. Use ppa-purge (I have not test this myself):
```
sudo apt-get install ppa-purge

ppa-purge ppa:easy-vdr4you/stable-vdr-natty

sudo apt-get update
sudo apt-get upgrade
```
ppa-purge is kind of a new package. This are references to it: [this]("http://askubuntu.com/questions/109231/installing-the-normal-kubuntu-desktop-after-removing-the-version-from-ppa"), and [this]("http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/").

I hope that helps, and tell us how it goes.
Regards.

---

### Post by Bullwinkle_Moose on 2012-04-24
Thanks, papibe.  Just wanted to note that ppa-purge didn't work… it appeared to install okay although it gave a lot of output:

[B]~$ sudo apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  aptitude libboost-iostreams1.42.0 libcwidget3
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
The following NEW packages will be installed:
  aptitude libboost-iostreams1.42.0 libcwidget3 ppa-purge
0 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 2,816 kB of archives.
After this operation, 8,630 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) natty/main libboost-iostreams1.42.0 i386 1.42.0-4ubuntu2 [55.5 kB]
Get:2 [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) natty/main libcwidget3 i386 0.5.16-3ubuntu2 [424 kB]
Get:3 [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) natty/main aptitude i386 0.6.3-3.2ubuntu1 [2,332 kB]
Get:4 [http://mirror.team-cymru.org/ubuntu/](http://mirror.team-cymru.org/ubuntu/) natty/universe ppa-purge all 0.2.8+bzr56 [4,360 B]
Fetched 2,816 kB in 0s (3,512 kB/s)   
Selecting previously deselected package libboost-iostreams1.42.0.
(Reading database ... 267712 files and directories currently installed.)
Unpacking libboost-iostreams1.42.0 (from .../libboost-iostreams1.42.0_1.42.0-4ubuntu2_i386.deb) ...
Selecting previously deselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3ubuntu2_i386.deb) ...
Selecting previously deselected package aptitude.
Unpacking aptitude (from .../aptitude_0.6.3-3.2ubuntu1_i386.deb) ...
Selecting previously deselected package ppa-purge.
Unpacking ppa-purge (from .../ppa-purge_0.2.8+bzr56_all.deb) ...
Processing triggers for man-db ...
Setting up libboost-iostreams1.42.0 (1.42.0-4ubuntu2) ...
Setting up libcwidget3 (0.5.16-3ubuntu2) ...
Setting up aptitude (0.6.3-3.2ubuntu1) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode.
Setting up ppa-purge (0.2.8+bzr56) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place[/B]

But then when I tried to run it using the syntax you gave, it warned me that "This script would need superuser privileges, use sudo", and when I did that...

[B]~$ sudo ppa-purge ppa:easy-vdr4you/stable-vdr-natty
Updating packages lists
PPA to be removed: easy-vdr4you stable-vdr-natty
Warning:  Could not find package list for PPA: easy-vdr4you stable-vdr-natty[/B]

I wonder if the fact that this repository is current disabled in Synaptic would affect the ability of ppa-purge to remove it?  Anyway, no luck there for now, and still a bit afraid to do the remove and reinstall at the moment.

---

### Post by papibe on 2012-04-24
It looks like the ppa has to be enabled so that ppa-purge can read the its packages.

Try this:
```
sudo add-apt-repository ppa:easy-vdr4you/stable-vdr-natty

sudo apt-get update
sudo apt-get upgrade

sudo ppa-purge ppa:easy-vdr4you/stable-vdr-natty

sudo apt-get update
sudo apt-get upgrade
```
Regards.

---

### Post by Bullwinkle_Moose on 2012-04-29
> **papibe said:**
> It looks like the ppa has to be enabled so that ppa-purge can read the its packages.

Try this:
```
sudo add-apt-repository ppa:easy-vdr4you/stable-vdr-natty

sudo apt-get update
sudo apt-get upgrade

sudo ppa-purge ppa:easy-vdr4you/stable-vdr-natty

sudo apt-get update
sudo apt-get upgrade
```
Regards.

Did that without realizing it was the wrong repository (not your fault, I gave the wrong link in the first message in the thread), and following those instructions installed and removed several things from that repository, including lirc, which later caused our remote to not function properly (uninstalling and reinstalling lirc from Synaptic fixed that, because it let us specify the correct remote).  When we substituted the correct repository THEN it worked. So what worked for us was to re-enable the repositories in synaptic, then...

sudo add-apt-repository ppa:easy-vdr4you/unstable-xbmc-natty
sudo apt-get update
sudo apt-get upgrade

sudo ppa-purge ppa:easy-vdr4you/unstable-xbmc-natty
sudo apt-get update
sudo apt-get upgrade

And then in /etc/apt/sources.list.d/ totally delete the files associated with the repository we didn't want to use.  XBMC apparently was upgraded when we did the ppa-purge but as I say, lirc got messed up when we ran your instructions so until we got that fixed we had a few minutes of panic!

So thanks for your help — your advice would likely have been right on had I given the correct link to the repository ([https://launchpad.net/~easy-vdr4you/+archive/unstable-xbmc-natty](https://launchpad.net/~easy-vdr4you/+archive/unstable-xbmc-natty)) in the first link in the thread, and anyway we figured it out.  Now of we could just get some resolution for [our other issue with accessing files on a FreeNAS server]("http://ubuntuforums.org/showthread.php?p=11887777"), things would be working perfectly!

---

