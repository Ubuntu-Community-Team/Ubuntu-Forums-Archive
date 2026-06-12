---
title: "ubuntu installation"
date: 2019-01-29
forum: Installation &amp; Upgrades
---

### Post by bijumeethal on 2019-01-29
[ATTACH=CONFIG]282350[/ATTACH]..


    Please support me to solve this issue , after installation when selecting ubuntu OS

---

### Post by Frogs Hair on 2019-01-29
The screen displays a wubi message which is no longer supported. Can you tell us more about this installation such as Windows and Ubuntu version. There is an unofficial wubi [fork]("https://github.com/hakuna-m/wubiuefi/wiki"),  but any questions would have to be directed to the developer though there is some trouble shooting information.

---

### Post by bijumeethal on 2019-01-29
windows version 8.1
Ubuntu 10.04 LTS

---

### Post by Dennis N on 2019-01-29
> **bijumeethal said:**
> windows version 8.1
Ubuntu 10.04 LTS
The problem with those old versions like Ubuntu 10.04 from 2010 are that they get no updates to keep your system safe. And you can't install additional software. The best choices now are currently supported versions 16.04 and 18.04.

---

### Post by Impavidus on 2019-01-30
Ubuntu 10.04 still came with a wubi installer. I think support for it was officially dropped with version 12.04 or 12.10 and a few releases later the wubi installer was actually removed from the live disk. The reason for this removal was that wubi is incompatible with the UEFI/GPT systems normally found with Windows 8 and later.

Fix the Windows boot loader. If you can still boot Windows, you should find an Ubuntu/wubi uninstaller that should do the job. Then either try a proper dual boot, a virtual machine or remove Windows entirely (not recommended if you're a Linux beginner and don't have a second computer still running Windows).

---

### Post by bijumeethal on 2019-01-31
i try to install with Edubuntu 14.04 LTS then also showing same error message

---

### Post by bijumeethal on 2019-01-31
[COLOR=#000000]i try to install with Edubuntu 14.04 LTS then also showing same error message[/COLOR]

---

### Post by Impavidus on 2019-02-01
The wubi install may have confused your Windows boot loader. You have to fix that from Windows. If you can't boot Windows, use a Windows repair disk. Only then you can prepair your system for installing Ubuntu alongside Windows. Use Windows tools to shrink the Windows partition to make unallocated space available for Ubuntu, then let the Ubuntu installer work. Alternatively, just wipe Windows, but if you're a Linux beginner you should only do that if you have a second computer with Windows available.

Stay away from wubi. Also, 14.04 is old and only has 2 months of support left. I don't know the plans of the Edubuntu team (or what's left of it), but it seems that 14.04 was the last release and it's almost dead. Don't install it, unless you really want to use it for no more than 2 months. However, the edubuntu-desktop metapackage is still available on later LTS releases of all Ubuntu flavours.

---

