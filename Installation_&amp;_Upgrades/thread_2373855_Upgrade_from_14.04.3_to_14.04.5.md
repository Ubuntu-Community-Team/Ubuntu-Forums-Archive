---
title: "Upgrade from 14.04.3 to 14.04.5"
date: 2017-10-10
forum: Installation &amp; Upgrades
---

### Post by pradeep8985 on 2017-10-10
Hi,

I wanted to upgrade from 14.04.3 to 14.04.5. I did mount the 14.0.4.5 dvd on the existing server and pointed the sources.list to 14.0.4.5 and tried the below commands.

apt-get clean
apt-get upgrade 

However the above doesn't work. Am i missing something here? How do i perform the upgrade?

```
# apt-get update
Ign file: trusty InRelease
Get:1 file: trusty Release.gpg [198 B]
Get:2 file: trusty Release [4,592 B]
Ign file: trusty/main Translation-en_IN
Ign file: trusty/main Translation-en
Ign file: trusty/restricted Translation-en_IN
Ign file: trusty/restricted Translation-en
Reading package lists... Done

```
```
# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by westie457 on 2017-10-10
What does ```
apt-get dist-upgrade
```return?

---

### Post by pradeep8985 on 2017-10-10
Nothing.. 

```
# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

---

### Post by westie457 on 2017-10-10
I admit I know little to nothing about servers and their setup.

There might be some clues for you on this page. [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by ajgreeny on 2017-10-10
What does command ```
lsb_release -a
uname -a
``` give as output?  It will probably tell you that you are already on 14.04.5 if you have been updating in the usual fashion; the one thing it may not have done is give you the newest kernel from the LTS Enablement Stack, linked to by westie457.

---

### Post by pradeep8985 on 2017-10-10
Thanks. But No, i do not want to upgrade kernel alone. I just want entire packages to upgrade to 14.04.5 release.

---

### Post by pradeep8985 on 2017-10-10
> **ajgreeny said:**
> What does command ```
lsb_release -a
uname -a
``` give as output?  It will probably tell you that you are already on 14.04.5 if you have been updating in the usual fashion; the one thing it may not have done is give you the newest kernel from the LTS Enablement Stack, linked to by westie457.

I did check that as well. Here is the output

```
# lsb_release -a ; uname -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty
Linux testubuntu 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux



```

---

### Post by ajgreeny on 2017-10-10
I think you have misunderstood the background to the various point releases that are available for the LTS versions of Ubuntu.

As an example I installed this Xubuntu-16.04  system using the 16.04.1 iso file but now when I run that ```
lsb_release -a
uname -a
``` what I see is ```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial
$ uname -a
Linux XubuntuXenial 4.4.0-96-generic #119-Ubuntu SMP Tue Sep 12 14:59:54 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```
ie, I am now on the 16.04.3 version, though not using the LTS Enablement Stack for 17.04, as the current kernel and xorg versions run fine on my hardware.
All other packages are, however, exactly the same version as they would be had I started with the 16.04.3 point iso file, as will all yours be if you have kept the system fully updated.

---

### Post by pradeep8985 on 2017-10-10
> **ajgreeny said:**
> I think you have misunderstood the background to the various point releases that are available for the LTS versions of Ubuntu.

As an example I installed this Xubuntu-16.04 system using the 16.04.1 iso file but now when I run that ```
lsb_release -a
uname -a
``` what I see is ```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial
$ uname -a
Linux XubuntuXenial 4.4.0-96-generic #119-Ubuntu SMP Tue Sep 12 14:59:54 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```
ie, I am now on the 16.04.3 version, though not using the LTS Enablement Stack for 17.04, as the current kernel and xorg versions run fine on my hardware.
All other packages are, however, exactly the same version as they would be had I started with the 16.04.3 point iso file, as will all yours be if you have kept the system fully updated.

Okay, let me make my point clear.. How do i upgrade my current 14.04.3 to 14.04.5 version (without reinstallation).... How do i do that?

---

### Post by deadflowr on 2017-10-10
> Okay, let me make my point clear.. How do i upgrade my current 14.04.3 to 14.04.5 version (without reinstallation).... How do i do that?
Not much to do but install the xenial hwe stack for trusty.
See here: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr")
You can also run the hwe-support-status commands
```
hwe-support-status --verbose
hwe-support-status --show-replacements
hwe-support-status --show-all-unsupported
```
They should give you a rundown of what packages to install and what, if any, need to be removed.
(Adding... the output should closely match what's posted in the link)

---

