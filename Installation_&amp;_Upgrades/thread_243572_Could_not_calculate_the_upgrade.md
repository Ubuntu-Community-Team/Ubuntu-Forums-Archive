---
title: "Could not calculate the upgrade"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by Megaben on 2006-08-25
I updated my Breezy Badger to have all the latest versions, including the new update manager.  then I restarted the system.
When I run Update Manager it tells me there is a new release of the system (Dapper 6.06 LTS) and I start the upgrade process.  Several files get downloaded and it gets to the 3rd line (where is should I believe start the download of the updates themselves) and I get the error as on the subject line,**Could not calculate the upgrade** with this text following: "A unresolvable problem occured while calculating the upgrade. Please report this as a bug". 

I have tried restarting the system again, but no difference.  there are no further updates available for me to install.  What do I do now?

Thanks.

---

### Post by ciscosurfer on 2006-08-25
> **Megaben said:**
> ..."A unresolvable problem occured while calculating the upgrade. Please report this as a bug". 

I have tried restarting the system again, but no difference.  there are no further updates available for me to install.  What do I do now?

Thanks.
Have you reported this issue on Launchpad as a bug like the warning told you to?

And while you're on Launchpad, you can complain that the dev who wrote that warning needs to update it with proper English: "A unresolvable problem" should be "An unresolvable problem".

---

### Post by Megaben on 2006-08-25
I searched launchpad and found several users have same problem, which was reported in June....
The update installer thinks there are broken dependencies on ubuntu-desktop.  I removed the package and tried again - this time it complained that there was no ubuntu-desktop package installed.  Added it back and reverts to original error.....
Is there any way to check whether there really are broken dependencies? - and if so a way to fix them?

---

### Post by ciscosurfer on 2006-08-25
This usually does the trick for me```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

