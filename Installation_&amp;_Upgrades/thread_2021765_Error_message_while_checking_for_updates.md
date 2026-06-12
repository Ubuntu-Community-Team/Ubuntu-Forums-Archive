---
title: "Error message while checking for updates"
date: 2012-07-09
forum: Installation &amp; Upgrades
---

### Post by jlapinski4 on 2012-07-09
I am receiving this error message when attempting to check for regular updates:

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Any ideas? The only thing that was different was immediately prior to getting this error message I arrived at work and hadn't logged into the wireless network but attempted to check for updates. I canceled, rebooted, and logged into the wireless network. Now each time I attempt to check for updates I get the above error message. 

Thanks

---

### Post by jmfal on 2012-07-09
Welcome to Ubuntu,

Run this in a terminal it will unlock that file so you can update

```
    sudo rm /var/lib/dpkg/lock      
```

Then you can update

sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean
 sudo apt-get autoremove

---

### Post by plucky on 2012-07-10
It the above doesn't work then try removing the .list files with ```
sudo rm /var/lib/apt/lists/* -rf
``` and then running ```
sudo apt-get update
``` to reload them.

Good luck

---

### Post by jlapinski4 on 2012-07-10
Thank you both! 

Now, stupid question since I unlocked and updated from the terminal, do I need to run any further commands to install the updates?

---

### Post by jmfal on 2012-07-10
You should be good to go, if there are problems similar to this you might have to dig a little deeper to correct the problem.

---

### Post by jlapinski4 on 2012-07-11
Thanks!  I am just having issues getting a downloaded software package to install. I keep getting the error message cannot unpack jar files

---

### Post by MoebusNet on 2012-08-17
This error message showed up today in my upper taskbar:

> An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, Eroblem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restric ted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

This thread really saved the day!

Thank you jmfal & plucky!!

---

