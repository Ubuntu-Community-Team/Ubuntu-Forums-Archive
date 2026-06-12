---
title: "Upgrading from 16.04 LTS to 18.04 LTS 2023"
date: 2023-11-15
forum: Installation &amp; Upgrades
---

### Post by GROMS on 2023-11-15
I am trying to upgrade my Ubuntu 16.04 lts to 18 lts from the terminal prompt.  I've done all the updates , downloaded the update-manager [ sudo update-manager -d ]. It finally shows a window that the computer is up to date and that "Ubuntu 18.04 is now available (you have16.04)".  There are 3 buttons: Settings, Upgrade and OK. When I select the upgrade button, It just returns to the $ prompt and does nothing. The first time I tried this and gotten the above window with only the settings and ok buttons. Am I doing something wrong or is there a better way?? this is flustering.

---

### Post by ian-weisser on 2023-11-15
Ubuntu 16.04 stopped receiving security updates two years ago (exception: Ubuntu Pro subscribers).
Were your system on one of my networks, I would require you to backup your data and install Ubuntu 22.04. Takes about an hour, including the backup and restore of your data.

By way of comparison, release-upgrade to Ubuntu 18.04...which is also past the End of Standard Support...means another release-upgrade to 20.04. Then (optionally) yet another to 22.04.
You could spend half the day tediously doing all that. And a problem with any of those release-upgrades means a new install anyway.

Also: Do not use the -d flag without fully understanding what it does. Its use, along with "*downloaded the update-manager*" suggests that you are following long-obsolete instructions.

---

### Post by grahammechanical on 2023-11-15
Run

```
man do-release-upgrade
```

That will explain the the -d switch upgrades to the development version. The present Ubuntu development version is Ubuntu 24.04. We cannot upgrade from 16.04 to 24.04 (development version).

> -d, --devel-release
              If  using  the latest supported release, upgrade to the development release

Try opening Software and Updates>Updates tab and make sure that the box "Notify me of a new Ubuntu version" is set to "For long-term support versions." Then reboot and see if Ubuntu put out a dialog offering to update to 18.04.

As stated above you are going to have to do 3 online updates (LTS version) to get to 22.04 (the latest LTS release). Not only does this take time but there is a big difference between Ubuntu 16.04 and 22.04. It is possible that something will get messed up.

Regards

---

### Post by MAFoElffen on 2023-11-18
Did you do your due diligence and do a good backup yet? I would.

After that, did you try
```

sudo apt update
sudo apt install -y update-manager-core 
sudo do-release-upgrade

```

---

