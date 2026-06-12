---
title: "Troubles updating Linux kernel"
date: 2016-01-20
forum: Installation &amp; Upgrades
---

### Post by dott-micronesia on 2016-01-20
Hi! 

I have a long story to tell but i'll try to be short. 

I'm a stable user of Kubuntu 14.04 LTS,but i have some problems running Garry's Mod and other games. When i join much servers or i load some heavy stuff in single player my computer is 100% going to freeze or to automatically reboot. This happens to other heave games too but Gmod and other source engine games are more subject to this type of problems. 
When this happens i can't do anything:Can't open tty,can't move mouse,can't press any key. The pc is just frozen and all i can hear is hard disk working hard ininterruptly before i manually reboot by case's button.
I decided to install amd proprietary drivers but it worked just for 2 days. After that,everytime i boot my pc freezes after some seconds on splash screen (the one with "kubuntu" lamping,text's shadow stops moving and i can't input anything).

Having to uninstall drivers by rescue mode terminal and reusing MESA's ones,i tried to update my kernel. A friend of mine that used Kubuntu 14.04 too told me he had no problems with 3.19. Installed images and headers,but when i boot i get an overscan (big black borders around the screen),low resolutions,USB ports didn't work and some little graphical glitches appeared. After that i rebooted with 3.14 and uninstalled other version.

Now i want to try to update my kernel again to the most reliable version for my hardware and maybe try to install amd drivers,what do you suggest me?

Here's a complete report of my computer: [www.googledrive.com/host/0B2rl3ANGEgeAR2ltbUVRNkJoa1k/](www.googledrive.com/host/0B2rl3ANGEgeAR2ltbUVRNkJoa1k/)

---

### Post by Bucky Ball on 2016-01-20
Welcome. If you are able to get to a desktop I suggest you do a regular update/upgrade before doing anything else.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Reboot when that's finished. What kernel are you now at? That will get you to the newest kernel for your release. This might be exactly the way your friend got there. Were they using the same release as you?

You should do an update prior to updating any software, not just drivers.

---

### Post by grahammechanical on 2016-01-20
I suggest that you revert to an open source video driver when doing this because part of the installation of a new kernel includes building a kernel module for the video driver. Also make sure that the latest proprietary video drivers still support your video card. As I found out, there will be problems installing a newer kernel if it also brings in a newer proprietary video driver that no longer supports the video card. 

Where are you getting this new kernel from? That also makes a difference. Kernels installed through the usual Kubuntu/Ubuntu channels will have been tested.

You also might want to think about upgrading the Hardware Enablement Stack as a means of getting kernel 3.19. It is the hardware enablement stack that came with the release of vivid (15.04) that has kernel 3.19. Please run

```
uname -a
lsb_release -a
```

And tell us the results.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards.

---

### Post by dott-micronesia on 2016-01-20
> **grahammechanical said:**
> I suggest that you revert to an open source video driver when doing this because part of the installation of a new kernel includes building a kernel module for the video driver. Also make sure that the latest proprietary video drivers still support your video card. As I found out, there will be problems installing a newer kernel if it also brings in a newer proprietary video driver that no longer supports the video card. 

Where are you getting this new kernel from? That also makes a difference. Kernels installed through the usual Kubuntu/Ubuntu channels will have been tested.

You also might want to think about upgrading the Hardware Enablement Stack as a means of getting kernel 3.19. It is the hardware enablement stack that came with the release of vivid (15.04) that has kernel 3.19. Please run

```
uname -a
lsb_release -a
```

And tell us the results.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards.

Hi.

I'm already on open drivers because as i said amd's ones brick my system.

All informations you ask are present in my hardware information scan linked in first post,but i'll paste them again here:

uname -a:
Linux lorenzo-System-Product-Name 3.13.0-76-generic #120-Ubuntu SMP Mon Jan 18 15:59:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

lsb_release -a:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty

> **Bucky Ball said:**
> Welcome. If you are able to get to a desktop I  suggest you do a regular update/upgrade before doing anything else.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Reboot when that's finished. What kernel are you now at? That will get  you to the newest kernel for your release. This might be exactly the way  your friend got there. Were they using the same release as you?

You should do an update prior to updating any software, not just drivers.

As i said,yes,he's using Kubuntu 14.04.3 as i am and as far as i know he installed kernel packages from APT.

Will the dist-upgrade get me to latest Kubuntu release or i'll still get the newest LTS?

---

### Post by Bucky Ball on 2016-01-20
No. dist-upgrade will NOT upgrade your release to a newer one, on the software you have to the latest.

---

