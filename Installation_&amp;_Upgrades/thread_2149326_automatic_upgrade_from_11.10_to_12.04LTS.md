---
title: "automatic upgrade from 11.10 to 12.04LTS"
date: 2013-05-28
forum: Installation &amp; Upgrades
---

### Post by ziemowitzima on 2013-05-28
Dear Ubuntu Users,
I need to upgrade from 11.10 to 12.04 LTS. I have a lot of software and other stuff on my 11.10.
Is there any way to do this without losing it ? (I mean without necessity of new installation)

Is the automatic upgrade function (which pops up in Update Manager) safe, able to do this ?

Best
and Thanks

---

### Post by deadflowr on 2013-05-28
It's a crapshoot.

I've used it repeatedly and haven't had a bad experience, except once on a new version release launch day.

But others have had opposite experiences.

read the [release notes]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes")

And if possible, back up your personal data.

---

### Post by Frogs Hair on 2013-05-28
Before proceeding  backup anything important !  In the update manager > settings there is setting to check for new releases . Once marked run the update manager and see if the upgrade is offered . 11.10 reached end of life may 9th so I don't know the effects if any on the ability upgrade. [https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)
 
It is likely there will be updates to your current software because 11.10 is gnome 3.2 and 12.04 uses gnome 3.4 . If the non Ubuntu software you are using has been updated by the developer you should have no problem , but there are programs that become obsolete with each new release.
 
Disable any PPAs you may have or you may end up with broken packages if they are not supported in 12.04 . If you have gnome 3.2 themes installed some may not work at all or display properly in 12.04.
 
      
After observing an upgrade I am convinced they take longer and have more problem potential than a clean installation.

---

### Post by deadflowr on 2013-05-28
> **Frogs Hair said:**
> 
After observing an upgrade I am convinced they take longer and have more problem potential than a clean installation.

Quite true, because when you think about it, a clean install only installs what's on the disk.
But an upgrade updates all the packages on the PC.
So the more you've installed, the more it'll have to upgrade.
The more it has to upgrade, the chances of problems coming up increase.

---

