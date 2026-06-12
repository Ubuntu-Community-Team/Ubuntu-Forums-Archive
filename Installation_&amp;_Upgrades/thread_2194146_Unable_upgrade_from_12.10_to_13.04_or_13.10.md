---
title: "Unable upgrade from 12.10 to 13.04 or 13.10"
date: 2013-12-16
forum: Installation &amp; Upgrades
---

### Post by sheenzhaox on 2013-12-16
I have been using Ubuntu 12.04 LTS for quite a while. Yesterday, I decided to move to 13.10. 

First, I use ```
sudo do-release-upgrade
``` to upgrade from 12.04 to 12.10.
Everything was fine, successfully reboot in 12.10.

After all necessary upgrade in 12.10, I tried to upgrade to next version in 12.10.
I tried same thing by using ```
sudo do-release-upgrade
```, however I've got the following error message

```

sudo do-release-upgrade 
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                           
Get:2 Upgrade tool [1,135 kB]                                                  
Fetched 1,135 kB in 0s (0 B/s)                                                 
authenticate 'saucy.tar.gz' against 'saucy.tar.gz.gpg' 
extracting 'saucy.tar.gz'


Reading cache


Checking package manager


Cannot upgrade 


An upgrade from 'quantal' to 'saucy' is not supported with this tool. 

```

I also tried on GUI ```
sudo upgrade-manager -d
```, and I got the similar error message.

Can anyone help me solve the problem? Thanks.

---

### Post by michael.thomas on 2013-12-22
Hi,

I've exactly the same problem. It seems that the update manager is skipping the necessary 13.04 upgrade.

I will try to upgrade with the ISO Image of 13.04. Perhaps this will work.

Best
Mic

---

### Post by grahammechanical on 2013-12-22
If I remember correctly, Saucy Salamander was the code name for Ubuntu 13.10. At the moment I am using Trusty Tahr (14.04). So, I think that the issue here is that for some reason the upgrade process has tried to upgrade from 12.10 to 13.10, which it cannot do. Just a hint in a possible direction is the best that I can give.

Have you tried going into System Settings>Software Sources>Updates and making sure that Update Manager is set to notify you of any new version of Ubuntu? It might still be set for LTS versions.

I ask because Update Manager should notify us that there is a newer version and all we need to do is click a button. Please note that from 13.04 onwards the name Software Sources has changed to Software and Updates. Are you sure that 12.10 is fully updated? You may need a new update manager core package. Try

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

That last command does not upgrade to the next version of Ubuntu. It upgrades the existing version in using smart conflict resolution. You might also want to do

```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```

do-release-upgrade is meant for server systems. I would suggest that for desktop systems using Update Manager to notify us of the next version available is the better course. It takes the geekiness out of using Ubuntu.





Regards.

---

