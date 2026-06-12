---
title: "Live system doesn't work"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by clouder on 2011-09-29
Hello community,
I have some problems with my Ubuntu Live Stick.
When my laptop starts to boot I don't get the purple screen for choosing an option but I get the Grub Bootloader of the Live System.
There are three options:
* Trying Ubuntu
* Installing Ubuntu
* Check Hard Drives

Selecting all of them has the same result:
The LED light of my USB stick blinks for a few seconds, the screen turns black and nothing happens.

Is there any solution to fix this?

My hardware specs are:
> 
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2934MiB
     *-cpu
          product: Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
     *-pci
          description: Host bridge
          product: Sandy Bridge DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Sandy Bridge Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:41 memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:4000(size=64)
        *-communication
             description: Communication controller
             product: Cougar Point HECI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:16 memory:e1705000-e170500f
        *-usb:0
             description: USB Controller
             product: Cougar Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:e170a000-e170a3ff
        *-multimedia
             description: Audio device
             product: Cougar Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:42 memory:e1700000-e1703fff
        *-pci:0
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:1
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:e1600000-e16fffff


---

### Post by dino99 on 2011-09-29
how i make installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

maybe you need to add boot option due to your chipset:

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by clouder on 2011-09-29
I already tried out no acpi and nomodeset, no solution.
But the odd fact is the purpel screen doesnt show up.
The Live USB System actually works, I've checked it with another PC.
I'm wondering why. As you can see this laptop has many Intel chips.

Edit:
I've recorded my power up because before Grub shows up a short message is shown.
> 
error: "Prefix" is not set.


Maybe this could help.

---

### Post by dino99 on 2011-09-29
from the grub menu (hold "shift" key down at bios end process to see the menu), you can either:

- edit the boot line to remove "quiet splash" to let you know the comments while loading

- select "recovery mode" (2d line) then select "repair package"

---

### Post by clouder on 2011-09-29
The clue of pressing "Shift" already told me a guy on IRC.
But it has no effect... also GRUB starts.

Edit:
Here I uploaded what happened (sorry about the bad quality, the codec sucked):
[http://www.youtube.com/watch?v=IkJUPPxwQOU](http://www.youtube.com/watch?v=IkJUPPxwQOU)

---

