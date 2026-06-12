---
title: "Upgrade errors"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by Nettlerash on 2011-11-14
I have a server running 10.10 Maverick and I'm trying to upgrade it to Natty. I've followed the advice in the 'NattyUpgrades' pages, i.e. install update-manager-core and tried to upgrade using do-release-upgrade. This successfully works out which packages to download etc. but when I confirm that I wish to continue, I get multiple errors such as:

       Err [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) natty-updates/main .....
     Connection failed
  
I can connect to gb.archive.ubuntu.com and surely it must have connected here to work out what to download but it just fails when it actually tries to obtain each upgraded package.

The server is running behind a web proxy so I'm guessing that may be the cause of the problem. The proxy is using port 8090. I've not got access to this proxy and my network team have so far not been able to help!

So, my next thought was to use the CD upgrade. So I obtained the Alternate CD version as described in the NattyUpgrades page. I ran cdromupgrade and answered [n]o to using the Network to upgrade. This seemingly works out what to upgrade based on the CD's files. It then asks the same 'continue' question, to which I answered [y]es but then it tries to download the upgrade packages from the internet as before... and hence fails with the same error as above!

So, I have two questions: any idea what's causing the internet upgrade errors, and why doesn't the CD upgrade just use the CD?

Any help would be gratefully received.

---

### Post by Hakunka-Matata on 2011-11-14
Hi, Welcome:

I've seen so much on upgrade glitches to 11.10.  Have you tried this set of commands:
**Oneiric repos open!**             
                                                                The development cycle is uninterrupted!

     Code:
     ```
sudo sed -i 's/natty/oneiric/g' /etc/apt/sources.list 
sudo aptitude update 
sudo aptitude dist-upgrade 
```(You might want to save the natty-updates, natty-backports, natty-security, and natty-proposed repo lines in sources.list)

eric@kingfisher:~/Downloads$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"
                                                                                                                                     *                                               Last edited by Starks; April 28th,  2011 at 09:10 PM..                                                            *

---

### Post by Nettlerash on 2011-11-14
Thanks for the reply. This seems to have got me something which pretty closely resembles my other 11.10 servers but with a few broken bits and pieces here and there. I'll try running my applications on it and see how they cope. If not, it might be a completely new installation over the top.

---

### Post by Nettlerash on 2011-11-15
Whilst this originally looked like it might work, the resulting system was in a state of somewhat befuddled packages hence updates and package installation was failing. I have therefore given up and am currently trying to install Natty on top of the messed up system.

---

### Post by Hakunka-Matata on 2011-11-15
Good idea probably, you're going to overwrite/format the partition, is that right?

---

