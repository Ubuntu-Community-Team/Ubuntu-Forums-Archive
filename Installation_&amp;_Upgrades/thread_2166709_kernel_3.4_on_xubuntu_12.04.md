---
title: "kernel 3.4 on xubuntu 12.04?"
date: 2013-08-10
forum: Installation &amp; Upgrades
---

### Post by al.adab on 2013-08-10
hello

i'm running Xubuntu 12.04 on an old Thinkpad T42 that freezes randomly and becomes totally unresponsive (keyboard, mouse, no chance on a ctrl-alt-f1 or the like). The kernel version is 

[I]~$ uname -a
Linux T42 3.2.0-51-generic #77-Ubuntu SMP Wed Jul 24 20:21:10 UTC 2013 i686 i686 i386 GNU/Linux[/I]

would it make sense to try and install the kernel 3.4 to see if it solves the issue? if it would, could you please advise on what exactly i should do (from terminal, i suppose?). thanks


PS: the machine specs (hopefully the relevant ones): 

[I]~$ lshw
WARNING: you should run this program as super-user.
t42                       
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1015MiB
     *-cpu
          product: Intel(R) Pentium(R) M processor 1.70GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.13.6
          size: 1700MHz
          capacity: 1700MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 cpufreq
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:d0000000-dfffffff
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=4096) memory:c0100000-c01fffff memory:e0000000-e7ffffff
           *-display
                description: VGA compatible controller
                product: RV350 [Mobility Radeon 9600 M10]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:11 memory:e0000000-e7ffffff ioport:3000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff[/I]

---

### Post by al.adab on 2013-08-12
bump? am i not asking the right question? :)

---

### Post by matt_symes on 2013-08-12
Hi

You could install the saucy (3.8), raring (3.6) or quantal (3.4) Hardware enablement stack and see if one of them helps.

They support newer hardware.

Have a read of this.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

If you still not sure of the exact commands to type then post back and someone will post the terminal commands for you.

Kind regards

---

### Post by Doug S on 2013-08-12
To try a different kernel:
First make sure there is enough room for another kernel on /boot, and if not perhaps delete some older kernel(s) that are not needed anymore.
Then get whatever kernel you want to try from the [kernel ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") and put it to some directory. For example 3.11rc2, from the directory:```
sudo dpkg -i linux-headers-3.11.0-031100rc2_3.11.0-031100rc2.201307211535_all.deb
sudo dpkg -i linux-headers-3.11.0-031100rc2-generic_3.11.0-031100rc2.201307211535_amd64.deb
sudo dpkg -i linux-image-3.11.0-031100rc2-generic_3.11.0-031100rc2.201307211535_amd64.deb
```Then re-boot, and you may or may not need to select the kernel from the grub menu.
Note: I have had troubles with updates in the past when running a different kernel, so I never do updates while running the not standard kernel.

Also have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2160015").

---

