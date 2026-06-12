---
title: "Need Procedure for Downgrading Kernel"
date: 2021-02-21
forum: Installation &amp; Upgrades
---

### Post by jasonterando on 2021-02-21
Hi, I've installed Focal and it works great on my ThinkPad X1.  Because it's 2021 and we still can't have nice things, my company's security department is mandating we install Cylance, a "security" package by BlackBerry.  The fine folks at BB have not yet deigned to support kernel 5.8, so I have to downgrade to 5.4.

I've tried running ```
sudo apt-get upgrade linux-image-5.4.0-65-generic
``` which installs the old kernel and gets it into Grub, but none of my networking devices (WiFi, Bluetooth, etc.) are recognized.  Is there some other package I need to install or process to run?

 FYI - my machine uses the Intel 8265/8275 wireless adapter

---

### Post by CatKiller on 2021-02-21
If you want to stay on the 5.4 branch you'll want to install the **linux-generic** and remove the **linux-generic-hwe-20.04** metapackages, as well as removing your 5.8 kernels. It's the Hardware Enablement stack that will pull in the newer kernels, but the 5.4 general availability branch that 20.04 came with will also be supported and get security updates for the life of the release.

For your hardware support it's the -modules packages that bring those in, I think.

If your hardware only got support with the 5.8 branch then you'll be out of luck and you'll have to choose which you want, but that doesn't seem particularly likely.

---

### Post by DuckHook on 2021-02-21
Welcome to the forums, jasonterando.

You need to install more than linux-image. You also need headers and modules.

Better to use:```
sudo apt install linux-generic
```&#8230;which is a metapackage that will drag in not only image, but headers and modules as well.

EDIT:

CatKiller must have Ninja'd me by seconds.

---

### Post by kansasnoob on 2021-02-23
There is an "official" process:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_20.04_LTS_-_Focal_Fossa](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_20.04_LTS_-_Focal_Fossa)

---

### Post by grahammechanical on 2021-02-23
Once you get the system running on the 5.4 kernel do not use Software Updater to update/upgrade the system. Use the terminal.

```
sudo apt update
sudo apt upgrade
```

Software Updater will bring in newer kernels and run apt autoremove and possibly remove the 5.4 kernel again. Even if update/upgrade through the terminal does bring in 5.8 kernel the 5.4 kernels will still be accessible from Grub menu Advanced Options for Ubuntu.

An alternative is to carefully review what Software Updater is offering and untick 5.8 kernels. I find that if I update/upgrade through the terminal and do not run autoremove then Software Updater will load and offer to remove packages that are no longer needed. Giving Software & Updater authority to do that will take out the older kernels that you need to keep.

Regards

---

### Post by DuckHook on 2021-02-23
> **grahammechanical said:**
> Once you get the system running on the 5.4 kernel do not use Software Updater to update/upgrade the system.…
May as well get it off my chest… I *HATE* Software Updater. It's ruined a few installs on me. If one knows how to apt-mark hold a package, then one can avoid the worst of its damage, but then, if one is that handy with apt, why use Software Updater?

---

