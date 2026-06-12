---
title: "Problems after an automatic update"
date: 2014-05-15
forum: Installation &amp; Upgrades
---

### Post by jamesr on 2014-05-15
Hi,

I am seeing an error on one of my archival servers, it is running lucid (10.04 LTS). Yes I know that I should upgrade!
In the notifaction bar at the top right I see a " no entry sign" and when I click on the symbol I see an error message. 

> Could not initialise the package information.

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid-updates_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I cannot update using apt-get nor use Synaptic. 

I am unsure on 2 points
a) where to report bug as mentioned in the error message
and 
b) possibly, more importantly, how to solve the problem. The server is working but I cannot update it. I do have backups of the system.

Any suggestions would be gratefully received.

Best Wishes
Jim R.

---

### Post by ibjsb4 on 2014-05-17
```
sudo apt-get clean
sudo mv /var/lib/apt/lists /var/lib/apt/lists.broke
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get update
```
more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened&as_qdr=all&sa=Google+Search&lang=en)

Edit: I should add that this fix works on supported versions.

---

