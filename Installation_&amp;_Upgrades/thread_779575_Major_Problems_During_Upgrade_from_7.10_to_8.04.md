---
title: "Major Problems During Upgrade from 7.10 to 8.04"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by tallkid on 2008-05-02
About a week ago I tried to upgrade via the "update manager" and the "upgrade" button at the top.  It went through some preliminary actions and got to the point of downloading the necessary packages.  This was in the evening and since I thought it might take a while I left my terminal.  When I came back in the morning my machine was off, I went to boot I got a graphics error before having the ability to login.  Said I needed to configure my graphics or run in low-graphics mode.  I configured the graphics, and continued, only to find that the login window being displayed was about 4 times the size of my monitor.  Tried logging in, got a brown screen with nothing else.  Let it sit for hours, nothing changed.  

I rebooted in recovery mode, tried 'apt-get upgrade' got an error that I needed to 'apt-get -f install'.  Tried this, a few times, but got errors that my dpkg available file was corrupt.  Renamed the available file to some temp name and then renamed available-old to available.  Re ran 'apt-get -f install', appeared to work on some things.  

I don't completely remember the order of events, but I had to 'dpkg --configure -a' which failed because some packages depended on others that were not installed.  The last step I did was create the directory '/var/run/dbus' because I kept getting an error that it did not exist. This allowed 'dpkg --configure -a' to successfully run.  Then ran 'apt-get -f install', this worked as well.  Then tried 'apt-get upgrade' and it told me:  
0 upgraded, 0 newly installed, 0 to remove and 164 not upgraded.

I rebooted (my boot selection still stated it was 7.10), had to configure the graphics again, and then reached a blue login screen with a flower.  I am assuming this is part of 8.04 because I never saw that in 7.10.  Login is fine, but it now appears I have some hybrid of 7.10 and 8.04.  It still looks like 7.10 but when I try to use the update manager I get the following messages:
Not all updates can be installed
Run a partial upgrade, to install as many updates as possible.
blah blah blah

I click 'Partial Upgrade' and get the following:
Can not upgrade
A upgrade from 'hardy' to 'gutsy' is not supoprted with this tool.

That is not a misspelling on my part above, that is what appears.
So I really do not know what to do.

I do not want to wipe the slate clean and reinstall 8.04 for a number of reasons.  I would love to fix this issue and finish the upgrade to 8.04 if someone can help me.  I don't know what information you need to know to help, just let me know and I will provide it. 

Thanks,
tk

---

### Post by empthollow on 2008-05-02
try running:
```

sudo apt-get dist-upgrade
```
from a terminal, if it doesn't work from a terminal i would try it from recovery mode.  If update manager won't let you upgrade "from hardy to gutsy":lolflag: perhaps apt-get will take care of it.  Good luck.  By the way, i like to do a fresh install every couple releases but i do upgrades to my systems as well.  I too usually have some issues right afterward but I can usually have them fixed in an hour.  The problems generally appear bigger than they are in my experience.

---

### Post by lemming465 on 2008-05-02
At a guess, /etc/apt/sources.list is still full of gutsy repositories rather than hardy.  What you want is something like:```
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```
Also, it's recommended to upgrades with ```
sudo update-manager --dist-upgrade
```
as this will do a better job on Ubuntu than the more traditional Debian-style *apt-get* ploy.

---

### Post by tallkid on 2008-05-03
Thanks for the replys.  I did end up trying 
```
sudo apt-get dist-upgrade
```
And it fixed a number of problems.  But now I get the following:
E: Problem parsing dependency Depends
E: Error occurred while processing mencoder (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

When I start the package manager.  So I tried 
```
sudo update-manager --dist-upgrade
```
And I get the following errors:
Traceback (most recent call last):

  File "/usr/bin/update-manager", line 92, in <module>
    if not controler.doPreUpgrade():

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeController.py", line 612, in doPreUpgrade
    if len(self.cache.reqReinstallPkgs) > 0:

AttributeError: 'NoneType' object has no attribute 'reqReinstallPkgs'

And it told me to include the following file:
 /var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log


At this point I am up and running but I can't add, remove or update any packages, which sucks.  Any thoughts?

---

### Post by empthollow on 2008-05-03
sounds like there are some broken packages, try
```
sudo apt-get -f install
``` or open synaptic and find 'fix broken' in the menus.  if that doesn't work you cant try this to reconfigure all the packages on your system.  
[CODE]sudo dpkg --configure -a[CODE]

---

### Post by tallkid on 2008-05-03
```
sudo apt-get -f install
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing mencoder (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

```
sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 20544 package `mencoder':
 error in Version string `2:1.0~rc2-0ubuntu13': epoch in version is not number

```

This makes me think my status file is corrupt, or somehow got overwritten with garbage.

I replaced /var/lib/dpkg/status with status-old, then...
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libfaad2-0 liblzo1 libx264-54 python-qt3 python-sip4 libiso9660-4 libungif4g
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-2.6.24-16-generic
The following NEW packages will be installed:
  linux-headers-2.6.24-16-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/642kB of archives.
After this operation, 7418kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 126793 files and directories currently installed.)
Unpacking linux-headers-2.6.24-16-generic (from .../linux-headers-2.6.24-16-generic_2.6.24-16.30_i386.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.24-16-generic_2.6.24-16.30_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/src/linux-headers-2.6.24-16-generic/include/linux/autoconf.h')
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.24-16-generic_2.6.24-16.30_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

and

```
sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.24-16-generic; however:
  Package linux-headers-2.6.24-16-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-generic

```

Any thoughts?

Thanks,
tk

---

### Post by lemming465 on 2008-05-04
At this point we're beyond what I know about fixing dpkg|apt problems.

Is there anything helpful in:> /var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log


---

### Post by tallkid on 2008-05-04
I am not completely sure of the order of events that finally fixed my install, but I do know what I did last.

```
sudo dpkg -r linux-headers-generic
```

Followed by

```
sudo aptitude upgrade
```

I got a message saying that 'aptitude upgrade' was depecrated and I should use 'aptitude safe-upgrade' instead, but I went forth anyway and now all is well.  I have no errors with dpkg, apt-get, update-manager, etc.  I can update, add, remove packages at will.

Thanks for all the help along the way,
tk

---

