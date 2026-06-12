---
title: "Update Manager Sources List Duplicates Problems  Help"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by rlj1965 on 2008-10-17
1) Getting the following error here on a new install of Hardy 8.04 when trying to run the update manager. 

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'W:Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_hardy_partner_binary-i386_Packages), E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

2) Also, this PC gives me no sound. It has an Audigy card in it as well as onboard sound. I have disabled onboard sound in the bios so the audigy card should be clear. I have the medibuntu and all other multimedia codecs installed. Tried switching between alsa and pulseaudi in the sound manager. I am stumped on this.

Thanks for any help.

Rich

---

### Post by sisco311 on 2008-10-17
open a terminal and post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by cariboo on 2008-10-17
This is the 4th time I've seen this error in the last day or two, doing a little research it turns out you have the Ultimate Linux repositories enabled, the repositories have been down since October 13th. If you don't want to see the error message comment out the Ultimax repositories and un comment all the repositories that were commented out when you set up the Ultimax repositories.

Jim

---

### Post by Pinpoint Focus on 2008-10-18
> **rlj1965 said:**
> 1) Getting the following error here on a new install of Hardy 8.04 when trying to run the update manager. 

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'W:Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_hardy_partner_binary-i386_Packages), E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

2) Also, this PC gives me no sound. It has an Audigy card in it as well as onboard sound. I have disabled onboard sound in the bios so the audigy card should be clear. I have the medibuntu and all other multimedia codecs installed. Tried switching between alsa and pulseaudi in the sound manager. I am stumped on this.

Thanks for any help.

Rich
I have been dealing with this problem for the last week and have gotten no were. Help.

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

