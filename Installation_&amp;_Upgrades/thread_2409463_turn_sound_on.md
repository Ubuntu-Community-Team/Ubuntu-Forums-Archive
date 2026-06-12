---
title: "turn sound on?"
date: 2019-01-02
forum: Installation &amp; Upgrades
---

### Post by mringer on 2019-01-02
I upgraded from L-UB 14 to 16 and the sound is turned off. 
On the last occasion I searched the forum and found a
thread here:

[https://ubuntuforums.org/showthread.php?t=2209009&highlight=turn+sound](https://ubuntuforums.org/showthread.php?t=2209009&highlight=turn+sound)

where  ajgreeny  said to use alsamixer. On that 
occasion it worked & I thanked Ajgreeny  . But this time 
I tried  alsamixer   & it failed. It says everything is on.  
In UB 14, there was a small volume control button near
the bottom RH of the screen, not now.

lshw says [cut]

```

       *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:29 memory:fe9fc000-fe9fffff

```

---

