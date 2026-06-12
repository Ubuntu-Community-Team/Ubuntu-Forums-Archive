---
title: "Xubuntu upgrade problem"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by Y^2om&amp;#7sgP on 2014-04-30
Hi all

I'm currently running Xubuntu 13.10 on my desktop PC.

I have tried for the past couple of days to run 

sudo apt-get update

sudo apt-get dist-upgrade

to upgrade to 14.04

but it advises that there are no upgrades to install.

It appears though that updates for 13.10 are being installed as I get a prompt each day (so far) to install them.

I've tried disabling extra ppa's, but don't know where to go from there.

Any ideas please?  I could (as a last resort) just install 14.04 from scratch, but would rather not if it can be helped.

Thanks for any suggestions

---

### Post by Bucky Ball on 2014-04-30
*Thread moved to **Installation & Upgrades**.*

'sudo apt-get dist-upgrade' will not upgrade your current installed release to the next. It will upgrade your current install. You're better to do a clean install to 14.04 LTS at this point.

You might also want to have a look here:

[http://www.itworld.com/open-source/414941/upgrade-ubuntu-1310-ubuntu-1404](http://www.itworld.com/open-source/414941/upgrade-ubuntu-1310-ubuntu-1404)

---

### Post by monkeybrain20122 on 2014-04-30
dist-upgrade is updating software, it has nothing to do with distro upgrade. 

Instead of "upgrade" just backup your data and do a clean install, "upgrade" is complex, fragile and not very reliable. Clean install takes 15 minutes and even if it takes you an hour to reinstall all the software (not likely) you are still ahead of "upgrade" which takes several hours during which many things can go wrong.

---

### Post by LastDino on 2014-04-30
Command to update versions is
> $ sudo do-release-upgrade

If there is still message saying no updates, then run
> sudo apt-get install update-manager-core
 

Force update
**[COLOR=#FF0000]Warning[/COLOR]**: The following method will check if upgrading to the latest devel (also known as unstable) release is possible via -d option.
To force upgrade pass the -d option to sudo do-release-upgrade command:


>  sudo do-release-upgrade -d

**A note about upgrading from Ubuntu 13.10 on a desktop system**

First,  you need to remove all 3rd party binary drivers such as NVIDIA or AMD  graphics card driver. Once removed and rebooted the desktop, press Alt+F2 and type in update-manager into the command box:
> update-manager
Update Manager should open up and tell you: New distribution release '14.04 LTS' is available. Just click **Upgrade** and follow the on-screen instructions to upgrade your desktop systems.

But it is advised to do fresh install, we have enough users with problems doing on line upgrade.

---

### Post by slickymaster on 2014-04-30
> **hattpa said:**
> Hi all

I'm currently running Xubuntu 13.10 on my desktop PC.

I have tried for the past couple of days to run 

sudo apt-get update

sudo apt-get dist-upgrade

to upgrade to 14.04

but it advises that there are no upgrades to install.

It appears though that updates for 13.10 are being installed as I get a prompt each day (so far) to install them.

I've tried disabling extra ppa's, but don't know where to go from there.

Any ideas please?  I could (as a last resort) just install 14.04 from scratch, but would rather not if it can be helped.

Thanks for any suggestions

_Here's what you have to do:_

[LIST=1]
[*]Backup all your data
[*]Open a terminal window and run the following command:```
sudo apt-get update && sudo apt-get upgrade
```
[*]After that done, run this:```
sudo do-release-upgrade
```When prompted, enter your user password. The Update Manager application will open after a few seconds with a prompt to upgrade. Click this button to begin the process.
[/LIST]

---

### Post by Y^2om&amp;#7sgP on 2014-04-30
Thanks for all the suggestions.

I think that on balance I'll backup and do a clean install at the weekend

Thanks again

---

