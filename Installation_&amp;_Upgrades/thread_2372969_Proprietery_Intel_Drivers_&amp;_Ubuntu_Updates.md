---
title: "Proprietery Intel Drivers &amp; Ubuntu Updates"
date: 2017-10-01
forum: Installation &amp; Upgrades
---

### Post by maxxx1234 on 2017-10-01
Hi all!

**Ubuntu Version:** 16.04 LTS

**Background:** I was messing around trying to solve a problem with my onboard Intel graphics HW (i915 based) & accelerated video playback, and installed the intel proprietery drivers using the "intel graphics update tool" from [https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.2](https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.2) in the process. Ironically I found out later the problem was caused by a kernel boot parameter and not the driver, so it probably would have worked with the default ubuntu i915 driver anyway.

I am now thinking of reverting back to the Ubuntu driver and removing the intel-installed stuff.

**Question:** Will I run into problems in the future when I try to update Ubuntu (for example next year to 18.04 LTS) and have the intel repository packages installed? Will there be conflicts, will I have to run the intel tool again to get driver updates in the future ans ubuntu wont touch them now, etc.? Or will the newer versions from Ubuntu supersede and overwrite the now installed intel stuff? Im wondering if I should try to remove the intel packages to get back to a clean ubuntu-only installation so I can upgrade easier later on with less conflicts etc.

The packages that were installed from the intel repository installed are:

> i915-4.6.3-4.4.0-dkms |          1 | [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial/main amd64 Packages
i965-va-driver | 1.7.1-0intel1 | [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial/main amd64 Packages
intel-gpu-tools | 1.15-1intel1 | [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial/main amd64 Packages
intel-graphics-update-tool |      2.0.2 | [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial/main amd64 Packages
libcairo-gobject2 | 1.15.2-0intel1 | [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial/main amd64 Packages
 libcairo2 | 1.15.2-0intel1 | [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial/main amd64 Packages
libva-drm1 | 1.7.1-0intel1 | [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial/main amd64 Packages
libva-egl1 | 1.7.1-0intel1 | [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial/main amd64 Packages
libva-glx1 | 1.7.1-0intel1 | [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial/main amd64 Packages
libva-tpi1 | 1.7.1-0intel1 | [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial/main amd64 Packages
libva-wayland1 | 1.7.1-0intel1 | [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial/main amd64 Packages
libva-x11-1 | 1.7.1-0intel1 | [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial/main amd64 Packages
    libva1 | 1.7.1-0intel1 | [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial/main amd64 Packages
va-driver-all | 1.7.1-0intel1 | [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial/main amd64 Packages
    vainfo | 1.7.1-0intel1 | [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial/main amd64 Packages

Should I remove the intel stuff, or can I leave it and it will be overwritten by newer Ubuntu packages from main repository?

Thanks for your help :)

---

### Post by maxxx1234 on 2017-10-03
Hi, maybe I did not phrase my question correctly, apologies for that. Lets try this way:

Will the Intel-installed packages ever get updated by Ubuntu updates?

---

### Post by ian-weisser on 2017-10-03
Eventually, when you upgrade to the next release of Ubuntu.

Apt, the package manager, will install the highest version number that it can from the sources available.

Here's an example using libva1:
Intel:  1.7.1-0intel1
Ubuntu 16.04: 1.7.0-1
Ubuntu 17.04: 1.7.3-2

You're running 16.04, which comes with 1.7.0.
You replaced it with a higher version, 1.7.1, from intel.

If Ubuntu adds 1.7.2 to the 16.04 repos, then it will replace the intel version.
However, Ubuntu won't do that. Any bugfixes and security patches will be assigned a 1.7.0 sub-version number...like 1.7.0-1ubuntu0.1 (currently in -proposed). As far as apt is concerned, it's still lower than 1.7.1, and apt won't *downgrade* a package unless you specifically instruct it to.

Instead, newer upstream versions go into the *next* release of Ubuntu, like 1.7.3 in 17.04, and 1.8.3 in 17.10.
If you want to try those newer versions of the software, you must install one of the newer versions of Ubuntu. That's how deb package management works.

---

### Post by maxxx1234 on 2017-10-05
Thank you very much Ian, that was extremely helpful!

I will leave everything as it is, and let apt sort it out during the next LTS upgrade in a year or so...

---

