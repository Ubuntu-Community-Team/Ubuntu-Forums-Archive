---
title: "Hardy Boots to BusyBox Prompt?"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by DaddyUnit on 2008-06-25
I've got a several-years-old AMD Athlon that I loaded Gutsy on a few months ago. I recently used the upgrade manager to upgrade to Hardy and after the final installation reboot, the system boots to a command prompt that looks like:

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)
```

When I tried to reload Hardy from disk, the installation would proceed normally until it got to the disk partition part at which point it would give me no options for partitioning the disk (no items in the dialog box) and only a back or cancel button.

So, I reloaded Gutsy again then tried to upgrade to Hardy again and got exactly the same result.

Any ideas on what I can try to get Hardy to work on my old box?

Thanks.

---

### Post by Pumalite on 2008-06-25
Post your specs.
Or:
lshw

---

### Post by DaddyUnit on 2008-06-25
Thanks for responding.

ubuntu@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MB
     *-cpu
          product: AMD-K7(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.1.2
          size: 550MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat mmx syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: AMD-751 [Irongate] System Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 23
          width: 32 bits
          clock: 33MHz
          configuration: latency=64
        *-pci
             description: PCI bridge
             product: AMD-751 [Irongate] AGP Bridge
             vendor: Advanced Micro Devices [AMD]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
        *-display
             description: VGA compatible controller
             product: NV34 [GeForce FX 5500]
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list
             configuration: latency=64 maxlatency=1 mingnt=5
        *-network
             description: Ethernet interface
             product: NC100 Network Everywhere Fast Ethernet 10/100
             vendor: ADMtek
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 11
             serial: 00:04:5a:86:ca:24
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.7 latency=64 maxlatency=128 mingnt=64 module=tulip multicast=yes
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 14
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=VIA_IDE latency=32 module=via82cxxx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: WDC WD600BB-32CCB0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 55GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   product: 52X32COMBO
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 695MB
                   capabilities: packet
              *-cdrom:1
                   product: SONY CD-RW CRX140E
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet
        *-usb
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-serial UNCLAIMED
             description: SMBus
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@0000:00:07.4
             version: 10
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: ES1371 [AudioPCI-97]
             vendor: Ensoniq
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ENS1371 latency=64 maxlatency=128 mingnt=12 module=snd_ens1371

---

### Post by Pumalite on 2008-06-25
It seems fine. Download Ubuntu 8.4 drom here:
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
Follow this:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, burn at 4x or less, clean the lens in your burner.
If you still have trouble; post back.

---

