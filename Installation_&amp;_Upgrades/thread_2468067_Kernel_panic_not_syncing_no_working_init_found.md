---
title: "Kernel panic not syncing no working init found"
date: 2021-10-17
forum: Installation &amp; Upgrades
---

### Post by bkl070 on 2021-10-17
I did search but didn't find anything similar enough. I am attempting to install Ubuntu 16.04.6 from usb thumb drive on an older machine. Get the error found in the title. Have no idea what to do next.[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289299&stc=1[/IMG]

---

### Post by grahammechanical on 2021-10-17
Why Ubuntu 16.04.6? It has reached end of its standard support life. Once installed you will need to activate Extended Security Maintenance (ESM) in order to get security support up to April 2026.

If you do not think that the latest versions of Ubuntu will run well on that machine then think about installing one of the Flavors of Ubuntu such as Lubuntu. As for this problem you should describe the install options you have chosen.

Is this a dual boot? What partitions have you decided on? At what point of the installation did this error appear? Was it during the install process or after the installation finished and the machine was rebooted? As a wild guess it seems that the Linux kernel cannot find some of its modules. 

According to Wikipedia

> In [Unix]("https://en.wikipedia.org/wiki/Unix")-based computer [operating systems]("https://en.wikipedia.org/wiki/Operating_system"), **init** (short for *initialization*) is the first [process]("https://en.wikipedia.org/wiki/Process_(computer_science)") started during [booting]("https://en.wikipedia.org/wiki/Booting") of the computer system. Init is a [daemon]("https://en.wikipedia.org/wiki/Daemon_(computing)") process that continues running until the system is shut down. It is the direct or indirect [ancestor]("https://en.wikipedia.org/wiki/Parent_process") of all other processes and automatically adopts all [orphaned processes]("https://en.wikipedia.org/wiki/Orphan_process"). Init is started by the [kernel]("https://en.wikipedia.org/wiki/Kernel_(computing)") during the [booting]("https://en.wikipedia.org/wiki/Booting") process; a [kernel panic]("https://en.wikipedia.org/wiki/Kernel_panic") will occur if the kernel is unable to start it.

If I was getting an error message like that I would re-install. Less trouble.

Regards

---

### Post by MAFoElffen on 2021-10-17
As mentioned, That version is End of life and not supported...

Next, have have not mentioned anything about the machine information you are trying to install it on... Or what architecture... so no one can recommend what may be going on...

I see from the screen shot that it is an HP Pavilion, but do not recognize what the exact model may be. (And I have my HP Warranty Service Certs.)

I will make a wild guess that it is HP Pavilion 061 with an Intel Pentium D, 2 core, 64bit CPU... About circa 2012 through 2013(?) A very rough guess. Which "should" run current Ubuntu flavors.

With a hardware addressing error such as that, at that point in the installation process, what I would recommend... Download a current 20.04.3 LTS. Upon the download, before creating your USB key, verify the sha5sum to ensure you have a good image. One you can verify that, create your USB LiveCD installation media. 

Before you try booting the media, update your BIOS firmware to latest...

When you boot from it, let it go though the file checks of the installation media of the LiveCD to verify the filesystem is good... The when it get to either "Try" or "Install", select "try." to verify that it runs as a "Stable System" before you install...

I see no reason why you should install an end of life OS of that system. As long as the system can run a current support LiveCD environment.

---

