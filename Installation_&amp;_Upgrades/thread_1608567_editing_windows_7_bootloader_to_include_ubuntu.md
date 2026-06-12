---
title: "editing windows 7 bootloader to include ubuntu"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by helios_05 on 2010-10-29
Hi,
I want to ask if there is a way to use the windows 7 bootloader as my default loader in a dual boot?
I want to install ubuntu 10.10 64 bit with windows 7 64-bit in a separate partition.
Tried wubi before but now I cannot boot in ubuntu.Thanks in advance.

---

### Post by mikewhatever on 2010-10-29
Probably a good idea to ask at a Windows7 forum.

---

### Post by graphius on 2010-10-29
As far as I know, the windows bootloader will only install one operating system (windows). In fact it will only load one version of windows. It is hard to run, for example xp and win7 on the same drive.
What is wrong with grub? it will load any windows and ubuntu (and MacOS and ....) You can even make Windows the default boot.

---

### Post by me_loco on 2010-10-29
> **helios_05 said:**
> Hi,
I want to ask if there is a way to use the windows 7 bootloader as my default loader in a dual boot?
I want to install ubuntu 10.10 64 bit with windows 7 64-bit in a separate partition.
Tried wubi before but now I cannot boot in ubuntu.Thanks in advance.

try this.
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by helios_05 on 2010-10-29
thanks mate.I finally solved it.I install the ubuntu 10.10 in a separate partition with grub in that partition not overwriting the MBR.Then using the EasyBCD([http://neosmart.net](http://neosmart.net)) you can easily edit the windows bootloader to add ubuntu.Thanks for the quick response.

---

