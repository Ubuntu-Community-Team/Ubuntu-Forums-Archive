---
title: "Ubuntu 12.04 uninstall wine problem"
date: 2012-06-23
forum: Installation &amp; Upgrades
---

### Post by ali_gear1 on 2012-06-23
```
sudo dpkg --list | grep wine
ii  wine-gecko1.5                          1.5-0ubuntu1~ppa1~precise1              Microsoft Windows compatibility layer (embedded web browser)
rc  wine1.4                                1.4-0ubuntu5~precise1~ppa1              Microsoft Windows Compatibility Layer (Binary Emulator and Library)
rc  wine1.4-i386                           1.4-0ubuntu5~precise1~ppa1              Microsoft Windows Compatibility Layer (32-bit support)
ii  wine1.5                                1.5.6-0ubuntu1~pulse17                  Microsoft Windows Compatibility Layer (Binary Emulator and Library)
ii  wine1.5-i386                           1.5.6-0ubuntu1~pulse17                  Microsoft Windows Compatibility Layer (32-bit support)

```result:

```
sudo apt-get purge wine
sudo apt-get remove wine
----------------------------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by grahammechanical on 2012-06-23
I will not say that this is the solution for certain but ...

You have two versions of Wine installed and you need to remove the one installed through a PPA (wine 1.4) before you can remove the other version of wine (wine 1.5). That is my guess.

You may need to install a utility to purge the PPA

```
sudo apt-get install ppa-purge
```

and then use the command

```
sudo ppa-purge ppa:1.4-0ubuntu5~precise1~ppa1
```

Or something like that.

Another idea would be to see if Ubuntu Software Centre will remove it for you.

Regards.

---

### Post by ali_gear1 on 2012-06-23
> **grahammechanical said:**
> I will not say that this is the solution for certain but ...

You have two versions of Wine installed and you need to remove the one installed through a PPA (wine 1.4) before you can remove the other version of wine (wine 1.5). That is my guess.

You may need to install a utility to purge the PPA

```
sudo apt-get install ppa-purge
```and then use the command

```
sudo ppa-purge ppa:1.4-0ubuntu5~precise1~ppa1
```Or something like that.

Another idea would be to see if Ubuntu Software Centre will remove it for you.

Regards.
```
PPA to be removed: ppa:1.4-0ubuntu5~precise1~ppa1 ppa:1.4-0ubuntu5~precise1~ppa1
Warning:  Could not find package list for PPA: ppa:1.4-0ubuntu5~precise1~ppa1 
ppa:1.4-0ubuntu5~precise1~ppa1

```

---

### Post by Jibbals on 2012-12-12
I've got the same problem, is there an answer for this out there?

```

~$ sudo dpkg --list | grep wine
[sudo] password for jibbals: 
ii  libkwineffects1abi3                    4:4.8.5-0ubuntu0.2                      library used by effects for the KDE window manager
ii  wine                                   1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (meta-package)
ii  wine-gecko1.4                          1.4.0-0ubuntu2                          Microsoft Windows compatibility layer (embedded web browser)
ii  wine1.3                                1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (transitional package)
ii  wine1.4                                1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (Binary Emulator and Library)
ii  wine1.4-common                         1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (transitional package)
ii  wine1.4-i386                           1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (32-bit support)
ii  winetricks                             0.0+20120308                            Microsoft Windows Compatibility Layer (winetricks)

```

solution?
```

sudo dpkg --list | grep wine
sudo apt-get purge wine
sudo apt-get purge wine1.3
sudo apt-get purge wine1.4
sudo apt-get purge wine-gecko1.4
sudo apt-get purge winetricks
sudo apt-get autoremove
sudo dpkg --list | grep wine

```

This seemed to uninstall all my wine packages, is there anything I'm missing?

---

### Post by LuisGMarine on 2012-12-12
Have you tried using Synaptic Package Manager?  It can't hurt to search wine in synaptic and trying to remove the packages (if possible).
```

sudo apt-get install synaptic
```

---

### Post by Jibbals on 2012-12-12
> **LuisGMarine said:**
> Have you tried using Synaptic Package Manager?  It can't hurt to search wine in synaptic and trying to remove the packages (if possible).
```

sudo apt-get install synaptic
```

Thanks, I tried it out and it looks like my previous purging got rid of the wine packages.

I'll hold onto synaptic package manager for next time

---

