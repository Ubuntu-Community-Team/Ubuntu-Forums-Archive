---
title: "About upgrade to ubuntu 12.04 LTS"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by satimis on 2012-05-06
Hi all,

Ubuntu 11.04 desktop host (64bit)
Ubuntu 9.04 desktop VM (64bit)
Virtualizer	Oracle VirtualBox

I followed "Network Upgrade for Ubuntu Desktops 10.04 LTS to 12.04 LTS (Recommended)" on;
[https://help.ubuntu.com/community/PreciseUpgrades#Upgrade_from_11.10_to_12.04_LTS_and_10.04_LTS_to_12.04_LTS](https://help.ubuntu.com/community/PreciseUpgrades#Upgrade_from_11.10_to_12.04_LTS_and_10.04_LTS_to_12.04_LTS)

"update" and "install update" went through without problem.  After finish it needs to reboot the OS.  After reboot pressing "Check", "Upgrade" doesn't appear.

$ uname -a```

Linux ub1004dktop02 2.6.32-41-generic #88-Ubuntu SMP Thu Mar 29 13:10:32 UTC 2012 x86_64 GNU/Linux

```

$ uname -r```

2.6.32-41-generic

```

The kernel is NOT ubuntu 12.04 LTS.  Pls help.  TIA

B.R.
satimis

---

### Post by grahammechanical on 2012-05-06
I am confused. Do you have or did you have 10.04 installed? You say this

> Ubuntu 11.04 desktop host (64bit)
Ubuntu 9.04 desktop VM (64bit)
Virtualizer Oracle VirtualBox

So, why did you follow instructions that are specific to 10.04 or 11.10.

If you are upgrading 11.04 to 12.04 you have to first upgrade to 11.10 and then you upgrade 11.10 to 12.04. That is the recommended method.

It is possible to upgrade from one LTS release (10.04) to the next LTS release (12.04) and also to upgrade from the last release (11.10) to the next release (12.04) but we cannot jump from 11.04 to 12.04 or from 10.10 to 12.04.

You most probably have only upgraded to 11.10. Run this command

```
lsb_release -a
```

and see whether you have 11.10 or 12.04 or what?

Regards.

---

### Post by jadtech on 2012-05-06
2.6.32-41-generic according to all my search  is lucid version 10.04

and what the documentation says is to do all the updates the release update should show up when you are at 10.04.4

change your server in update manager go to the terminal .

```
 sudo apt-get update

sudo apt-get do-release-upgrade


```

given that actually fails do a dist-upgrade some have good luck updating from 10.04 other  have to go the longer route to 11.10  first, really just seems to me  its how well up to date  one keeps things someone who installs and then just forgets about it comes back only to update a few years later will have way more issues to contend with  .. 

hope this helps

---

### Post by satimis on 2012-05-06
> **grahammechanical said:**
> I am confused. Do you have or did you have 10.04 installed? You say this



So, why did you follow instructions that are specific to 10.04 or 11.10.

If you are upgrading 11.04 to 12.04 you have to first upgrade to 11.10 and then you upgrade 11.10 to 12.04. That is the recommended method.

It is possible to upgrade from one LTS release (10.04) to the next LTS release (12.04) and also to upgrade from the last release (11.10) to the next release (12.04) but we cannot jump from 11.04 to 12.04 or from 10.10 to 12.04.

You most probably have only upgraded to 11.10. Run this command

```
lsb_release -a
```

and see whether you have 11.10 or 12.04 or what?

Regards.

$ lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid

```

Other advice noted.  Thanks

B.R.
satimis

---

### Post by satimis on 2012-05-06
> **jadtech said:**
> 2.6.32-41-generic according to all my search  is lucid version 10.04

and what the documentation says is to do all the updates the release update should show up when you are at 10.04.4

change your server in update manager go to the terminal .

```
 sudo apt-get update

sudo apt-get do-release-upgrade


```

given that actually fails do a dist-upgrade some have good luck updating from 10.04 other  have to go the longer route to 11.10  first, really just seems to me  its how well up to date  one keeps things someone who installs and then just forgets about it comes back only to update a few years later will have way more issues to contend with  .. 

hope this helps

Thanks for your advice.

IIRC I did follows;
sudo apt-get update
sudo apt-get do-release-upgrade

on another VM, running 11.04 desktop, of this virtual machine.  On reboot only a black screen was displayed.  I'm still struggling to fix the problem.

B.R.
satimis

---

### Post by jadtech on 2012-05-06
you cant actually  go to 12.4 from 11.4 you have to do the dist upgrade first  to 11.10 this could be part of the issue maybe ..

I am no expert but I have did this up grade more then twice on 2 computers and  I mostly all good but I have had one go very wrong and just gave up  and did a complete new install ..

just one more tip if you do decide to move up to 11.10 then on to 12.4 before you do the up grade to 12  do an install of apt python-apt before the upgrade this can be a problem for some not everyone some already have it installed for other purposes but it is need to help in an orderly depackaging of the 12.4 install and it opens late in the upgrade and starts a cascade of dependcy issues  the upgrade completes but not all lib packages install so you would have no icons or guis or menus  on reboot .

it really pays to read all the  upgrade and release documentation  there is a lot of known issues and advice to prevent  problems in the long run ...

---

