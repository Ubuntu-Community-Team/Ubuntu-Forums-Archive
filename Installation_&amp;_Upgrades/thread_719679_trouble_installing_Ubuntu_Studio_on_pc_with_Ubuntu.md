---
title: "trouble installing Ubuntu Studio on pc with Ubuntu 7.10 already installed"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by fast eddie on 2008-03-09
Ok, here's the thing - I had a pc that had Win XP on and I successfully installed Ubuntu last year and have been happily using it ever since.

I would now like to use that pc to run Ubuntu Studio but I cant get it to boot from the ISO disk I have burned.

I know that the disk is ok because I tested it on another machine and I have changed the bios settings on the pc to boot from disc drive (actually I haven't changed any settings on the pc since I installed Ubuntu instead of XP last year).

My question is: why will it not boot from the cd? Is there a setting in Ubuntu that I need to change in order to put a new OS on?

Please help as I am losing the will to live - maybe that is an exaggeration but I am well p1ssed off with it now.

Thanks in advance for any helpful advice,

---

### Post by wolfen69 on 2008-03-09
ubuntustudio is just ubuntu with a new theme and extra packages installed. open synaptic and search for ubuntu studio. then you will have it without re-installing.

---

### Post by velib on 2008-03-09
> **wolfen69 said:**
> ubuntustudio is just ubuntu with a new theme and extra packages installed. 

It's not 'just ubuntu' with different theme and pkgs.  FYI, it runs on the low-latency kernel (linux-rt) with different settings.

fast eddie,

If you upgrade, take a look at this:
[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy)
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) 
(->Real-time kernel and Support sections.  There's a couple of config tweaks you'll need to make).

As far as the boot problems go, could it be you burned the ubuntustudio DVD on another machine, but the drive in the machine you're trying to install on is a cdrom?

---

