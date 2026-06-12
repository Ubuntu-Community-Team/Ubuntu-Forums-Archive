---
title: "Can't install Lubuntu on old Sempron based machine / mint will install though"
date: 2013-03-13
forum: Installation &amp; Upgrades
---

### Post by strickja on 2013-03-13
I am trying to repurpose and old machine and cannot , despite hours of trying diff install param , get lubuntu 12.10, or 12.04 to install; the perplexing thing is Peppermint 3.0 will install, but don't care for the distro and would prefer to run lubuntu on the machine - intended purpose will be a backup and/or cloud server , basically just sit and run files up and down an ethernet connection to a my CM -  

It is an old emachine, sempron based -
description: Desktop Computer
    version: SYS-xxxxxx
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: K8M-800M
       vendor: First International Computer, Inc.
       physical id: 0
       version: PCB 2.x
       serial: C235A39527
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG
          date: 07/26/2005
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Sempron(tm) Processor 3300+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.12.2
          slot: Socket 940
          size: 2GHz
          capacity: 3400MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm cpufreq
      

I have tried toggling every combination of install parameters from the live CD; have checked memory ( was at 1.5G, ck fine, took out 1G board, still memtest fine); have three diff DVD with distro that have all been used to install successfully on two other machines 

Most combinations just freeze during install;   those that progress run until they begin spewing SQASHFS error - have searched and all advice seems to be bad disc (not the case) or bad memory (memtest passes) - so looking for other ideas - any help would be much appreciated

---

