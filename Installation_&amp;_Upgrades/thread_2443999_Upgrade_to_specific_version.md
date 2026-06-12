---
title: "Upgrade to specific version"
date: 2020-05-23
forum: Installation &amp; Upgrades
---

### Post by omanidos on 2020-05-23
Hi,

I currently have Ubuntu 18.04 on my PC and I want to upgrade to Ubuntu 18.04.4 but if I use "do-release-upgrade" it will install Ubuntu 20.04.
Is there a way to choose the version I upgrade to?

---

### Post by Impavidus on 2020-05-23
There's no release upgrade from 18.04 to 18.04.4. 18.04.4 is no separate release. It is a separate live disk image, with all the bugfixes released between April 2018 and January 2020 built in. If you just install all regular upgrades, you will get at 18.04.4. Actually, you should have got there in January.

---

### Post by CatKiller on 2020-05-23
Normal upgrades will take you from 18.04 to 18.04.4. The only difference between an upgraded 18.04 and a fresh install is that from 18.04.2 onwards fresh installs defaulted to the Hardware Enablement Stack and earlier versions didn't. You can choose to enable the HWE stack.

---

### Post by omanidos on 2020-05-23
Ok, thanks for the help.

---

### Post by deadflowr on 2020-05-23
In a terminal, check the output of
```
lsb_release -a
```
The Description should show as 18.04.4 on a fully up-to-date 18.04 release.

---

### Post by TheFu on 2020-05-23
```
sudo apt update
sudo apt full-upgrade
```

The "full-upgrade" goes from .0-->.1 --> .2 -->  .3 --> .4.
i don't know if it goes one at a time or jumps from .0 --> .4.  
i think to get the kernel version updated, you'll need use the HWE upgrade process.  
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_18.04_LTS_-_Bionic_Beaver](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_18.04_LTS_-_Bionic_Beaver)

You'll want full backups before doing any of this.
```

       full-upgrade (apt-get(8))
           full-upgrade performs the function of upgrade but will remove
           currently installed packages if this is needed to upgrade the
           system as a whole.

```

Two 16.04 examples. No HWE:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:        16.04
Codename:       xenial

istar:~$ uname -r
**4.4**.0-179-generic
```

This has the HWE:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:        16.04
Codename:       xenial

posc:/$ uname -r
**4.15**.0-99-generic
```

---

