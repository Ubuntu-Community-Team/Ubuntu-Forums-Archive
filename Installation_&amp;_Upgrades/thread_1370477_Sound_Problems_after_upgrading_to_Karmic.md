---
title: "Sound Problems after upgrading to Karmic"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by lol768 on 2010-01-02
Hi,
After upgrading to ubuntu 9.10 I have experienced no sound. I am using a 82801G (ICH7 Family) High Definition Audio Controller (rev 01) sound card and have my headphones attached to the front headphone jack. I know that on 9.04 I had to turn "independent HD" off before the sound would work, however in 9.10 I cannot access the volume control where I was previously able to set this option. I have tried EEEandrew's solution ([https://wiki.ubuntu.com/eeeandrew](https://wiki.ubuntu.com/eeeandrew)), but the only thing that happens is that I do not receive the "waiting for system sound message" and the sound dialog never appears.

Here is the output from lshw:

*-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:16 memory:fea78000-fea7bfff
[B]
EDIT: Solved the problem by using the alsa mixer and disabling independent HD from there.[/B]

---

