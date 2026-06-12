---
title: "Could not initialize the package information"
date: 2012-08-29
forum: Installation &amp; Upgrades
---

### Post by jackstine on 2012-08-29
I just downloaded a copy of Ubuntu and put it on my new computer yesterday.  When I got it up and wanted to see if there were updates, I opened Update Manager and got this message.

[INDENT]An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
[/INDENT]
What is wrong?

---

### Post by Frogs Hair on 2012-08-29
Open the terminal and copy and paste or type the following one at time(update manager closed). 
 
Checks for updates
```
sudo apt-get update
```
Installs updates
```
sudo apt-get upgrade
``` 

If that fails post the terminal output in code tags using the # symbol on the reply box tools.

---

