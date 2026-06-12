---
title: "secureboot-db update error"
date: 2018-10-31
forum: Installation &amp; Upgrades
---

### Post by rattskjelke on 2018-10-31
Today I got this when updating Xubuntu 18.04.1 LTS:
```
The following packages will be upgraded:
  secureboot-db
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,488 B of archives.
After this operation, 21.5 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 secureboot-db amd64 1.4~ubuntu0.18.04.1 [8,488 B]
Fetched 8,488 B in 0s (30.9 kB/s)         
(Reading database ... 188269 files and directories currently installed.)
Preparing to unpack .../secureboot-db_1.4~ubuntu0.18.04.1_amd64.deb ...
Unpacking secureboot-db (1.4~ubuntu0.18.04.1) over (1.1) ...
Setting up secureboot-db (1.4~ubuntu0.18.04.1) ...
Can't access efivars filesystem at /sys/firmware/efi/efivars, aborting
$ 
```
Is this bad? This is an older BIOS pc that doesn't have secure boot as far as I can tell.

---

### Post by ubfan1 on 2018-10-31
Shouldn't be a problem on your older PC.  I just noticed I have the same package on my legacy install of 18.04, but never noticed any update errors, (possibly because they were buried in the other update messages).

---

