---
title: "Ubuntu Server 14.04 - Won't boot unless in recovery mode?"
date: 2014-06-16
forum: Installation &amp; Upgrades
---

### Post by tarmac515 on 2014-06-16
Hi,


I have problems with a new system i'm trying to install Ubuntu Server 14.4 onto, I have been unable to install anything without a recuring boot issues, whereby I get boot splash, rolling text, spash, boot in recovery mode etc etc.
------
System spec:
AMD A6-6400K APU dual core cpu
64bit Ubuntu 14.04 Server
Memory 3GB showing - 4gb stick - so assuming 1gb has been allocated to graphics
graphics VESA VST
------
Booted ubuntu server 14.04, installed just the core system
then ran:
sudo apt-get install xorg gnome-core gnome-system-tools gnome-app-install


to install gnome desktop


Then rebooted and ran into issues again... Splash, scrolling text, spash, boot in recovery mode


Then boots fine,


So i'm assuming its a graphics issue as I swapped out most of the hardware(!).


Here is the output from:
lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex [1022:1410]
00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) I/O Memory Management Unit [1022:1419]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8470D] [1002:9996]
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller [1002:9902]
00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port [1022:1414]
00:10.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7814] (rev 09)
00:10.1 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7814] (rev 09)
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7801] (rev 40)
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:780b] (rev 16)
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:780e] (rev 11)
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge [1022:780f] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7809] (rev 11)
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0 [1022:1400]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1 [1022:1401]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2 [1022:1402]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3 [1022:1403]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4 [1022:1404]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5 [1022:1405]
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)


Under Additional drivers
currently using AMD Radeon HD 8470D driver
recommended
-------


I tried to switch to xorg, but I can't get it to restart without recovery so it won't update?


Any suggestions?

---

### Post by tarmac515 on 2014-06-16
ps: I've already run the usual software updates to check everything is upto date

---

### Post by mastablasta on 2014-06-17
what are you trying to do? why did you install server and then gnome desktop?

by the way lightdm or GDM would be good to have.

---

### Post by tarmac515 on 2014-06-17
Hi mastablasta, thanks for your post - ok a little background:

I'm hoping to use this new built pc as a home server to serve up dlna music, files, photos etc to my home network. As much to learn a little about linux and networking as anything else (I have run ubuntu and debian machines for fives years+) 
I have tried to install standard Ubuntu with unity, Debian (this worked ok ish) and ubuntu home server - detailed above.
Really I just want to get to the bottom of what is causing the boot issues so I can address it. As its a home server having a desktop GUI would be handy but not essential as I can SSH or run ISPConfig. But I would like to isolate the issue - any ideas?

Thanks for the lightdm link - looks far more appropriate very lightweight.
Cheers

---

### Post by Bucky Ball on 2014-06-17
There is also XDM for a login manager. Are you specifically after Gnome and a server? If not, why not a minimal install? Just the kernel so you'll get possibly lighter again. I only ever go for that, then something like:

```
sudo apt-get install xorg gdm xfce4 xfwm4 synaptic 
```

... reboot, and take it from there once I'm at the desktop. Launch Synaptic and install the few things I want/need.

Once you get a basic system running you can make it want you want, including a server with gnome desktop. ;)

---

### Post by tarmac515 on 2014-06-17
Hi Bucky Ball thanks for your post, no i'm not after gnome and a server - just a server with a gui (for now anyhow may lose it later). The issue is that both unity and gnome have caused the endless cycle boot issues (detailed above), debian with lxde - did boot but with error messages. Really I just want to establish what is the root of the boot issues - i'm assuming its graphics/software as i've already changed: PSU, RAM, CPU cooler!

Will take a look at XDM now,
Cheers

---

### Post by Bucky Ball on 2014-06-17
Yes, a login manager might help. I presume the gnome packages you installed include a windows manager also? xfwm4 is light if not. There are others.

PS: Try a login manager before we head down the graphics issue path. ;)

---

### Post by tarmac515 on 2014-06-17
OK, I will try a different login manager and see if that helps. 
[COLOR=#000000]OK so if I run 
[/COLOR]```
sudo apt-get install xdm
```

[COLOR=#000000]to install xdm and go from there

[/COLOR]

To install Gnome I just ran so:
[COLOR=#000000]```
sudo apt-get install xorg gnome-core gnome-system-tools gnome-app-install[/COLOR][COLOR=#000000]
```[/COLOR][COLOR=#000000]

[/COLOR][COLOR=#000000]

[/COLOR]

---

### Post by mastablasta on 2014-06-17
> **tarmac515 said:**
> just a server with a gui (for now anyhow may lose it later). 

have a look at Zentyal (Ubuntu based - it has free community version) or Open Media Vault (Debian based) - these are servers with a GUI - you connect to them via browser form another computer.
you can also install webmin (a similar interface for server admin via GUI&browser)

----

it does seem like a GPU issue. however it could be possible you are missing a component. you could install a metapackage such a Xubuntu-desktop or Ubuntu-desktop on it.

there are system logs in /var/log

you should check the boto logs to see why it is not booting. you may need to use nano or something ot check the logs.

otherwise a how to for Ubutnu minimal install: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by tarmac515 on 2014-06-17
Hi mastablasta,  
I have downloaded open media vault and that failed to boot from usb using unetbootin  (same software worked ok when booted ubuntu server and debian), I hadn't hears of Zentyal so I will take a look now.

---
OK will take a look at the boot logs later today to see if that sheds any light on it.
I don't really need graphics but I do need it to boot and it would be nice to fix it all the same!

---

### Post by Bucky Ball on 2014-06-17
> **mastablasta said:**
>  you could install a metapackage such a Xubuntu-desktop or Ubuntu-desktop on it.

... and load it with bloat a server doesn't need. Don't go there unless you actually have to. If you're heading down that path don't bother with all this server fiddling at all and just install Xubuntu or Ubuntu because that is what you will be doing if you install either *buntu-desktop. 

A lightweight desktop environment is all you should need, not the whole shebang. :-k

Install XDM or GDM, reboot and report back as to whether you can log in okay or not, please. That is what I have been asking you to do for a post or two. If that works, problem solved simply. If not, dig and tweak at will. ;)

---

### Post by mastablasta on 2014-06-17
Quite possible they do not have a live version, although it should boot (to install it).

i read a few people had issues wiht unetbootin lately. i usually try various other options pendrive Linux, yumi, startupdisk creator...

or it could be that it just doesn't boot.

by the way does the computer boot if you use any of the boot parameters: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

i have a PC that doesn't want to boto at all into live 14.04. i can not figure out what si wrong,. however when i uprgaded it form 12.04 to 14.04 it booted. strange - and i think it has something to do with old ATI card.  you say oyu have porprietary drivers installed - did you install them via additonal drivers applicaiton? hmm..it could be they are not configured. see how it's done via command line (with various configuraiton steps) as well as some other troubleshooting tips: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

i know A4 works well i am not sure how A6 Works.... for A10 APU some reported issues.

---

### Post by tarmac515 on 2014-06-18
Ok so a couple of updates:

I installed XDM by running
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install xdm[/FONT][/COLOR]
```
However same issues at next boot - got to scrolling text of boot, then bios splash, then enter recovery mode and boots.


Here is the result from:

result from dsmg:
```
Attaching: [tmux____1]
[   31.061824] Bluetooth: RFCOMM TTY layer initialized
[   31.061837] Bluetooth: RFCOMM socket layer initialized
[   31.061843] Bluetooth: RFCOMM ver 1.11
[   31.128412] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.128417] Bluetooth: BNEP filters: protocol multicast
[   31.128426] Bluetooth: BNEP socket layer initialized
[   31.198275] type=1400 audit(1403071787.197:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1105 comm="apparmor_parser"
[   31.198284] type=1400 audit(1403071787.197:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=1105 comm="apparmor_parser"
[   31.198614] type=1400 audit(1403071787.197:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1105 comm="apparmor_parser"
[   31.207079] type=1400 audit(1403071787.205:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=1169 comm="apparmor_parser"
[   31.207087] type=1400 audit(1403071787.205:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-cli[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 8984 pages used for memmap
[    0.000000]   DMA32 zone: 574938 pages, LIFO batch:31
[    0.000000]   Normal zone: 4032 pages used for memmap
[    0.000000]   Normal zone: 258048 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x14] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x15] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10228210 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x8ced3000-0x8cf02fff]
[    0.000000] PM: Registered nosave memory: [mem 0x8d1c1000-0x8d27afff]
[    0.000000] PM: Registered nosave memory: [mem 0x8d27b000-0x8e23ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x8e241000-0x8e446fff]
[    0.000000] PM: Registered nosave memory: [mem 0x8e882000-0x8eff2fff]
[    0.000000] PM: Registered nosave memory: [mem 0x8f000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed3ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed40000-0xfed44fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed45000-0xfed7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed8ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0x8f000000-0xfebfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88013ec00000 s86336 r8192 d24256 u524288
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 823882
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic root=UUID=ab499b2c-a763-4adb-b6e0-33de877e153e ro recovery nomodeset
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 84000000
[    0.000000] PM: Registered nosave memory: [mem 0x84000000-0x87ffffff]
[    0.000000] Memory: 3127200K/3347932K available (7356K kernel code, 1142K rwdata, 3396K rodata, 1332K init, 1440K bss, 220732K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]  RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000]  Offload RCU callbacks from all CPUs
[    0.000000]  Offload RCU callbacks from CPUs: 0-3.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 13631488 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration failed
[    0.008000] tsc: PIT calibration matches HPET. 1 loops
[    0.008000] tsc: Detected 3892.864 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 7785.72 BogoMIPS (lpj=15571456)
[    0.000071] pid_max: default: 32768 minimum: 301
[    0.000128] Security Framework initialized
[    0.000182] AppArmor: AppArmor initialized
[    0.000215] Yama: becoming mindful.
[    0.000544] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001879] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002506] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.002563] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.002802] Initializing cgroup subsys memory
[    0.002855] Initializing cgroup subsys devices
[    0.002889] Initializing cgroup subsys freezer
[    0.002924] Initializing cgroup subsys blkio
[    0.002957] Initializing cgroup subsys perf_event
[    0.002991] Initializing cgroup subsys hugetlb
[    0.003044] tseg: 008f000000
[    0.003046] CPU: Physical Processor ID: 0
[    0.003079] CPU: Processor Core ID: 0
[    0.003113] mce: CPU supports 7 MCE banks
[    0.003157] Last level iTLB entries: 4KB 512, 2MB 1024, 4MB 512
[    0.003157] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 512
[    0.003157] tlb_flushall_shift: 5
[    0.003287] Freeing SMP alternatives memory: 32K (ffffffff81e6c000 - ffffffff81e74000)
[    0.004068] ACPI: Core revision 20131115
[    0.007184] ACPI: All ACPI Tables successfully acquired
[    0.016507] ftrace: allocating 28463 entries in 112 pages
[    0.026292] [Firmware Bug]: AMD-Vi: IOAPIC[0] not in IVRS table
[    0.026374] [Firmware Bug]: AMD-Vi: No southbridge IOAPIC found
[    0.026407] AMD-Vi: Disabling interrupt remapping
[    0.026830] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067815] smpboot: CPU0: AMD A6-6400K APU with Radeon(tm) HD Graphics (fam: 15, model: 13, stepping: 01)
[    0.174483] Performance Events: Fam15h core perfctr, AMD PMU driver.
[    0.174621] ... version:                0
[    0.174654] ... bit width:              48
[    0.174688] ... generic registers:      6
[    0.174721] ... value mask:             0000ffffffffffff
[    0.174755] ... max period:             00007fffffffffff
[    0.174787] ... fixed-purpose events:   0
[    0.174819] ... event mask:             000000000000003f
[    0.176246] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.176412] x86: Booting SMP configuration:
[    0.176459] .... node  #0, CPUs:      #1
[    0.191168] x86: Booted up 1 node, 2 CPUs
[    0.191283] smpboot: Total of 2 processors activated (15571.45 BogoMIPS)
[    0.191720] devtmpfs: initialized
[    0.233397] pci 0000:01:00.0: supports D1 D2
[    0.233399] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.243216] pci 0000:00:04.0: PCI bridge to [bus 01]
[    0.243311] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.243314] pci 0000:00:04.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.243317] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.243406] pci 0000:00:14.4: PCI bridge to [bus 02] (subtractive decode)
[    0.243448] pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    0.243449] pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    0.243451] pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
[    0.243452] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.243454] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.243455] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.243457] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.244180] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 5 7 10 *11 14 15)
[    0.244543] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 5 7 *10 11 14 15)
[    0.244904] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 5 7 10 *11 14 15)
[    0.245268] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 5 7 *10 11 14 15)
[    0.245622] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 5 7 10 11 14 15) *0
[    0.245987] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 5 7 10 11 14 15) *0
[    0.246354] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 5 7 10 11 14 15) *0
[    0.246719] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 5 7 10 11 14 15) *0
[    0.247285] ACPI: \_SB_.PCI0: notify handler is installed
[    0.247325] Found 1 acpi root devices
[    0.247444] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    0.247496] vgaarb: loaded
[    0.247528] vgaarb: bridge control possible 0000:00:01.0
[    0.247715] SCSI subsystem initialized
[    0.247817] libata version 3.00 loaded.
[    0.247835] ACPI: bus type USB registered
[    0.247893] usbcore: registered new interface driver usbfs
[    0.247933] usbcore: registered new interface driver hub
[    0.247992] usbcore: registered new device driver usb
[    0.248126] PCI: Using ACPI for IRQ routing
[    0.255236] PCI: pci_cache_line_size set to 64 bytes
[    0.255284] e820: reserve RAM buffer [mem 0x0009e800-0x0009ffff]
[    0.255286] e820: reserve RAM buffer [mem 0x8ced3000-0x8fffffff]
[    0.255288] e820: reserve RAM buffer [mem 0x8d1c1000-0x8fffffff]
[    0.255289] e820: reserve RAM buffer [mem 0x8e241000-0x8fffffff]
[    0.255290] e820: reserve RAM buffer [mem 0x8e882000-0x8fffffff]
[    0.255291] e820: reserve RAM buffer [mem 0x8f000000-0x8fffffff]
[    0.255293] e820: reserve RAM buffer [mem 0x13f000000-0x13fffffff]
[    0.255370] NetLabel: Initializing
[    0.255404] NetLabel:  domain hash size = 128
[    0.255436] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.255481] NetLabel:  unlabeled traffic allowed by default
[    0.255589] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.255740] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.257822] Switched to clocksource hpet
[    0.263779] AppArmor: AppArmor Filesystem Enabled
[    0.263895] pnp: PnP ACPI init
[    0.263940] ACPI: bus type PNP registered
[    0.264101] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.264151] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.264223] system 00:01: [mem 0x90000000-0xbfffffff] has been reserved
[    0.264270] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.264340] system 00:02: [mem 0xfeb80000-0xfebfffff] could not be reserved
[    0.264389] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.264586] system 00:03: [io  0x0295-0x0296] has been reserved
[    0.264621] system 00:03: [io  0x0778-0x077f] has been reserved
[    0.264655] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.264886] pnp 00:04: [dma 0 disabled]
[    0.264926] pnp 00:04: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.265203] pnp 00:05: [dma 3]
[    0.265286] pnp 00:05: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.265318] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.265327] pnp 00:07: [dma 4]
[    0.265344] pnp 00:07: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.265382] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.265402] pnp 00:09: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.265520] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.265556] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.265580] pnp 00:0b: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.265890] system 00:0c: [io  0x04d0-0x04d1] has been reserved
[    0.265936] system 00:0c: [io  0x040b] has been reserved
[    0.265970] system 00:0c: [io  0x04d6] has been reserved
[    0.266004] system 00:0c: [io  0x0c00-0x0c01] has been reserved
[    0.266038] system 00:0c: [io  0x0c14] has been reserved
[    0.266072] system 00:0c: [io  0x0c50-0x0c51] has been reserved
[    0.266107] system 00:0c: [io  0x0c52] has been reserved
[    0.266140] system 00:0c: [io  0x0c6c] has been reserved
[    0.266174] system 00:0c: [io  0x0c6f] has been reserved
[    0.266207] system 00:0c: [io  0x0cd0-0x0cd1] has been reserved
[    0.266242] system 00:0c: [io  0x0cd2-0x0cd3] has been reserved
[    0.266274] system 00:0c: [io  0x0cd4-0x0cd5] has been reserved
[    0.266308] system 00:0c: [io  0x0cd6-0x0cd7] has been reserved
[    0.266342] system 00:0c: [io  0x0cd8-0x0cdf] has been reserved
[    0.266376] system 00:0c: [io  0x0800-0x089f] could not be reserved
[    0.266409] system 00:0c: [io  0x0b20-0x0b3f] has been reserved
[    0.266443] system 00:0c: [io  0x0900-0x090f] has been reserved
[    0.266477] system 00:0c: [io  0x0910-0x091f] has been reserved
[    0.266511] system 00:0c: [io  0xfe00-0xfefe] has been reserved
[    0.266546] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.266580] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.266614] system 00:0c: [mem 0xfed80000-0xfed8ffff] has been reserved
[    0.266649] system 00:0c: [mem 0xfed61000-0xfed70fff] has been reserved
[    0.266684] system 00:0c: [mem 0xfec10000-0xfec10fff] has been reserved
[    0.266718] system 00:0c: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.266751] system 00:0c: [mem 0xff000000-0xffffffff] has been reserved
[    0.266784] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.267028] pnp 00:0d: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.267033] pnp: PnP ACPI: found 14 devices
[    0.267067] ACPI: bus type PNP unregistered
[    0.273594] pci 0000:00:04.0: PCI bridge to [bus 01]
[    0.273629] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.273664] pci 0000:00:04.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.273699] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.273737] pci 0000:00:14.4: PCI bridge to [bus 02]
[    0.273779] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.273781] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.273783] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
[    0.273784] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
[    0.273786] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
[    0.273787] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
[    0.273789] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xffffffff]
[    0.273790] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.273791] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.273793] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.273795] pci_bus 0000:02: resource 4 [io  0x0000-0x03af]
[    0.273796] pci_bus 0000:02: resource 5 [io  0x03e0-0x0cf7]
[    0.273797] pci_bus 0000:02: resource 6 [io  0x03b0-0x03df]
[    0.273799] pci_bus 0000:02: resource 7 [io  0x0d00-0xffff]
[    0.273800] pci_bus 0000:02: resource 8 [mem 0x000a0000-0x000bffff]
[    0.273801] pci_bus 0000:02: resource 9 [mem 0x000c0000-0x000dffff]
[    0.273803] pci_bus 0000:02: resource 10 [mem 0xc0000000-0xffffffff]
[    1.106988] usb usb6: Manufacturer: Linux 3.13.0-29-generic xhci_hcd
[    1.107021] usb usb6: SerialNumber: 0000:00:10.0
[    1.107137] hub 6-0:1.0: USB hub found
[    1.107187] hub 6-0:1.0: 2 ports detected
[    1.107279] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.107313] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 7
[    1.110212] usb usb7: New USB device found, idVendor=1d6b, idProduct=0003
[    1.110245] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.110282] usb usb7: Product: xHCI Host Controller
[    1.110316] usb usb7: Manufacturer: Linux 3.13.0-29-generic xhci_hcd
[    1.110350] usb usb7: SerialNumber: 0000:00:10.0
[    1.110461] hub 7-0:1.0: USB hub found
[    1.110508] hub 7-0:1.0: 2 ports detected
[    1.117960] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.118003] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 8
[    1.118252] xhci_hcd 0000:00:10.1: irq 44 for MSI/MSI-X
[    1.118257] xhci_hcd 0000:00:10.1: irq 45 for MSI/MSI-X
[    1.118261] xhci_hcd 0000:00:10.1: irq 46 for MSI/MSI-X
[    1.118353] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    1.118387] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.118424] usb usb8: Product: xHCI Host Controller
[    1.118457] usb usb8: Manufacturer: Linux 3.13.0-29-generic xhci_hcd
[    1.118492] usb usb8: SerialNumber: 0000:00:10.1
[    1.118637] hub 8-0:1.0: USB hub found
[    1.118689] hub 8-0:1.0: 2 ports detected
[    1.118788] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.118823] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 9
[    1.121679] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    1.121713] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.121751] usb usb9: Product: xHCI Host Controller
[    1.121785] usb usb9: Manufacturer: Linux 3.13.0-29-generic xhci_hcd
[    1.121819] usb usb9: SerialNumber: 0000:00:10.1
[    1.121926] hub 9-0:1.0: USB hub found
[    1.121977] hub 9-0:1.0: 2 ports detected
[    1.129848] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.130354] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.130394] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.130561] mousedev: PS/2 mouse device common for all mice
[    1.130730] rtc_cmos 00:08: RTC can wake from S4
[    1.130862] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.130918] rtc_cmos 00:08: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.132187] device-mapper: uevent: version 1.0.3
[    1.132295] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.132336] ledtrig-cpu: registered to indicate activity on CPUs
[    1.132447] TCP: cubic registered
[    1.132565] NET: Registered protocol family 10
[    1.132751] NET: Registered protocol family 17
[    1.132791] Key type dns_resolver registered
[    1.133088] Loading compiled-in X.509 certificates
[    1.133916] Loaded X.509 cert 'Magrathea: Glacier signing key: 6602cb36f1313bea01c4bda96567cfa723c970d8'
[    1.133965] registered taskstats version 1
[    1.136252] Key type trusted registered
[    1.138284] Key type encrypted registered
[    1.140210] AppArmor: AppArmor sha1 policy hashing enabled
[    1.140248] IMA: No TPM chip found, activating TPM-bypass!
[    1.140511] regulator-dummy: disabling
[    1.140585]   Magic number: 2:602:165
[    1.140706] rtc_cmos 00:08: setting system clock to 2014-06-18 06:09:16 UTC (1403071756)
[    1.140851] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.140983] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.141017] EDD information not available.
[    1.141090] PM: Hibernation image not present or could not be loaded.
[    1.142322] Freeing unused kernel memory: 1332K (ffffffff81d1f000 - ffffffff81e6c000)
[    1.142407] Write protecting the kernel read-only data: 12288k
[    1.145151] Freeing unused kernel memory: 824K (ffff880001732000 - ffff880001800000)
[    1.147723] Freeing unused kernel memory: 700K (ffff880001b51000 - ffff880001c00000)
[    1.161565] systemd-udevd[104]: starting version 204
[    1.185976] ahci 0000:00:11.0: version 3.0
[    1.186189] ahci 0000:00:11.0: irq 47 for MSI/MSI-X
[    1.186247] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    1.186289] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.186924] scsi0 : ahci
[    1.187080] scsi1 : ahci
[    1.187155] ata1: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51100 irq 47
[    1.187196] ata2: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51180 irq 47
[    1.201678] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.201725] r8169 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.210652] r8169 0000:01:00.0: irq 48 for MSI/MSI-X
[    1.211208] r8169 0000:01:00.0 eth0: RTL8168g/8111g at 0xffffc9000067e000, 44:8a:5b:61:39:be, XID 0c000800 IRQ 48
[    1.211253] r8169 0000:01:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.429740] usb 8-2: new full-speed USB device number 2 using xhci_hcd
[    1.487701] usb 8-2: New USB device found, idVendor=046d, idProduct=c52e
[    1.487740] usb 8-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.487774] usb 8-2: Product: USB Receiver
[    1.487807] usb 8-2: Manufacturer: Logitech
[    1.498701] hidraw: raw HID events driver (C) Jiri Kosina
[    1.540011] usbcore: registered new interface driver usbhid
[    1.540050] usbhid: USB HID core driver
[    1.541653] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:10.1/usb8/8-2/8-2:1.0/input/input5
[    1.541806] hid-generic 0003:046D:C52E.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:10.1-2/input0
[    1.542322] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:10.1/usb8/8-2/8-2:1.1/input/input6
[    1.542579] hid-generic 0003:046D:C52E.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:10.1-2/input1
[    1.677676] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.677734] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.678752] ata1.00: ATA-8: HGST HTS545050A7E380, GG2OAC90, max UDMA/133
[    1.678790] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.679109] ata2.00: ATA-8: Hitachi HDS721010CLA332, JP4OA39C, max UDMA/133
[    1.679145] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.679813] ata1.00: configured for UDMA/133
[    1.679990] scsi 0:0:0:0: Direct-Access     ATA      HGST HTS545050A7 GG2O PQ: 0 ANSI: 5
[    1.680204] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.680244] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.680308] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.680368] sd 0:0:0:0: [sda] Write Protect is off
[    1.680404] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.680430] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.680663] ata2.00: configured for UDMA/133
[    1.680796] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDS72101 JP4O PQ: 0 ANSI: 5
[    1.680968] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.680985] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.681081] sd 1:0:0:0: [sdb] Write Protect is off
[    1.681118] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.681142] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.686994]  sdb: sdb1
[    1.687306] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.748292]  sda: sda1 sda2 < sda5 >
[    1.748673] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.853620] tsc: Refined TSC clocksource calibration: 3892.726 MHz
[    2.117833] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.117917] EXT4-fs (sda1): write access will be enabled during recovery
[    2.415421] EXT4-fs (sda1): recovery complete
[    2.423246] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.853484] Switched to clocksource tsc
[    3.138667] random: nonblocking pool is initialized
[    4.913229] systemd-udevd[216]: starting version 204
[   31.061824] Bluetooth: RFCOMM TTY layer initialized
[   31.061837] Bluetooth: RFCOMM socket layer initialized
[   31.061843] Bluetooth: RFCOMM ver 1.11
[   31.128412] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.128417] Bluetooth: BNEP filters: protocol multicast
[   31.128426] Bluetooth: BNEP socket layer initialized
[   31.198275] type=1400 audit(1403071787.197:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1105 comm="apparmor_parser"
[   31.198284] type=1400 audit(1403071787.197:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=1105 comm="apparmor_parser"
[   31.198614] type=1400 audit(1403071787.197:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1105 comm="apparmor_parser"
[   31.207079] type=1400 audit(1403071787.205:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=1169 comm="apparmor_parser"
[   31.207087] type=1400 audit(1403071787.205:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1169 comm="apparmor_parser"
[   31.207092] type=1400 audit(1403071787.205:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1169 comm="apparmor_parser"
[   31.207600] type=1400 audit(1403071787.209:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1169 comm="apparmor_parser"
[   31.207607] type=1400 audit(1403071787.209:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1169 comm="apparmor_parser"
[   31.207802] type=1400 audit(1403071787.209:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1169 comm="apparmor_parser"
[   31.214513] type=1400 audit(1403071787.213:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=1170 comm="apparmor_parser"
[   31.245620] init: cups main process (1167) killed by HUP signal
[   31.245635] init: cups main process ended, respawning
[   39.328485] audit_printk_skb: 123 callbacks suppressed
[   39.328490] type=1400 audit(1403071795.329:53): apparmor="DENIED" operation="mkdir" profile="/usr/lib/telepathy/mission-control-5" name="/var/lib/gdm/.config/libaccounts-glib/" pid=1721 comm="mission-control" requested_mask="c" denied_mask="c" fsuid=111 ouid=111
[   39.330117] type=1400 audit(1403071795.333:54): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/etc/dconf/profile/gdm" pid=1721 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=111 ouid=0
[   61.281085] type=1400 audit(1403071817.285:55): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2262 comm="apparmor_parser"
[   61.281093] type=1400 audit(1403071817.285:56): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2262 comm="apparmor_parser"
[   61.281511] type=1400 audit(1403071817.289:57): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2262 comm="apparmor_parser"
[  329.765741] systemd-hostnamed[4808]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!



```

---

### Post by tarmac515 on 2014-06-18
Have checked the AMD website and the recommended driver is the [AMD Catalyst&#8482; 14.4 Proprietary Linux x86 Display Driver]("http://www2.ati.com/drivers/linux/amd-catalyst-14-4-rev2-linux-x86-x86-64-may6.zip") 

Which having checked on the additional drivers tab - I assume is what I'm running:
AMD Richland Radeon 8470D

I can select the open source option and mark it for install at the next boot - but as it doesn't reboot correctly it will not install. I'm starting to think an easy way to find out if its graphics is to buy a cheap nvidia card and install it?

---

### Post by mastablasta on 2014-06-19
no the easiest way to see what is going wrong is to download a desktop version (14.04 64 bit) burn it to a live CD or USB and then boot from it into live system. now if that works out OK. it means you installed something in a wrong way. hard to say what was that since wasn't present at the install.

Server image is not ment to run desktop. although one can install desktop to it. server image is ment to run on computers (servers) with no monitors attached. so i am not sure but maybe some packages are missing or some step is not done.

you could try and remove drivers and then reinstall manually the latest version: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by tarmac515 on 2014-07-16
OK, an update:

I gave up with ubuntu server and managed to install ubuntu desktop. It was a graphics issue. In ubuntu server with the GUI you can change the graphics drivers but it needs to reboot to change them - as it could not reboot it never completed. Under vanilla desktop it just updates immediately, so I changed the drivers to i think open source and its been fine ever since! Not quite the slim server I was hoping for but it does the trick and is running plex really well. 

Next time its back to intel! (It seems to me that my oldish 2.8ghz pentium chip is quicker that this 3.9ghz chip)

thanks for all the help it was really appreciated!

---

### Post by Bucky Ball on 2014-07-16
Good news. Please mark as solved to help others. Enjoy. ;)

---

### Post by tarmac515 on 2014-07-16
Done, thanks again!

---

