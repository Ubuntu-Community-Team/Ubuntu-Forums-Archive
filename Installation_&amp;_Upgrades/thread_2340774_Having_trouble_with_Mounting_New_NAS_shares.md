---
title: "Having trouble with Mounting New NAS shares"
date: 2016-10-22
forum: Installation &amp; Upgrades
---

### Post by mapota on 2016-10-22
Hi All,

I have just installed a new instance of mythbuntu 16.04.1 and cannot get shares to mount. This was working on 14.04.5.

I have followed the advice on [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently). but the biggest issue I have is with the install of CIFS-UTILS.

When I try to install I get

```
$sudo apt-get install cifs-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cifs-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'cifs-utils' has no installation candidate

```


I have tried

sudo apt-get update
sudo apt-get upgrade 
and 
sudo apt-get dist-upgrade
to no avail.

lsb_release -a gives me !


No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


Any ideas, everything I can find on the net 

Thanks

---

### Post by deadflowr on 2016-10-22
cifs-utils is in main repository.
What repositories do you have enabled?

---

### Post by mapota on 2016-10-22
I have not changed them from the standard install of mythbuntu.

I have reverted the system back to the original hard disk. Will be able to check and report back tomorrow.

Just had a quick look on the net and I am 99% certain that the "canonical-supported free and open source software (main)"is ticked. Along withth e three below it.

Andrew

---

### Post by mapota on 2016-10-23
Tried a full reinstall and all good now. Not sure what happened.

---

