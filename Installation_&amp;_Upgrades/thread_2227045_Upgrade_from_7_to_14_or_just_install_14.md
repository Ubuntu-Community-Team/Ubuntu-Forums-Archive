---
title: "Upgrade from 7 to 14 or just install 14"
date: 2014-05-30
forum: Installation &amp; Upgrades
---

### Post by Chris_Aiken on 2014-05-30
One of my customers is running V7.1 and I'd like to get then on the latest 14.
Obviously I can just do a fresh install of 14 but that will cause me some problems with other software currently installed.
Is it worth upgrading throught the versions or can I install 14 without wiping the other data on the system?

---

### Post by bapoumba on 2014-05-30
Upgrading from Gusty 7.10 to Trusty 14.04 is a long way to go.. I would honestly recommend you fresh install, provided the machine specs can handle later ubuntu releases. You may want to have a look at lubuntu or xubuntu.

Now if you have a separate /home partition, or a separate storage area, when installing please choose "do something else" to be able to keep those unformatted. If not, I would recommend to backup all user data on a removable device (backups are mandatory, whichever path you choose).

What other software have you installed ?

---

### Post by slickymaster on 2014-05-30
Hey Chris_Aiken, welcome to the forums.

> **bapoumba said:**
> Upgrading from Gusty 7.10 to Trusty 14.04 is a long way to go.. I would honestly recommend you fresh install, provided the machine specs can handle later ubuntu releases. You may want to have a look at lubuntu or xubuntu.

Now if you have a separate /home partition, or a separate storage area, when installing please choose "do something else" to be able to keep those unformatted. If not, I would recommend to backup all user data on a removable device (backups are mandatory, whichever path you choose).

What other software have you installed ?

A big +1 on bapoumba's advice.

Just let me add something about the upgrade concept in the *buntu family. An upgrade is the process of going from an earlier version of Ubuntu to a newer version of Ubuntu with an installed system and should only be done from one release to the next release or from one LTS release to the next. In your customer's case this would be going from Ubuntu 7.10 to Ubuntu 8.04 LTS and progressively upgrading to each LTS successive version until you get 14.04 LTS.

Renewing the Installation without formatting the partitions (in contrast to upgrading), will also keep his personal data and configurations under **/home** but will renew all system settings under **/etc** as well as the default set of installed packages.

Here's something you should read: [install Ubuntu without loosing configs (even if /home not separate)]("http://ubuntuforums.org/showthread.php?p=11770332#post11770332")

---

### Post by Chris_Aiken on 2014-05-30
I'll probably do a clean install then. It's a decent Dell server, or was four years ago.
We use an programming language which has a licence key based on the hardware and installed OS so may well need a new config key if re-installed. So my customer will be down until I get the new key.
We're in the UK and the software company is in the US. It's not a massive problem, just a bit  inconvenient.
We'll be taking backups.
Thanks for your help.

---

### Post by bapoumba on 2014-05-30
> **Chris_Aiken said:**
> I'll probably do a clean install then. It's a decent Dell server, or was four years ago.
We use an programming language which has a licence key based on the hardware and installed OS so may well need a new config key if re-installed. So my customer will be down until I get the new key.
We're in the UK and the software company is in the US. It's not a massive problem, just a bit  inconvenient.
We'll be taking backups.
Thanks for your help.

You are most welcome and thanks to slickymaster :)

I personally would check about the license key before doing anything else. I recall on one occasion a very nice interaction with a software provider. I checked in advance as I was changing machines, the previous one was going to be recycled, and they did give me a new key for free. But I asked before doing anything as it was a stopper deal. Your customer may not appreciate if they end up not getting back up at all ..

---

