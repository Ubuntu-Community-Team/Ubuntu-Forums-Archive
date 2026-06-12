---
title: "not getting upgrades to dbgsym"
date: 2021-04-01
forum: Installation &amp; Upgrades
---

### Post by dvcroft on 2021-04-01
[COLOR=#000000][FONT=serif]I'm trying to install debug symbol packages for kwin on to a ku[/FONT][/COLOR]buntu 20.04.2 system.[COLOR=#000000][FONT=serif]
 [/FONT][/COLOR]
[COLOR=#000000][FONT=serif]I get the following error[/FONT][/COLOR]
[COLOR=#000000][FONT=serif][FONT=monospace]# apt install kwin-common-dbgsym
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
kwin-common-dbgsym : Depends: kwin-common (= 4:5.18.4.1-0ubuntu2) but 4:5.18.5-0ubuntu0.1 is to be installed
[COLOR=#FF5454]**E: **[/COLOR]Unable to correct problems, you have held broken packages.
[/FONT][/FONT][/COLOR]

[COLOR=#000000][FONT=serif]When I do apt show for it, I can see it is not being installed from focal-updates[/FONT][/COLOR]
[COLOR=#000000][FONT=serif][FONT=monospace]APT-Sources: [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) focal/universe amd64 Packages

[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=serif]But I have the following repositories included:[/FONT][/COLOR]
[COLOR=#000000][FONT=serif][FONT=monospace]deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) focal main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) focal-updates main restricted universe multiverse
[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=serif]
Are the 4:5.18.4.1-0ubuntu2 versions missing, or do I not have something set up correctly to get the updated versions?


[/FONT][/COLOR]

---

