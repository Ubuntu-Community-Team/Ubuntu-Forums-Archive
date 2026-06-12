---
title: "Avast Errors"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by 2tired on 2008-01-12
I just installed Avast Deb file from the Avast website. Not only does it not work, but the package manager will not update..it says the following error:

could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package avast4server needs to be reinstalled, but I can't find an archive for it.'

 When I try to reinstall it says:

Could not open 'avast4workstation_1.0.8-2_i386.deb'

The package might be corrupted or you are not aloud to open the file. Check the permissions of the file.

I even tried to manually delete the files to see if it would help to reinstall it, but it did not. So, before I try to reinstall Ubuntu I thought I would see if anyone would be able to help!!!:confused:

---

### Post by Partyboi2 on 2008-01-13
Try 
```
sudo apt-get remove --purge avast4workstation_1.0.8-2_i386
```
or
```
sudo dpkg --remove --force-remove-reinstreq avast4workstation_1.0.8-2_i386
```

---

### Post by 2tired on 2008-01-14
This is what the first command gave me.....

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package avast4server needs to be reinstalled, but I can't find an archive for it.

This is the 2nd command....

dpkg - warning: ignoring request to remove avast4workstation_1.0.8-2_i386 which isn't installed.

It is still coming up with this error when I run the update manager...

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package avast4server needs to be reinstalled, but I can't find an archive for it.'

I cannot get into the package manager or reinstall the deb file, it says it is corrupted..Does this mean a complete Ubuntu reinstall or is there a work around?:confused:

---

### Post by tgiannak on 2008-02-05
please did anyone solve that problem?? i have the same problem with avast and i can't update please help

---

