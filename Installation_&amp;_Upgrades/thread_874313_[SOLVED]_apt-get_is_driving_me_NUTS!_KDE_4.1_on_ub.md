---
title: "[SOLVED] apt-get is driving me NUTS! KDE 4.1 on ubuntu"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by markg85 on 2008-07-29
Hi,

I did **exactly** what is written here:
[http://www.kubuntu.org/news/kde-4.1](http://www.kubuntu.org/news/kde-4.1)

Now with the installation it fails here:
> 
root@mark-laptop:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kde-window-manager
The following NEW packages will be installed:
  kde-window-manager
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0B/1516kB of archives.
After this operation, 5005kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  kde-window-manager
Install these packages without verification [y/N]? y
(Reading database ... 152142 files and directories currently installed.)
Unpacking kde-window-manager (from .../kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/doc/kde4/HTML/en/kcontrol/kwindecoration/index.cache.bz2', which is also in package kdebase-runtime-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@mark-laptop:~# 


and now when i run the install line again i get this:

> 
root@mark-laptop:~# apt-get install kubuntu-kde4-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kubuntu-kde4-desktop is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kubuntu-kde4-desktop: Depends: kde-window-manager but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@mark-laptop:~# 


And when i do apt-get -f install i get the first quote... AARGH driving me nuts!@#!@#!@#!@

Isn't there a FORCE option to get this installed?
And why is apt-get so darn annoying when it comes to errors.. no clear solutions are given..

O and if i install the kde4-window-manager manually i get this :evil::evil::evil:
> 
root@mark-laptop:~# apt-get install kde-window-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  kde-window-manager
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0B/1516kB of archives.
After this operation, 5005kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  kde-window-manager
Install these packages without verification [y/N]? y
(Reading database ... 152142 files and directories currently installed.)
Unpacking kde-window-manager (from .../kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/doc/kde4/HTML/en/kcontrol/kwindecoration/index.cache.bz2', which is also in package kdebase-runtime-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@mark-laptop:~# 


In yum you simply have a ignore option.. but how to get this kde 4.1 working on ubuntu... and more importantly.. **how** do i get rid of those darn errors.. It happened to me before with MySQL and back then (few months ago) noboddy could help me with it so i had to **reinstall**!! and i'm far from a linux n00b. Work with it every day. make programs on it, make websites on it (php)..

Edit::

I don't have any other third party repository's installed other then the one kubuntu (in de kde 4.1 news) pointed me to and the wine repository. So nothing is wrong there.

---

### Post by t.rei on 2008-07-30
Same error - still looking.

Seems like some pooish redundancy of kde-window-manager and kdebase-runtime-data

[I]"trying to overwrite `/usr/lib/kde4/share/doc/kde4/HTML/en/kcontrol/kwindecoration/index.cache.bz2', which is also in package kdebase-runtime-data"

[/I]Just stay patient, usually these problems get resolved very quickly. (If I should find something I'll post)

*edit (solved)*

Ok, you might want to try this:

+ add the repos to your sources.list
+ update via the update manager
+ install kubuntu-kde4-desktop

worked for me this way.

---

### Post by markg85 on 2008-07-30
> **t.rei said:**
> Same error - still looking.

Seems like some pooish redundancy of kde-window-manager and kdebase-runtime-data

[I]"trying to overwrite `/usr/lib/kde4/share/doc/kde4/HTML/en/kcontrol/kwindecoration/index.cache.bz2', which is also in package kdebase-runtime-data"

[/I]Just stay patient, usually these problems get resolved very quickly. (If I should find something I'll post)

*edit (solved)*

Ok, you might want to try this:

+ add the repos to your sources.list
+ update via the update manager
+ install kubuntu-kde4-desktop

worked for me this way.

Confirmed.
worked for me as well.
thanx for telling me.

---

