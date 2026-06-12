---
title: "UbuntuStudio hoses up VirtualBox install"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by HW_Hack on 2008-04-13
This has happened twice - so there is obviously an issue or something simple I'm not doing --

clean 7.10 install - do all the upgrades -- install the VirtualBox SW and do the entire load of XP - everything works fine -- I then do 
[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy)

And VirtualBox stops working --- something about driver missing ????

Anyone been here before ?

Maybe I need to :
1- Install 7.10  etc ...
2. Do the Studio upgrade 
3. then do the Virtualbox ... ?

Confused

---

### Post by Existentialist on 2008-04-13
It sounds like you are missing the kernel module for the new kernel you are installing as part of Ubuntu Studio.  You could try looking if they are in the repos, they should look something like:

virtualbox-ose-modules-2.6.22-16-generic

But the last portion would be the kernel you are using (found with 'uname -r').  I'm not sure if they have them for the Ubuntu Studio kernel, you may have to follow this guide to install them manually:

[http://phorolinux.com/installing-virtualbox-ose-on-ubuntu-710-gutsy-gibbon.html](http://phorolinux.com/installing-virtualbox-ose-on-ubuntu-710-gutsy-gibbon.html)

---

