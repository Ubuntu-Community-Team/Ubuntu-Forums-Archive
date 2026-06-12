---
title: "Fixed a problem - wise I hadn't, NVIDIA issues"
date: 2015-05-24
forum: Installation &amp; Upgrades
---

### Post by bugbear6502 on 2015-05-24
For a while I'd been getting an error when updating via apt-get:

Error! Bad return status for module build on kernel: 3.13.0-51-generic (x86_64)
Consult /var/lib/dkms/nvidia-331-updates-uvm/331.113/build/make.log for more information.

Having some time on my hands, I though I'd clean this up.

I found this thread:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1268257](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1268257)

With the cure (workround)
sudo apt-get install --reinstall nvidia-331 nvidia-331-uvm

Did that, went OK, rebooted. Nvidia driver newness is MINE!

Arrgh! Fuzzy Text.

Googling reveals this to be a common problem, FXAA aliasing, which can "apparently"
be turned on via nvidia-settings.

However, this dialog is meant to have sections for X Screen 0
and GPU 0 (see thread

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1309595](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1309595)
)

Mine looks like this:

[ATTACH=CONFIG]262187[/ATTACH]

No good!?

Further, my monitor/display is now good old 1024x768, which is a shame
when I've got a Dell Vostro 1700 with a 1440 x 900 display.

Can any one help - right now going back a driver version or two would
suit me well enough.

I think I've "just" got a completely borked driver settings,
or (meta-fault) borked driver settings-settings.

 BugBear

---

### Post by bugbear6502 on 2015-05-24
I'm guessing this would be helpful:

lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

uname -r
3.11.0-13-generic

nvidia-331                     331.113-0ubuntu0.0.4  amd64 NVIDIA binary driver - version 331.113
nvidia-331-uvm                 331.113-0ubuntu0.0.4  amd64 NVIDIA Unified Memory kernel module
nvidia-opencl-icd-331-updates  331.113-0ubuntu0.0.4  amd64 NVIDIA OpenCL ICD
nvidia-prime                   0.6.2                 amd64 Tools to enable NVIDIA's Prime
nvidia-settings                331.20-0ubuntu8       amd64 Tool for configuring the NVIDIA graphics driver


 BugBear

---

### Post by bugbear6502 on 2015-05-25
In order to make my PC vaguely usable, I've switched to neaveau via Software & Updates->Additional Drivers.

This seems to have switched me into 1280 x 800 (according to Display Settings), which is better than 1024x768, but I don't think it's right.

 BugBear

---

### Post by efflandt on 2015-05-25
Whenever I kept getting that error about bad return error for nvidia-331-updates-uvm during kernel updates (or nvidia-*-uvm for some newer driver versions) ignoring the error did not result in any issues, so I simply removed that uvm package which did not result in any issues. It is a "Unified Memory kernel module", but have not found a good explanation when it might be used other than CUDA or OpenCL programming for using cpu and gpu in parallel, which I have not been involved with. I don't know if it is used for normal graphics or if forcing uvm interferes with normal graphics. Not having uvm installed is not a problem on my hybrid Intel/Nvidia graphics laptop:```
efflandt@GE60-2OE:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-331-updates                                    331.113-0ubuntu0.0.4                                amd64        NVIDIA binary driver - version 331.113
ii  nvidia-opencl-icd-331-updates                         331.113-0ubuntu0.0.4                                amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver
```And maybe uvm was erroring in nvidia-349 (from xorg-edgers ppa) on my desktop, because uvm package is not currently installed on that either. The 1080p display that works fine (clearly) and likewise for 1080p HDTV on my desktop, including Steam games.

How is your graphics device described in lspci (begins with small L). Typically it would be on a line containing "VGA", but nvidia on my laptop is on a line with "3D" (on my desktop nvidia is on a line with VGA).```
efflandt@GE60-2OE:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
efflandt@GE60-2OE:~$ lspci | grep 3D
01:00.0 3D controller: NVIDIA Corporation GK106M [GeForce GTX 765M] (rev ff)
```

---

### Post by bugbear6502 on 2015-05-25
> **efflandt said:**
>  

How is your graphics device described in lspci (begins with small L). 
```

lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G86M [GeForce 8400M GS] (rev a1)


```

    BugBear

---

