---
title: "[SOLVED] Software update deadly embrace of network-manager and network-manager-gnome"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by bousozoku on 2007-12-05
I've checked both networking threads and those related to installations and upgrades and have found nothing that works so far.

Way back when the 7.10 release candidate was made available, I installed it.  After that, I noticed the Restricted Drivers Manager and I downloaded and installed support for *NVIDIA accelerated graphics driver (latest cards)* and *Firmware for Broadcom 43xx chipset family*.  This seemed to cause a problem with shutting down and network-manager didn't seem to like something.

After wiping the volume and re-installing 7.04 and consequently upgrading to 7.10, I didn't seem to have a problem (that I remember) until Software Update had some network-manager update.

Now, I have a problem with network-manager and network-manager-gnome, as they are apparently not able to be configured.  I would provide the text from the process but everything grinds to a halt and I have to power off and power on the machine to continue.  Since one package seems to require the other, it would seem that it cannot go forward.

I have tried:

[LIST]
[*]re-installing the packages through Synaptic Package Manager

[*]sudo apt-get upgrade

[*]sudo apt-get update
[*]sudo apt-get install -f

[*]sudo apt-get clean
[*]sudo apt-get autoclean
[/LIST]

None of which caused any real difference.

Networking continues to work and, while I'd like to remove network-manager and network-manager-gnome to see how that would work, in case of corrupted packages, I'm unsure as to whether I'll be able to connect to download new packages.

My next thought is to disable the Broadcom 43xx firmware to see if that has any positive effect on the situation since I rely on a wired connection at the moment.

I'm sure someone with greater experience on Linux and GNOME will have good ideas, so please feel free to tell me something new.

Thanks in advance!

**Removing the Broadcom firmware corrected the problem and the update was able to continue.  Maybe obviously, the wireless card doesn't serve much of a purpose now, so this is hardly solved, but I'm mostly using a wired connection.**

---

