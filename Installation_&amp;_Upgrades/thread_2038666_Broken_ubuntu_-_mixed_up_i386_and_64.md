---
title: "Broken ubuntu - mixed up i386 and 64?"
date: 2012-08-07
forum: Installation &amp; Upgrades
---

### Post by frncz on 2012-08-07
Hello
I just installed ubuntu, and then tried to install dropbox, which failed.
Now, the Ubuntu Software Center opens and crashes. Installing programs in the terminal gives, for example:
:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

I would love some help
Mike

---

### Post by frncz on 2012-08-07
In addition, this message may be useful, obtained when I click the 'No Entry' icon on the top bar:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
A re-boot does not fix this.

---

### Post by plucky on 2012-08-07
> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binar y-i386_Packages
E: The package lists or status file could not be parsed or opened.


From a terminal ```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

The first command removes all the .list files in the /var/lib/apt/lists/ directory,and the second command reloads them.

There seems to be a problem in the name of one of the files (binar y-i386)

Good Luck

---

### Post by frncz on 2012-08-10
> **plucky said:**
> From a terminal ```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

The first command removes all the .list files in the /var/lib/apt/lists/ directory,and the second command reloads them.

There seems to be a problem in the name of one of the files (binar y-i386)

Good Luck

This is great. It fixed my problem. Very many thanks

Mike

---

