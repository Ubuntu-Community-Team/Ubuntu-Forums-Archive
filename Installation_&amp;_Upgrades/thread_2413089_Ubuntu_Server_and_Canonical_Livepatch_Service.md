---
title: "Ubuntu Server and Canonical Livepatch Service"
date: 2019-02-21
forum: Installation &amp; Upgrades
---

### Post by rad0104 on 2019-02-21
Hey guys, I just installed ubuntu server and was trying to run the setup for canonical livepatch service and am receiving some errors that I am unfamiliar with and hoping someone could help out or point me in the right direction.
OS details:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.2 LTS"
```

When running the first step in the setup I get the following:

```
rad@plex:~$ sudo snap install canonical-livepatch


error: cannot perform the following tasks:
- Setup snap "canonical-livepatch" (54) security profiles (cannot setup apparmor for snap "canonical-livepatch": cannot load apparmor profiles: exit status 1
apparmor_parser output:
Cache read/write disabled: interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning: unable to find a suitable fs in /proc/mounts, is it mounted?
Use --subdomainfs to override.
)
- Setup snap "canonical-livepatch" (54) security profiles (cannot load apparmor profiles: exit status 1
apparmor_parser output:
Cache read/write disabled: interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning: unable to find a suitable fs in /proc/mounts, is it mounted?
Use --subdomainfs to override.
)
```

any help is greatly appreciated.

---

### Post by deadflowr on 2019-02-21
From last I remember livepatchs do not run on the [hwe kernels]("https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack").
Was this from the Ubuntu 18.04.2 install?
what's the current kernel version:
```
uname -a
```

---

### Post by rad0104 on 2019-02-21
Thanks for the reply its:

Linux plex 4.15.0-45-generic #48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by rad0104 on 2019-02-25
anybody?

---

