---
title: "How can I stop weekly updates from installing a specific ethernet driver?"
date: 2020-09-29
forum: Installation &amp; Upgrades
---

### Post by cepheid42 on 2020-09-29
I have an MSI B550 motherboard that uses the Realtek r8125 driver.

Every week without fail, when the automatic update runs it removes the r8125 driver and installs the r8169 driver. This makes my ethernet connect completely unusable, Linux cannot even recognize the ethernet chipset correctly.

The only way to fix it is to manually purge the r8169 driver and install the r8125 driver by running the autorun script that comes with it.

I tried blacklisting the r8169 driver in /etc/modprobe.d/blacklist.conf as 
> 
# Blacklist bad ethernet driver
blacklist r8169


I'm not sure if this is working correctly, as it still removes the r8125 driver, but doesn't install the r8169 driver (as far as I can tell). So end up having to manually install the driver anyway.

It's super annoying, and I don't like the idea of turning off security updates entirely.

I submitted a bug report ([https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1895008](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1895008)), but it doesn't seem to be a concern for most people as even Google doesn't really have a lot of information about it.

---

### Post by mikewhatever on 2020-09-29
Since r8125 is not from the repositories, it must be rebuilt after a new kernel is installed. On average, that happens every 4-5 weeks, and not weekly. The Update Manager does not remove the r8125 driver, as it knows nothing about it. 
There is a way to auto-build the r8125 module with dkms: [https://help.ubuntu.com/community/DKMS](https://help.ubuntu.com/community/DKMS), which could be an interesting exercise, in case you are interested. 
Other then that, there is nothing to be done, but wait for the driver to be included in future kernels. It's a slow process that can take years.

---

### Post by cepheid42 on 2020-09-30
Thanks for the information. Is there a place to request drivers be added? That way if enough people chime in, it could be added sooner. It's a bit disheartening to think it could be years before it's fixed upstream, but oh well.

I'll look into the DKMS thing, it seems like it's not terribly hard to do. I'll just have to remember what I did for the future uses.

---

