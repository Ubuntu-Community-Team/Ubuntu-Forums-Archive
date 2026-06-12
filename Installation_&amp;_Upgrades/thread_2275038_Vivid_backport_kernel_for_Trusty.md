---
title: "Vivid backport kernel for Trusty?"
date: 2015-04-23
forum: Installation &amp; Upgrades
---

### Post by mattlach on 2015-04-23
Hey all,

I am doing a new install on a ultra low power haswell system and have to use the IGP GPU.

I understand video playback on this haswell gpu can have problems if on any kernel older than 3.18.4

I always stay on LTS releases, and thus don't want to run Vivid.

That being said LTS releases are supposed to get backported kernels from the latest release.

I have been trying to find information on how to install Vivid's 3.19 backport kernel in Trusty, but have been coming up short.

Is there a PPA or something I need to use?

If not, what is the best way to get a 3.18.4+ kernel?  Ideally I'd like to avoid mainline kernels, as apparently they lack certain Ubuntu drivers, and tweaks.  Getting something in an apt repository would also be ideal, as then it will automatically update in the future.

Appreciate any help!

Thanks,
Matt

---

### Post by dino99 on 2015-04-24
you can download to an empty folder the headers+images for a given kernel version, then from a terminal: sudo dpkg -i *
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by mattlach on 2015-04-25
> **dino99 said:**
> you can download to an empty folder the headers+images for a given kernel version, then from a terminal: sudo dpkg -i *
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I am familiar with this method, thank you.

Problem with mainline kernels - however - is that they lack Ubuntu patches and driver additions.

A proper Vivid backport would be ideal.

I'm guessing this is not available yet?

Current LTS releases are supposed to get the latest kernels backported  (Trusty - for example currently has the Utopic backport kernel).

Just a matter of waiting then?

---

### Post by sukinkot on 2015-05-20
Add Canonical Kernel Team PPA: 
sudo add-apt-repository ppa:canonical-kernel-team/ppa
sudo apt-get update
sudo apt-get install linux-generic-lts-vivid

---

### Post by Bucky Ball on 2015-05-20
> **sukinkot said:**
> Add Canonical Kernel Team PPA: 
sudo add-apt-repository ppa:canonical-kernel-team/ppa
sudo apt-get update
sudo apt-get install linux-generic-lts-vivid

Or don't:

> This ppa is used for building pre-release and test kernels.

It IS NOT RECOMMENDED that you subscribe to this PPA.

There is a [LOT]("https://duckduckgo.com/?q=3.18+kernel+.deb") of info out there about installing the 3.18 kernel in 14.**. 

When I have had to do what you are now doing in the past, I have been able to locate the .deb for the appropriate kernel without much effort and install with a couple of clicks. Good luck. ;)

---

### Post by grahammechanical on 2015-05-20
The back ports that you speak of are called point releases and it is not so long ago that Ubuntu 14.04.2 was release with the Utopic hardware enablement stack (including kernel). The next point release (14.04.3) is scheduled sometime during August this year. That is mostly likely when 14.04 will get the Vivid hardware enablement stack.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards.

---

