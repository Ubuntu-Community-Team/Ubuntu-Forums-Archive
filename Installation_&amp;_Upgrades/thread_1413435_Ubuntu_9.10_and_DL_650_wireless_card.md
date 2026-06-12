---
title: "Ubuntu 9.10 and DL 650 wireless card"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by dlines on 2010-02-22
I am trying to install Ubuntu 9.10 on an older IBM laptop from a LiveCD. (Windows stopped working and I thought this would be a great time to try Linux!) When I boot up Ubuntu (which takes forever) it starts up, but I don't think it is recognizing the wireless card (DL 650). One suggestion I got from the net was to disable the acx module by blacklisting it with the statement:
 
blacklist acx
 
in the blacklist.conf file.
 
The next step is to install ndiswrapper with:
 
sudo apt-get install ndiswrapper-common
 
The last step is to get the Windows driver (I have it) and put it in a directory. Then go to that directory and type:
 
sudo ndiswrapper -i AIRPLUS.INF
 
This is all well and good, but where do I do these things to test to see if it works and ultimately, if it works, to set it up this way permanently? How do I edit blacklist.conf if this is a LiveCD and as soon as I turn off the machine everything goes away? I am not sure that I can install on the hard disk at this point because I don't want to wipe out Windows yet (it isn't my computer). I would like to prove Ubuntu (or maybe Xubuntu) before committing to it. I am also not sure that the single USB port will allow me to install a USB stick version of Ubuntu. Any help or direction would be appreciated. Thanks.

---

