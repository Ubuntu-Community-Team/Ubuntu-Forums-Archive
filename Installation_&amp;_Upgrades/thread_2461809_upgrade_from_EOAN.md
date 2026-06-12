---
title: "upgrade from EOAN"
date: 2021-05-07
forum: Installation &amp; Upgrades
---

### Post by drumanart on 2021-05-07
Hello 
I missed the train to upgrade my eoan. Now the files have been moved to old-releases this is why I'm trying to upgrade to foscal manually.

So I edited the /etc/apt/sources.list and changed all eoan to foscal 

Disabling the main repo qith synaptic I can do  the apt-get upgrade command but still eoan persists.

lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 19.10
Release:	19.10
Codename:	eoan

Is there a way or do I have to install everything from scrarch
Thanks Martin

---

### Post by ajgreeny on 2021-05-07
I hope that when you edited the sources.list file you did not edit **eoan** to **foscal**.

If you did so that may explain why you are having the problem, as it should be **focal** not **foscal**.

However, was your eoan fully up to date, or were packages from eoan already outdated before you attempted the manual upgrade process?

---

### Post by drumanart on 2021-05-07
Of course I put **focal **to the sources list.
I'm not entirely sure weather my **eoan **was fully updated.
In any case in changing the sources list to** focal **made the system download a lot of files, all worked well.

---

### Post by ajgreeny on 2021-05-08
In your updated version run command ```
sudo apt update && sudo apt full-upgrade
``` and if there are no problems with that I think you can assume that all is well and just continue using the system.

Depending on the name you chose for your system's hostname when you installed it, ie, if you called it **Ubuntu-eoan** or another name using eoan, you may wish to edit the two files ***/etc/hosts*** and ***/etc/hostname*** to give your upgraded version another more appropriate hostname.

---

### Post by grahammechanical on 2021-05-08
Changing the addresses of the repositories in sources.list and then running update/upgrade commands will bring in upgraded packages from the newer Ubuntu release but I do not think it will upgrade to the newer release. The better method is offered in the Ubuntu 20.04 release notes.

[https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes)

> To upgrade on a desktop system: 

[LIST]
[*]Open the "Software & Updates" Setting in System Settings. 


[*]Select the 3rd Tab called "Updates". 
[*]Set  the "Notify me of a new Ubuntu version" drop down menu to "For any new  version" if you are using 19.10; set it to "For long-term support  versions" if you are using 18.04 LTS. 
[*]Press Alt+F2 and type update-manager -c into the command box if you are using 19.10; type update-manager -c -d if you are using 18.04 LTS. 


[*]Update Manager should open up and tell you that Ubuntu 20.04 LTS is now available. 
[*]Click Upgrade and follow the on-screen instructions.
[/LIST]

Try following those instructions and see if the /etc/lsb-release text document gets upgraded to this

> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04.2 LTS"

lsb-release is a text file that has not been upgraded because the correct method for upgrading from one release to the next was not followed. There may be other parts of the Ubuntu 19.10 that did not get upgraded as well.

Some users may offer the upgrade method for server systems. This is it.

> To upgrade on a server system: 

[LIST]
[*]Install  update-manager-core if it is not already installed. 


[*]Make sure the Prompt line in /etc/update-manager/release-upgrades is set to 'normal' if you are using 19.10, or 'lts' if you are using 18.04 LTS. 


[*]Launch the upgrade tool with the command sudo do-release-upgrade on 19.10; use sudo do-release-upgrade -d if you are using 18.04 LTS.

The release notes say this about the do-release-upgrade -d command. 

> The -d switch is necessary to upgrade from  Ubuntu 18.04 LTS as upgrades have not yet been enabled and will only be  enabled after the first point release of 20.04 LTS.

Ubuntu 20.04 is now at the second point release so the -d switch should not be needed.

[/LIST]

Regards

---

### Post by ajgreeny on 2021-05-08
> **grahammechanical said:**
> Changing the addresses of the repositories in sources.list and then running update/upgrade commands will bring in upgraded packages from the newer Ubuntu release but I do not think it will upgrade to the newer release. The better method is offered in the Ubuntu 20.04 release notes.

[https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes)
I wondered about that but a day or two ago I upgraded a virtual installation in KVM of hirsute to impish, 21.04 to 21.10, by manually editing the sources.list file as there is at present no upgrade path, 21.10 repos having only been available for a few days.

The ***/etc/lsb_release*** file has been updated and now shows as I would have expected from a clean install of impish.
However, I accept that there may be other parts of the OS that will not change when a system is upgraded in this way, though I admit that I don't have any details of this, nor which files that may be.

---

### Post by guiverc on 2021-05-08
Documentation on EOL Upgrades exists

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

It tells you how to deal with the move from archives to old-releases, so you can ensure your system is fully upgraded, then perform upgrade.

Upgrades like Debian can work, but can also fall over & fail to complete/boot; `do-release-upgrade` does a few upgrades in specific order, stops screensaver etc that ensures the upgrade process will not encounter any problems (particularly with python etc)

---

### Post by drumanart on 2021-05-11
Thanks a lot for all the help, finally I made a fresh install.
Martin

---

