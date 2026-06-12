---
title: "update manager is not working!!!!"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by smooth5959 on 2011-06-03
I have been using 11.04 for a while, no real problems, until recently when i go to launch Update Manager, i get the following message: (someone please help)

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by plucky on 2011-06-03
> **smooth5959 said:**
> I have been using 11.04 for a while, no real problems, until recently when i go to launch Update Manager, i get the following message: (someone please help)

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Welcome to the Forum.

Open a terminal and run ```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
``` and then see if update manager will now run.


Good Luck

---

### Post by Jalexa5834 on 2011-06-03
Thanks so much. I've been struggling with this very issue for a couple weeks now. Very simple solution and much appreciated!

Any ideas on what may have caused this to happen in the first place? It was working well until just over a couple weeks ago...

Thanks again!

---

### Post by smooth5959 on 2011-06-03
Thank you so much, it worked! This is why i LOVE Ubuntuand the Ubuntu community. Thanks again

---

