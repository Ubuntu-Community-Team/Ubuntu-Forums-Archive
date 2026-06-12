---
title: "Installing from backup of local repository"
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by cmil87 on 2012-01-14
currently I have two linux machines, and only one is allowed (due to local network policy) to access the internet to pull updates. I've read through manual pages on apt-get and adding repositories and cant figure this out.

What i am trying to do, is take the packages from this machine (the linux machine that is allowed to access the internet) from /var/apt/cache copy them to a usb external drive, take the external hdd and then mount it on the other ubuntu machine, add the folder as a repository and using the option to filter packages by source, install every package from the external hdd to the offline ubuntu machine.

when i try to add the folder into the sources.list file this is what i am entering:

deb file:/media/external/ubuntu-apt-cache ./

im not getting any errors when i reload synaptic, but the source isnt showing up in synaptic either. I've created a package list via the dpkg-scanpackages command, and confirmed that synaptic is seeing it.

any help would be greatly appreciated, and thank you in advance!
:)

---

### Post by jerrrys on 2012-01-16
Have a look at this

[http://rxezlqu.wordpress.com/2010/02/15/updating-ubuntu-on-slow-connectionsoffline/](http://rxezlqu.wordpress.com/2010/02/15/updating-ubuntu-on-slow-connectionsoffline/)

Synaptic Package Manager is a very handy tool for this and other things.  It can be installed through the software center or in terminal (sudo apt-get install synaptic).

Also here are some other links.

[https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

---

