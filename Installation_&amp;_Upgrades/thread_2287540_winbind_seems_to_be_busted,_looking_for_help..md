---
title: "winbind seems to be busted, looking for help."
date: 2015-07-20
forum: Installation &amp; Upgrades
---

### Post by ulao2 on 2015-07-20
Ubuntu 12.04.2 LTS


My computer names were not resolving and winbind seems to be set up right. I want not able to start or stop the service so I figure I'd remove and reinstall it. after it was removed and I tried to reinstall I get this.
```

sudo apt-get install winbind
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winbind : Depends: libwbclient0 (= 2:3.6.3-2ubuntu2.12) but 2:3.6.6-5 is to be installed
           Depends: samba-common (= 2:3.6.3-2ubuntu2.12) but 2:3.6.6-5 is to be installed
           Recommends: libpam-winbind but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Not sure where to go from here. I did try to install the dependencies


sudo apt-get install libwbclient0
Reading package lists... Done
Building dependency tree
Reading state information... Done
libwbclient0 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-image-3.2.0-38-generic-pae linux-image-2.6.35-23-generic-pae linux-image-3.2.0-37-generic-pae
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 493 not upgraded.


sudo apt-get install samba-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
samba-common is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-image-3.2.0-38-generic-pae linux-image-2.6.35-23-generic-pae linux-image-3.2.0-37-generic-pae
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0

also read that libnss-winbind is needed but get this
 sudo apt-get install libnss-winbind
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libnss-winbind is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

---

### Post by ulao2 on 2015-07-20
I replaced my source.list with a the official 12.04 and did an update, then I was able to install.

---

### Post by ajgreeny on 2015-07-20
Please use the Thread Tools menu at the top and mark this thread as SOLVED.
Apologies!  I see you have done that already; I didn't notice.

---

