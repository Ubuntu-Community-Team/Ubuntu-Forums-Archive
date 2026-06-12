---
title: "Installation fails"
date: 2004-11-19
forum: Installation &amp; Upgrades
---

### Post by drochaid on 2004-11-19
I've tried to install Ubuntu on my HP nx5000 laptop 3 times now. Each time all goes great [Centrino wifi picked up and configured straight off etc  :-) ] until it starts setting up the packages, just after downloading the updates. I've tried this with and without downloading updates adn same result.

It just stops dead at "Setting up pmount (0.1.6) ..." and does nothing. Any ideas?

---

### Post by arctic on 2004-11-19
hi there.
could you please post some more info about your laptops hardware? (hdds, motherboard, usb-devices, graphics,...)

---

### Post by wallijonn on 2004-11-26
[http://packages.debian.org/unstable/utils/pmount](http://packages.debian.org/unstable/utils/pmount) :
> pmount is a wrapper around the standard mount program which permits normal users to mount removable devices without a matching /etc/fstab entry. This provides a robust basis for automounting frameworks like GNOME's Utopia project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some information like device labels and mount options from hal and passes them to pmount. Install the package "hal" if you want to use this feature. 

[dep]
libc6 (>= 2.3.2.ds1-4) [not alpha, ia64]
    GNU C Library: Shared libraries and Timezone data
[dep]	
libsysfs1
    Interface library to sysfs
[sug]	
hal
    Hardware Abstraction Layer


pmount = partition mount. 

Did you take the defaults for setting up all the partitions? Otherwise it may be something in the HAL, which would point to some unsupported hardware. So start by disconnecting any USB devices, disabling USB in the BIOS, etc.

---

### Post by nzgreen on 2004-12-10
I've just installed Ubuntu on my nx5000 and can confirm that there is a conflict with HAL and the onboard Broadcom 4400 network adapter.  I don't have a need for it, so I added b44 to /etc/hotplug/blacklist to stop the driver from loading.  HAL works fine now  ;-)

---

