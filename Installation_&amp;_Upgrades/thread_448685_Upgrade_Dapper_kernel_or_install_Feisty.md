---
title: "Upgrade Dapper kernel or install Feisty?"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by brundles on 2007-05-19
I have an HVR1300 DVB-T card which has been sitting idle in the machine for a while now and thought I'd get a few opinions before drowning in ambition...

Currently I'm running a Dapper Drake install as an HTPC - uses Myth (0.18 - old I know) as the front end and works nicely as a download machine (using Ninan along with a bunch of scripts to manage the downloaded files, switch off when done, etc) and streaming WMV files to the Xbox 360 (uShare - very handy :) ).

Now to get the native kernel support for the HVR1300 I want to put the 2.6.20 kernel in. I also want to (eventually) get onto a newer version of Myth. 

I suspect I'm going to be better off just upgrading the kernel in Dapper and then upgrading Myth in my own time, but wondered if anybody thought I'd be better off rebuilding from scratch using Feisty instead. I'm a bit dubious about that for a couple of reasons. The first is the Nvidia problems I've read about on the Feisty install (I have one of the AGP MX440 cards that got dropped to legacy). The second, more important issue, is the wife! Put it this way - I get more grief for a 10 minute 'net outage here at home than I do if one of our customers at work has an hour long outage nationwide!!!! I suspect the outcome if the Feisty install meant she couldn't watch her TV shows for a week or two would not be pretty!

Any thoughts or opinions appreciated.

Thanks!

---

### Post by scrooge_74 on 2007-05-19
Is Dapper is working fine you should let it that way is going to have a long support life. . Feisty could give you troubles as it may not. If you have room to spare you could try installing it also on a dual boot config

---

### Post by brundles on 2007-05-29
Thanks for the advice scrooge - I've taken the plunge and built 2.6.20-11. So far with mixed results - so I'm hoping some kind guru like souls can help out...

First up - immediately following the ram disk load, it complains about devfs being an unknown file system. I suspect I can resolve this by rebuilding the kernel tracking down the relevant driver and building it into the kernel rather than as a module. I'm curious as to why this didn't sort itself out given I started with a make oldconfig though.

Next, the dreaded Nvidia (sp?) drivers... 

The first boot to the new kernel loudly failed to boot X coming up with an X style BSOD indicating that it couldn't find the nvidia module. Swapping the xorg.conf to nv rather than nvidia resolved this but left me with a 640x480 screen. I'm assuming that rebuilding the official Nvidia drivers against 2.6.20-11 will resolve this, but will it leave me with only 2.6.20-11 working on Nvidia rather than a working X desktop when I boot back to 2.6.15?

On the plus side, checking messages showed that it picked up the DVB card on bootup :).

Once I get the above sorted (and I've rebuilt the IRC and LCD drivers against the new kernel), it'll be time to work out what's happened to Myth during the upgrade!

---

### Post by retsaw on 2007-05-30
devfs has been deprecated for years and was finally removed from the kernel in the 2.6.17 release (I think).  I would have thought Dapper would be using udev by default anyway.  This means you'll have to switch your current install to udev if you want to do the kernel upgrade.

As to the nVidia issue, I think your card will be supported by the latest drivers and you should be able to use install the driver for multiple kernels (this may be dependent on how Ubuntu handles the installation of the drivers).  I guess you'll have to test this yourself, although you always have the nv drivers as a fallback if it doesn't work.  Using my nVidia MX 420 on another distro, I'm sure the latest 97xx drivers worked, although there was a reason that now escapes me that I used the 96xx drivers instead, the legacy drivers are 71xx which did work as well.

---

### Post by brundles on 2007-05-30
Thanks for the response.

I saw some other stuff about devfs not being supported for a while. I'd wondered if it was anything to do with the difference between mkinitrd and mkinitramfs - the only thing I saw on the topic beyond a load of questions with the same problem I have but no answer.

Assuming it's not the mkinitrd/mkinitramfs thing, how do I switch from devfs to udev? I'm guessing that's not a simple thing?

---

### Post by tgalati4 on 2007-05-30
Check the repositories, there are some nvidia configuration tools that work with "nvidia" driver.  Of course you get the "nvidia taints the kernel message", but hey it works.

---

