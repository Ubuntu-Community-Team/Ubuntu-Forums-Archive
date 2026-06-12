---
title: "why kernel is not getting updated on 12.04"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by stephenbbb on 2014-04-26
I have two installs of 12.04 both on amd 2core arch. one of them shows kernel 3.8 while the other one is 3.2

why the difference and casn I upgrade the kernel on the 3.2 to a newer kernel? i need higher than 3.5 for BTLE capability.

thanks everyody

---

### Post by Bashing-om on 2014-04-26
stephenbbb; Hi !

Maybe; with release 12.04.1 to get the later kernels one must enable the hardware stack.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
However, doing so - if you are running ATI proprietary drivers on the 2x/3x/4x/ cards, will break ! With no other good solution.
```

sudo lshw -C display

```
to make sure before taking that leap.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by stephenbbb on 2014-04-26
i get ;
  *-display               
       description: VGA compatible controller
       product: Wrestler [Radeon HD 6250]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:41 memory:80000000-8fffffff ioport:4000(size=256) memory:90400000-9043ffff


i know I am using fglrx from amd, but both boxes are using it and the one with 3.8 kernel upgraded the kernel when I intalled a new 12.04 ona new SSD. it must have intsalled 12.04.02. 
will try the hw stack upgrade in may after sth important on this box gets taken care of. don't want to risk messing up as i see posts from people suffering from kernel upgrade mania.

---

### Post by Bashing-om on 2014-04-26
stephenbbb; OK,

My concerns are alleviated.
On the troubled box what results from terminal code:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade #this invokes apt's smart mode to deal with that kernel upgrade#

```

Now if HES is not enabled on that box, you will not upgrade to the later release kernels above the 3.2 series kernels.

[INDENT][INDENT]still try'n to help
[/INDENT][/INDENT]

---

