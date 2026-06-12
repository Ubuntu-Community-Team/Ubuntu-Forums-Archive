---
title: "Update Manger won't let me update 2 Evolution updates? after upgrade to Ubuntu 11.10"
date: 2012-04-21
forum: Installation &amp; Upgrades
---

### Post by ledzepjes on 2012-04-21
I recently upgraded to Ubuntu 11.10 and ever since I get 2 Evolution updates that show up in Update Manager that I can't check mark to update, they just keep showing up. Also, when doing "sudo apt-get update" I don't see these show up?

I just opened synaptic package manager and searched for evolution, then it showed 2 packages that had grey ! marks beside them in the place of a green or white box. I right clicked them and they show the option to upgrade. 

They are listed as:
architecture independent files for Evolution
standard plugins for Evolution

Which is just the description for 2 pacakges named evolution-common and evolution-plugins.

Usually, for an installed package it shows a "green box", rt clicking then shows the options to:
Mark for Reinstallation
Mark for Removal
Mark for Complete Removal
Properties

For a package that's not installed it shows a "white box" to the left and rt clicking gives the options:
Mark for Installation
Properties

But for theses 2 packages listed in Synaptic Package Manager as:
```
Package           Installed Version Latest Version   Description
evolution-common  2.32.2-0ubuntu7   3.2.2-0ubuntu0.1 (architecture independent files for Evolution)
evolution-plugins 2.32.2-0ubuntu7   3.2.2-0ubuntu0.1 (standard plugins for Evolution)
```
the options are:
Mark for Upgrade
Mark for Removal
Mark for Complete Removal
Properties

and the installed version of 2.32.2 is not the latest version nor is it the same as the other 20-25 packages listed (all the packages shown after searching for evolution) that all have version 3.2.2, so I rt clicked both and upgraded, clicked apply, it upgraded and after which it also installed previously uninstalled package "Evolution", which probably got uninstalled during the upgrade process but all the left over pieces where still there or not all of the packages left over were upgrading properly.

Now when I run Update Manager it shows no packages.

Is there a terminal way to do this or a code for me to search for, or verbosely show, all packages that need upgraded?

---

### Post by jerrrys on 2012-04-21
Maybe a dist-upgrade would solve it.

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by ledzepjes on 2012-04-22
what do you mean? I think that's what caused it, or rather the behavior of not having Evolution updated happened after I upgraded from Ubuntu 10.04 through to 11.10 just recently

---

### Post by jerrrys on 2012-04-22
Wow, congratulations :)

But thats a release upgrade (s)

---

### Post by Ubuntu Warrior on 2012-05-01
Have the same problem only there are now three updates greyed out:

evolution-common
evolution-indicator
evolution-plugins

I assume this has something to do with 11.10/12.04 not defaulting Evolution anymore? Thunderbird now seems to be the flavour of the day.

---

### Post by jerrrys on 2012-05-01
> **Ubuntu Warrior said:**
> Have the same problem only there are now three updates greyed out:

evolution-common
evolution-indicator
evolution-plugins

I assume this has something to do with 11.10/12.04 not defaulting Evolution anymore? Thunderbird now seems to be the flavour of the day.

Its probably not any different from a regular apt-get install, but I think its worth a try.

Here's the download link:

[https://help.ubuntu.com/community/EmailClients#Evolution](https://help.ubuntu.com/community/EmailClients#Evolution)

Edit: also still think a dist-upgrade is worth a try :)

sudo apt-get dist-upgrade

---

