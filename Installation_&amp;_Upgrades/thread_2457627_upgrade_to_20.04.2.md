---
title: "upgrade to 20.04.2"
date: 2021-02-05
forum: Installation &amp; Upgrades
---

### Post by tendouser on 2021-02-05
is there any command to upgrade easily????

---

### Post by CatKiller on 2021-02-05
If you're already using 20.04, you're using 20.04.2.

---

### Post by tendouser on 2021-02-05
then how to upgrade to the specific kernel 5.8 would be the further question!

---

### Post by oldfred on 2021-02-05
I have never done it. 

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
> It is advised to keep Ubuntu Desktop 20.04 LTS with the kernel flavour picked during installation. 

---

### Post by guiverc on 2021-02-06
To update your software lists (so your system knows what packages are available)

```
sudo apt update
```

To apply all upgraded packages availble

```
sudo apt full-upgrade
```

this will automatically bump you from 20.04/20.04.1 to 20.04.2.  (`sudo apt upgrade` will apply most upgrades, but can leave some behind for later; refer `man` pages for more details)

There are two kernel options

- GA or generic option is 5.4 for 20.04 LTS.  This is the default of Ubuntu 20.04 LTS Server, and is seen as the most stable option.

- HWE or hardware enablement which changes during the life of 20.04.  This kernel recently upgraded to 5.4, the kernel from Ubuntu 20.10, in the future will use 21.04, 21.10, before finally 22.04's kernel. This is useful for more recent hardware

Links are
- [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
- [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

See the first link for how to switch to the HWE stack if you wish to.  Note it's the same link already provided by @oldfred.

---

