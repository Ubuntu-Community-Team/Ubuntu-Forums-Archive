---
title: "Can't install Apps"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2011-10-14
kakashi12@Sentia:~$ sudo aptitude install startupmanager
[sudo] password for kakashi12: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "startupmanager"
Couldn't find any package whose name or description matched "startupmanager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

kakashi12@Sentia:~$ sudo apt-get install kdegames
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdegames: Depends: atlantik (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kasteroids (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: katomic (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kbackgammon (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kbattleship (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kblackbox (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kbounce (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kenolaba (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kfouleggs (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kgoldrunner (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kjumpingcube (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: klickety (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: klines (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kmahjongg (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kmines (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: knetwalk (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kolf (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: konquest (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kpat (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kpoker (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kreversi (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: ksame (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kshisen (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: ksirtet (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: ksmiletris (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: ksnake (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: ksokoban (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kspaceduel (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: ktron (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: ktuberling (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: kwin4 (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
            Depends: lskat (>= 4:3.5.6-0ubuntu2) but it is not going to be installed
E: Broken packages
kakashi12@Sentia:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: libwxgtk2.6-0 (>= 2.6.3.2.1.5ubuntu6) but it is not going to be installed
E: Broken packages
kakashi12@Sentia:~$ sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: libwxgtk2.6-0 (>= 2.6.3.2.1.5ubuntu6) but it is not going to be installed
E: Broken packages
kakashi12@Sentia:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libldap2 (>= 2.1.17-1) but it is not going to be installed
E: Broken packages
kakashi12@Sentia:~$

---

### Post by oldos2er on 2011-10-15
Which version of Ubuntu are you using? Have you run ```
sudo apt-get update
sudo apt-get install -f
``` ?

---

### Post by kakashi_12 on 2011-10-15
8

---

