---
title: "Samba can't install"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Dusal on 2010-04-04
I fresh installed 10.04 32bit on my PC. And I tried to install Samba from Ubuntu software center. Then software center give me system-config-samba dependency error.
I tried
sudo apt-get install system-config-samba
from terminal. But there was no luck.

```
tuguldur@tuguldur-desktop:~$ sudo apt-get install system-config-samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  system-config-samba: Depends: python-libuser but it is not installable
E: Broken packages
tuguldur@tuguldur-desktop:~$ 

```

I can't find python-libuser. I tried to download from debian package. But it can't be installed too. How can I solve this problem?

---

### Post by garvinrick4 on 2010-04-05
Have you code: To fix broken packages, to clean cache, to fetch new samba with depends.

sudo apt-get install -f

sudo apt-get clean

sudo aptitude install samba


You can check your install:

aptitude show samba

---

### Post by Dusal on 2010-04-05
Thank you. But I already tried it. samba is working. But system-config-samba is can't be installed. It's visible "Samba" in software center. I'm not developer. I'm end-user. I reported bug to launchpad.

---

### Post by emarkay on 2010-04-05
What's the bug # so we can verify and subscribe if needed?

---

### Post by DevHead on 2010-04-05
> **Dusal said:**
> I fresh installed 10.04 32bit on my PC. And I tried to install Samba from Ubuntu software center. Then software center give me system-config-samba dependency error.
I tried
sudo apt-get install system-config-samba
from terminal. But there was no luck.

```
tuguldur@tuguldur-desktop:~$ sudo apt-get install system-config-samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  system-config-samba: Depends: python-libuser but it is not installable
E: Broken packages
tuguldur@tuguldur-desktop:~$ 

```

I can't find python-libuser. I tried to download from debian package. But it can't be installed too. How can I solve this problem?

Same issue here.
--> 04/05/2010 daily build

---

### Post by garvinrick4 on 2010-04-05
Python-lybuser seems to say it is automatically installed with install.


rick@rick-laptop:~$ aptitude show system-config-samba
Package: system-config-samba
State: installed
Automatically installed: no
Version: 1.2.63-0ubuntu4
Priority: optional
Section: universe/admin
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 6,001k
Depends: python, python-central (>= 0.6.7), samba, python-libuser
Description: GUI for managing samba shares and users
 system-config-samba is a graphical user interface for creating, modifying, and
 deleting samba shares and users.

rick@rick-laptop:~$ aptitude show python-libuser
Package: python-libuser
State: installed
Automatically installed: yes
Version: 1:0.56.9.dfsg.1-1ubuntu2
Priority: optional
Section: admin
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 217k
Depends: libc6 (>= 2.4), libglib2.0-0 (>= 2.12.0), libpam0g (>= 0.99.7.1),
         libuser1, python (< 2.7), python (>= 2.5), python-support (>= 0.7.1)
Conflicts: python2.3-libuser (< 1:0.54.6-2.1.dfsg.1-1.1)
Replaces: python2.3-libuser (< 1:0.54.6-2.1.dfsg.1-1.1)
Provides: python2.5-libuser, python2.6-libuser
Description: user and group account administration library (development files)
 The libuser library implements a standardized interface for manipulating and
 administering user and group accounts.  The library uses pluggable back-ends to
 interface to its data sources.

rick@rick-laptop:~$

---

### Post by DevHead on 2010-04-05
After further deliberations, I wanted to see if the issue was with my previous version.

1. Clean install of BETA 1
2. Ran all updates.
3. Tried to install system-config-samba
4. See stats below:


devhead@beta1:~$ sudo apt-get install system-config-samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  system-config-samba: Depends: python-libuser but it is not installable
E: Broken packages
devhead@beta1:~$

Same results as before.  Hmm.

---

### Post by DevHead on 2010-04-06
Update:

1. Clean install of Karmic Koala
2. Ran all updates
3. Tried to install system-config-samba
4. **[COLOR="blue"]Samba installed perfectly![/COLOR]**

Something isn't right with Lucid.  :(

---

### Post by Dusal on 2010-04-06
Yes I think it's lucid bug. I reported here: [https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/555499](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/555499) But it was duplicate of this: [https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/555295](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/555295)

---

### Post by scradock on 2010-04-06
system-config-samba is only a GUI for configuring Samba shares. Samba installs and works fine without it. You can configure simple shares using /etc/samba/smb.conf, or even more simply by using "Sharing" in Nautilus.

---

### Post by DevHead on 2010-04-09
I wonder if they took it out of Lucid.

---

### Post by RJARRRPCGP on 2010-04-09
No, they didn't remove the whole package.

---

