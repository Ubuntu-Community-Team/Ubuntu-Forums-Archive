---
title: "No more space left on device"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by souled on 2009-11-30
I have Ubuntu Server installed on one of my computers, and I decided to install ubuntu-desktop. I didn't, however, realize that I didn't have enough space on the partition. While unpacking the files, dpkg threw an error about not enough space:

```
Unpacking gnome-desktop-data (from .../gnome-desktop-data_1%3a2.26.1-0ubuntu2_all.deb) ...
dpkg: unrecoverable fatal error, aborting:
 unable to flush /var/lib/dpkg/updates/tmp.i after padding: No space left on device
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

How can I remove all of the packages and any metadata they left behind? When I try and run autoremove or uninstall, I get this message:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

When I try and run that, dpkg just complains about no more space... i can't free up any more space, so I'd rather just remove al of the packages. 

Thanks

---

### Post by phillw on 2009-11-30
> **souled said:**
> I have Ubuntu Server installed on one of my computers, and I decided to install ubuntu-desktop. I didn't, however, realize that I didn't have enough space on the partition. While unpacking the files, dpkg threw an error about not enough space:

```
Unpacking gnome-desktop-data (from .../gnome-desktop-data_1%3a2.26.1-0ubuntu2_all.deb) ...
dpkg: unrecoverable fatal error, aborting:
 unable to flush /var/lib/dpkg/updates/tmp.i after padding: No space left on device
E: Sub-process /usr/bin/dpkg returned an error code (2)

```How can I remove all of the packages and any metadata they left behind? When I try and run autoremove or uninstall, I get this message:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```When I try and run that, dpkg just complains about no more space... i can't free up any more space, so I'd rather just remove al of the packages. 

Thanks

Hi,
try ```
sudo apt-get clean
```

This will remove all the archived installs - this only matters if you re-install a package, as the system will have to go and get if from the repositry.

that should give you enough room.

Regards,

Phill.

---

