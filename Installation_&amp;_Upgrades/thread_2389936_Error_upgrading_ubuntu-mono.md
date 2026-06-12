---
title: "Error upgrading ubuntu-mono"
date: 2018-04-23
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2018-04-23
running a routine upgrade on 16.04 lTS I getting an error upgrading teh package ubuntu-mono

```
# apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  ubuntu-mono
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/178 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 303972 files and directories currently installed.)
Preparing to unpack .../ubuntu-mono_14.04+16.04.20180326-0ubuntu1_all.deb ...
Unpacking ubuntu-mono (14.04+16.04.20180326-0ubuntu1) over (14.04+16.04.20171116-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/ubuntu-mono_14.04+16.04.20180326-0ubuntu1_all.deb (--unpack):
 symbolic link '/usr/share/icons/ubuntu-mono-dark/status/24/gpm-primary-020.svg' size has changed from 24 to 19
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntu-mono_14.04+16.04.20180326-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Is the package broken? If the file gpm-primary-020.svg seems to be a a link gpm-battery-020.svg which seems to be a link to battery-020.svg

```
# ls -ld  gpm-primary-020.svg
lrwxrwxrwx 1 root root 24 Nov 16 17:38 gpm-primary-020.svg -> gpm-battery-020.svg

# ls -l gpm-battery-020.svg
lrwxrwxrwx 1 root root 15 Apr 23 18:05 gpm-battery-020.svg -> battery-020.svg

# ls -l battery-020.svg
-rw-r--r-- 1 root root 1766 Nov 16 17:49 battery-020.svg
```

---

### Post by dino99 on 2018-04-24
Have you ran clean/autoclean/autoremove and then re-uploaded ?

---

### Post by rsteinmetz70112 on 2018-04-24
Not autoclean, autoremove doesn't help. Also -f install doesn't help. I'll try autoclean later when I can get to the system.

ok tried autoclean and clean neither helped, got the same results.

---

### Post by rsteinmetz70112 on 2018-05-06
I deleted the files and links then reinstall ubuntu-mono via Synaptic. That seems to have worked

---

