---
title: "Can boot to ubuntu desktop, but not ubuntu server and lubuntu after install"
date: 2020-05-07
forum: Installation &amp; Upgrades
---

### Post by huailong on 2020-05-07
Hi,

I tried to install ubuntu desktop many times, but always crashed. I think it is because my machine has insufficient RAM of 1 GB.
I had a success once and it could boot and show grub.

Since it is too slow, I erase the disk and try to install lubuntu and ubuntu server on both UEFI and legacy mode. But it cannot boot and grub does not appear.
Here is the log from one boot-repair: [http://paste.ubuntu.com/p/ZzHNQ77kzH/](http://paste.ubuntu.com/p/ZzHNQ77kzH/)

I thought there should not be any difference between ubuntu desktop, ubuntu server and lubuntu in terms of booting?

---

### Post by DuckHook on 2020-05-08
Welcome to the forums, huailong.

A machine with 1GB RAM sounds like an old one. Please post the hardware specs and let's have a look. The pastebin that you linked to does not tell us things like Make, Model, CPU, MOBO, GPU, etc. Please provide those. The booting process loads many things. Obviously, a heavy DE like vanilla Ubuntu will be far more demanding than a CLI-only environment like Server.

System requirements for Ubuntu Desktop are 4GB RAM and relatively modern CPU and GPU. Server will run on much less, but 1 GB RAM is tight. Requirement page follows: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Please note the last paragraph:> With Lubuntu 18.04 LTS and before, you could use computers with even less memory, but with the newer LXQt desktop the Lubuntu team stopped providing minimum specifications so whilst it's still light, older hardware is no longer the primary focus of Lubuntu.You may be better off with a non-Ubuntu distro. You could try Puppy, Slitaz, Bunsenlabs. These are all designed to run on old HW. If happy staying entirely with the command line, you could also try the Ubuntu mini.iso. For some reason, Canonical is making it very hard to find this image so it is hidden in the following archive: [http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/)

Note that even if you install something like Bunsenlabs, 1 GB will provide a bad user experience. A modern browser without any other app running will be slow and painful. Without knowing the full HW specs, it is difficult to advise you, but if the machine is too underpowered, it may not be worth trying to run it.

---

### Post by guiverc on 2020-05-08
You didn't give specs for your machine.

I did use old boxes with only 1gb of ram for Lubuntu & Xubuntu up to the 19.04 cycle (whilst x86 was supported as 1gb was common for some non-upgraded x86 laptops/notebooks), but with amd64/x86_64 I now only test with 2gb (the usual minimum for 64 bit capable machines).

Booting can differ on hardware, and Lubuntu has testing under three categories
 - BIOS (legacy hardware)
 - UEFI controlled boot
 - Secure-UEFI
We want the system to boot on all three, however we can only test with hardware we actually have access to.

You provided no details on what release of Ubuntu/Lubuntu you actually tried, or provided details of your actual hardware. These details allow us to provide more specific advice/information.

---

