---
title: "The screen and keyboard don't respond when booting from kernel 3.13 after upgrading"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by icoming on 2014-04-24
Hello,

I upgrade my desktop from Ubuntu 12.04 to 14.04 recently. After upgrade, Ubuntu has awful display in both GNOME and KDE. The screen can't refresh itself fast enough in KDE and it doesn't display the menu properly in GNOME.

I figured that it might be caused by the old kernel. For some reason, the kernel remains 3.2.0. So I install kernel 3.13.0-24 manually. The machine can boot from kernel 3.13.0-24 and display the gdm login interface. However, the screen has very low resolution and freezes after entering that interface. The keyboard does not respond either. However, I can login to the machine with SSH. I checked dmesg and /var/log/Xorg.0.log and I couldn't see many error messages.

I'm wondering how I should debug in this situation?

Thanks,
Da

---

### Post by icoming on 2014-04-25
If I boot the machine with kernel 3.2.0-35, dmesg has the following error:
[ 2248.366616] radeon 0000:01:00.0: texture bo too small (2554 20 26 0 -> 245760 have 204800)
[ 2248.366623] radeon 0000:01:00.0: alignments 2560 128 8 512
[ 2248.366627] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !

Can anyone tell me what this error mean?
This kernel works fine in Ubuntu 12.04.

Thanks,
Da

---

### Post by Bashing-om on 2014-04-25
icoming; Hi !

Mind you I may not be the sharpest tack in this box of tacks, But, If it were me in this situation I would:
Make sure the system is fully updated:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade # apt's smart mode - does not release upgrade##

```
Then see what the graphics situation is:
To see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga
ubuntu-drivers devices
ubuntu-drivers list
##these commands will take a while to run##

```

And depending on what the graphics situation is. Maybe consider (re-)installing the open-source driver ?
Make sure you don't see lines "blacklist nouveau" with this command:
```

grep -ri nouveau /etc/modprobe*

```
Depending on what you have done in the past :
1. If you installed fglrx from the repo, do
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates

```

2. If you installed using a package from AMD/ATI's website. do
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo amdconfig --uninstall
sudo apt-get install dkms
sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-initramfs -u ## to create a new image ##. 

```
Then reboot your system and when it comes up it will be running with open source.


Also in this situation, as you manually installed a kernel, did you circumvent the package manager ?
Maybe there is a need to do some patching ?
```

sudo apt-get install linux-generic linux-headers-generic linux-image-generic

```
Maybe also do the same for generic-pae, and linux-image-extra (??)

With all the above done, maybe now the system is stable and one can then re-examine the options .

[INDENT][INDENT]hey, it is just 
[INDENT][INDENT][INDENT]my thoughts
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by icoming on 2014-04-25
Thank you for your reply.

> **Bashing-om said:**
> icoming; Hi !

Mind you I may not be the sharpest tack in this box of tacks, But, If it were me in this situation I would:
Make sure the system is fully updated:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade # apt's smart mode - does not release upgrade##

```

I did these multiple times and no more packages were installed.

> 
Then see what the graphics situation is:
To see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga
ubuntu-drivers devices
ubuntu-drivers list
##these commands will take a while to run##

```


$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: RV710 [Radeon HD 4550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:47 memory:e0000000-efffffff memory:f7df0000-f7dfffff ioport:dc00(size=256) memory:f7e00000-f7e1ffff


$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV710 [Radeon HD 4550] [1002:9540]
    Subsystem: Dell Device [1028:0002]
    Kernel driver in use: radeon
    Kernel modules: radeon

These other two commands don't display anything.

> 
And depending on what the graphics situation is. Maybe consider (re-)installing the open-source driver ?
Make sure you don't see lines "blacklist nouveau" with this command:
```

grep -ri nouveau /etc/modprobe*

```
Depending on what you have done in the past :
1. If you installed fglrx from the repo, do
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates

```

2. If you installed using a package from AMD/ATI's website. do
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo amdconfig --uninstall
sudo apt-get install dkms
sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-initramfs -u ## to create a new image ##. 

```
Then reboot your system and when it comes up it will be running with open source.

I don't remember what I installed for the graphics card.
I don't have /etc/X11/xorg.conf for some reason.
It seems to me that fglrx wasn't installed. I don't have amdconfig, either. I executed the remaining commands in the second case. After I reboot it with kernel 3.13, I still got the same problem. The screen and the keyboard don't respond.

---

### Post by Bashing-om on 2014-04-25
icoming; Curiouser and curiouser.

OK, running the open source Radeon driver is the better option - AMD dropped support for that card some time back. Release 14.04 touts it's self highly on the open source graphics support -> card is recognized and the open source driver 'radeon' is loaded.

No Keyboard, now that is going to be tough to overcome, humm
What keyboard are you using ? usb or the older ps/2 keyboard ?
Have you recently made any changes to your BIOS ? usb settings or plug n play settings ?
This situation only developed with 14.04 ? Is this a clean install or an upgrade from 12.04 ?

At what point do you loose the keyboard and monitor ? -> can you boot the 3.13 kernel into 'text' mode ? Maybe if so we can get some more info.

At grub's boot menu, ensure  the 3.13 kernel is highlighted and press the 'e' key for edit mode -> boot parameters screen;
Arrow down to the linux kernel boot line - similar to this - "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff" and arrow across to the terms "quiet splash" replace them with the term "text";
Key combo ctl+x to continue the boot process to a text terminal (TTY1) ( we hope !).

Log in at this terminal - username and pass word - 

Still with a keyboard and a display ? Let's see what happens when the graphic display is started;
Terminal command:
```

sudo service lightdm start

```
The graphical display is key combo ctl+alt+F7 , to return to the terminal on TTY1;  ctl+alt+F1.

Maybe this way we can isolate this to a problem with Xorg .

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]this is one of those times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by icoming on 2014-04-30
Could you tell me how to install the open source Radeon driver?
Does the following command install the Radeon driver?
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

I'm using a USB keyboard and I only lose the keyboard in Ubuntu 14.04 with kernel 3.13. The keyboard works fine if I use kernel 3.2.
I haven't made any change in BIOS recently.

Maybe I don't really lose the monitor. I just lose the keyboard and mouse, which made me believe I lost the monitor as well. If I boot ubuntu with the graphical interface, I can see the login interface.
If I boot Ubuntu with the text mode, as you suggested, I can also see the login prompt in the text terminal, but I still lost the keyboard.
So I guess the problem with the keyboard isn't related to Xorg.

I could ssh to the machine when it boots with kernel 3.13 and I saved dmesg, but I couldn't find any error related to the keyboard.
The output of dmesg is shown below:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-24-generic (buildd@panlong) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 (Ubuntu 3.13.0-24.46-generic 3.13.9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=5b389bde-278e-40de-b138-7f5da39a91b3 ro text vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e3ff] usable
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000db6cfbff] usable
[    0.000000] BIOS-e820: [mem 0x00000000db6cfc00-0x00000000db723bff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000db723c00-0x00000000db725bff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000db725c00-0x00000000dbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed20000-0x00000000fed9ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000feefffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Dell Inc. OptiPlex 980                 /0D441T, BIOS A04 09/11/2010
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0DF800000 mask FFF800000 uncachable
[    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xdb6cf max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fe710-0x000fe71f] mapped at [ffff8800000fe710]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdd000, 0x01fddfff] PGTABLE
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x21fe00000-0x21fffffff]
[    0.000000]  [mem 0x21fe00000-0x21fffffff] page 2M
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x21c000000-0x21fdfffff]
[    0.000000]  [mem 0x21c000000-0x21fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x21bffffff]
[    0.000000]  [mem 0x200000000-0x21bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xdb6cefff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xdb5fffff] page 2M
[    0.000000]  [mem 0xdb600000-0xdb6cefff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x36af6000-0x37572fff]
[    0.000000] ACPI: RSDP 00000000000fec00 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000000fc7e7 00007C (v01 DELL    B11K    00000015 ASL  00000061)
[    0.000000] ACPI: FACP 00000000000fc8d7 0000F4 (v03 DELL    B11K    00000015 ASL  00000061)
[    0.000000] ACPI: DSDT 00000000ffdc89e4 0047BC (v01   DELL    dt_ex 00001000 INTL 20050624)
[    0.000000] ACPI: FACS 00000000db6cfc00 000040
[    0.000000] ACPI: SSDT 00000000ffdcd2c1 0000AC (v01   DELL    st_ex 00001000 INTL 20050624)
[    0.000000] ACPI: APIC 00000000000fc9cb 000092 (v01 DELL    B11K    00000015 ASL  00000061)
[    0.000000] ACPI: BOOT 00000000000fca5d 000028 (v01 DELL    B11K    00000015 ASL  00000061)
[    0.000000] ACPI: ASF! 00000000000fca85 000096 (v32 DELL    B11K    00000015 ASL  00000061)
[    0.000000] ACPI: MCFG 00000000000fcb1b 00003E (v01 DELL    B11K    00000015 ASL  00000061)
[    0.000000] ACPI: HPET 00000000000fcb59 000038 (v01 DELL    B11K    00000015 ASL  00000061)
[    0.000000] ACPI: TCPA 00000000000fcdb5 000032 (v01 DELL    B11K    00000015 ASL  00000061)
[    0.000000] ACPI: ____ 00000000000fcde7 000030 (v01 DELL    B11K    00000015 ASL  00000061)
[    0.000000] ACPI: SLIC 00000000000fcb91 000176 (v01 DELL    B11K    00000015 ASL  00000061)
[    0.000000] ACPI: SSDT 00000000db725c00 002874 (v01  INTEL PPM RCM  80000001 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x21fffffff]
[    0.000000]   NODE_DATA [mem 0x21fff5000-0x21fff9fff]
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880217600000-ffff88021f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x21fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0xdb6cefff]
[    0.000000]   node   0: [mem 0x100000000-0x21fffffff]
[    0.000000] On node 0 totalpages: 2078316
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13980 pages used for memmap
[    0.000000]   DMA32 zone: 894671 pages, LIFO batch:31
[    0.000000]   Normal zone: 18432 pages used for memmap
[    0.000000]   Normal zone: 1179648 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdb6cf000-0xdb6cffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdb6d0000-0xdb722fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdb723000-0xdb723fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdb724000-0xdb724fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdb725000-0xdb725fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdb726000-0xdbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdc000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfed9ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeda0000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfeefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfef00000-0xffafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffb00000-0xffffffff]
[    0.000000] e820: [mem 0xdc000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88021fc00000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2045819
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=5b389bde-278e-40de-b138-7f5da39a91b3 ro text vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8087828K/8313264K available (7338K kernel code, 1138K rwdata, 3388K rodata, 1332K init, 1440K bss, 225436K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2792.954 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5585.90 BogoMIPS (lpj=11171816)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000027] Security Framework initialized
[    0.000045] AppArmor: AppArmor initialized
[    0.000047] Yama: becoming mindful.
[    0.000567] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002143] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002861] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.002872] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.003083] Initializing cgroup subsys memory
[    0.003089] Initializing cgroup subsys devices
[    0.003092] Initializing cgroup subsys freezer
[    0.003094] Initializing cgroup subsys blkio
[    0.003096] Initializing cgroup subsys perf_event
[    0.003099] Initializing cgroup subsys hugetlb
[    0.003115] CPU: Physical Processor ID: 0
[    0.003117] CPU: Processor Core ID: 0
[    0.003122] mce: CPU supports 9 MCE banks
[    0.003131] CPU0: Thermal monitoring enabled (TM1)
[    0.003139] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.003139] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.003139] tlb_flushall_shift: 6
[    0.003227] Freeing SMP alternatives memory: 32K (ffffffff81e6b000 - ffffffff81e73000)
[    0.004221] ACPI: Core revision 20131115
[    0.130447] ACPI: All ACPI Tables successfully acquired
[    0.130522] ftrace: allocating 28408 entries in 111 pages
[    0.142615] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.182340] smpboot: CPU0: Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz (fam: 06, model: 1e, stepping: 05)
[    0.291496] Performance Events: PEBS fmt1+, 16-deep LBR, Nehalem events, Intel PMU driver.
[    0.291502] perf_event_intel: CPU erratum AAJ80 worked around
[    0.291504] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    0.291507] ... version:                3
[    0.291509] ... bit width:              48
[    0.291510] ... generic registers:      4
[    0.291512] ... value mask:             0000ffffffffffff
[    0.291513] ... max period:             000000007fffffff
[    0.291515] ... fixed-purpose events:   3
[    0.291517] ... event mask:             000000070000000f
[    0.292931] x86: Booting SMP configuration:
[    0.306176] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.292934] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.385582] x86: Booted up 1 node, 8 CPUs
[    0.385588] smpboot: Total of 8 processors activated (44687.26 BogoMIPS)
[    0.390923] devtmpfs: initialized
[    0.393089] EVM: security.selinux
[    0.393091] EVM: security.SMACK64
[    0.393093] EVM: security.ima
[    0.393094] EVM: security.capability
[    0.393130] PM: Registering ACPI NVS region [mem 0xdb6cfc00-0xdb723bff] (344064 bytes)
[    0.393902] pinctrl core: initialized pinctrl subsystem
[    0.393957] regulator-dummy: no parameters
[    0.393986] RTC time: 19:31:01, date: 04/30/14
[    0.394015] NET: Registered protocol family 16
[    0.394097] cpuidle: using governor ladder
[    0.394100] cpuidle: using governor menu
[    0.394128] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.394131] ACPI: bus type PCI registered
[    0.394133] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.394180] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.394184] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.396873] PCI: Using configuration type 1 for base access
[    0.396879] dmi type 0xB1 record - unknown flag
[    0.397691] bio: create slab <bio-0> at 0
[    0.397824] ACPI: Added _OSI(Module Device)
[    0.397827] ACPI: Added _OSI(Processor Device)
[    0.397832] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.397834] ACPI: Added _OSI(Processor Aggregator Device)
[    0.432651] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.434397] ACPI BIOS Warning (bug): Incorrect checksum in table [TCPA] - 0x00, should be 0x7E (20131115/tbprint-214)
[    0.435299] ACPI: Interpreter enabled
[    0.435307] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.435319] ACPI: (supports S0 S1 S3 S4 S5)
[    0.435321] ACPI: Using IOAPIC for interrupt routing
[    0.435428] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.435499] ACPI: No dock devices found.
[    0.526005] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.526032] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.526055] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.542022] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.542555] PCI host bridge to bus 0000:00
[    0.542558] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.542561] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.542563] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.542566] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.542568] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000effff]
[    0.542571] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
[    0.542573] pci_bus 0000:00: root bus resource [mem 0xdb800000-0xf7ffffff]
[    0.542576] pci_bus 0000:00: root bus resource [mem 0xff87c000-0xff87ffff]
[    0.542578] pci_bus 0000:00: root bus resource [mem 0xff870000-0xff8707ff]
[    0.542580] pci_bus 0000:00: root bus resource [mem 0xfed20000-0xfed9ffff]
[    0.542583] pci_bus 0000:00: root bus resource [mem 0xfeda6000-0xfeda6fff]
[    0.542585] pci_bus 0000:00: root bus resource [mem 0xfeda7000-0xfeda7fff]
[    0.542594] pci 0000:00:00.0: [8086:d131] type 00 class 0x060000
[    0.542875] pci 0000:00:03.0: [8086:d138] type 01 class 0x060400
[    0.542921] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.543173] pci 0000:00:08.0: [8086:d155] type 00 class 0x088000
[    0.543447] pci 0000:00:08.1: [8086:d156] type 00 class 0x088000
[    0.543727] pci 0000:00:08.2: [8086:d157] type 00 class 0x088000
[    0.544007] pci 0000:00:10.0: [8086:d150] type 00 class 0x088000
[    0.544273] pci 0000:00:10.1: [8086:d151] type 00 class 0x088000
[    0.544556] pci 0000:00:16.0: [8086:3b64] type 00 class 0x078000
[    0.544583] pci 0000:00:16.0: reg 0x10: [mem 0xfeda6000-0xfeda600f 64bit]
[    0.544672] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.544933] pci 0000:00:16.2: [8086:3b66] type 00 class 0x010185
[    0.544952] pci 0000:00:16.2: reg 0x10: [io  0xfe80-0xfe87]
[    0.544961] pci 0000:00:16.2: reg 0x14: [io  0xfe90-0xfe93]
[    0.544970] pci 0000:00:16.2: reg 0x18: [io  0xfea0-0xfea7]
[    0.544980] pci 0000:00:16.2: reg 0x1c: [io  0xfeb0-0xfeb3]
[    0.544989] pci 0000:00:16.2: reg 0x20: [io  0xfef0-0xfeff]
[    0.545299] pci 0000:00:16.3: [8086:3b67] type 00 class 0x070002
[    0.545317] pci 0000:00:16.3: reg 0x10: [io  0xec98-0xec9f]
[    0.545327] pci 0000:00:16.3: reg 0x14: [mem 0xf7fdb000-0xf7fdbfff]
[    0.545658] pci 0000:00:19.0: [8086:10ef] type 00 class 0x020000
[    0.545674] pci 0000:00:19.0: reg 0x10: [mem 0xf7fe0000-0xf7ffffff]
[    0.545682] pci 0000:00:19.0: reg 0x14: [mem 0xf7fdc000-0xf7fdcfff]
[    0.545689] pci 0000:00:19.0: reg 0x18: [io  0xecc0-0xecdf]
[    0.545745] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.546001] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.546020] pci 0000:00:1a.0: reg 0x10: [mem 0xf7fdd000-0xf7fdd3ff]
[    0.546102] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.546337] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.546368] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.546382] pci 0000:00:1b.0: reg 0x10: [mem 0xff87c000-0xff87ffff 64bit]
[    0.546443] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.546696] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.546758] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.546991] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.547021] pci 0000:00:1c.4: [8086:3b4a] type 01 class 0x060400
[    0.547083] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.547317] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.547351] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.547370] pci 0000:00:1d.0: reg 0x10: [mem 0xf7fde000-0xf7fde3ff]
[    0.547453] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.547691] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.547718] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.547987] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.548017] pci 0000:00:1f.0: [8086:3b0a] type 00 class 0x060100
[    0.548365] pci 0000:00:1f.2: [8086:3b22] type 00 class 0x010601
[    0.548382] pci 0000:00:1f.2: reg 0x10: [io  0xfe00-0xfe07]
[    0.548389] pci 0000:00:1f.2: reg 0x14: [io  0xfe10-0xfe13]
[    0.548396] pci 0000:00:1f.2: reg 0x18: [io  0xfe20-0xfe27]
[    0.548402] pci 0000:00:1f.2: reg 0x1c: [io  0xfe30-0xfe33]
[    0.548409] pci 0000:00:1f.2: reg 0x20: [io  0xfec0-0xfedf]
[    0.548416] pci 0000:00:1f.2: reg 0x24: [mem 0xff870000-0xff8707ff]
[    0.548458] pci 0000:00:1f.2: PME# supported from D3hot
[    0.548710] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.548724] pci 0000:00:1f.3: reg 0x10: [mem 0xf7fdf000-0xf7fdf0ff 64bit]
[    0.548742] pci 0000:00:1f.3: reg 0x20: [io  0xece0-0xecff]
[    0.549037] pci 0000:01:00.0: [1002:9540] type 00 class 0x030000
[    0.549050] pci 0000:01:00.0: reg 0x10: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.549060] pci 0000:01:00.0: reg 0x18: [mem 0xf7df0000-0xf7dfffff 64bit]
[    0.549066] pci 0000:01:00.0: reg 0x20: [io  0xdc00-0xdcff]
[    0.549078] pci 0000:01:00.0: reg 0x30: [mem 0xf7e00000-0xf7e1ffff pref]
[    0.549107] pci 0000:01:00.0: supports D1 D2
[    0.555656] pci 0000:00:03.0: PCI bridge to [bus 01]
[    0.555665] pci 0000:00:03.0:   bridge window [io  0xd000-0xdfff]
[    0.555671] pci 0000:00:03.0:   bridge window [mem 0xf7d00000-0xf7efffff]
[    0.555678] pci 0000:00:03.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.555752] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.555807] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.555873] pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)
[    0.555882] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.555883] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.555885] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.555886] pci 0000:00:1e.0:   bridge window [mem 0x000c0000-0x000effff] (subtractive decode)
[    0.555888] pci 0000:00:1e.0:   bridge window [mem 0x000f0000-0x000fffff] (subtractive decode)
[    0.555889] pci 0000:00:1e.0:   bridge window [mem 0xdb800000-0xf7ffffff] (subtractive decode)
[    0.555891] pci 0000:00:1e.0:   bridge window [mem 0xff87c000-0xff87ffff] (subtractive decode)
[    0.555892] pci 0000:00:1e.0:   bridge window [mem 0xff870000-0xff8707ff] (subtractive decode)
[    0.555894] pci 0000:00:1e.0:   bridge window [mem 0xfed20000-0xfed9ffff] (subtractive decode)
[    0.555895] pci 0000:00:1e.0:   bridge window [mem 0xfeda6000-0xfeda6fff] (subtractive decode)
[    0.555897] pci 0000:00:1e.0:   bridge window [mem 0xfeda7000-0xfeda7fff] (subtractive decode)
[    0.568032] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.568913] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.569790] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.570686] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.571586] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.572467] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.573368] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.574246] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.574492] ACPI: Enabled 3 GPEs in block 00 to 3F
[    0.574500] ACPI: \_SB_.PCI0: notify handler is installed
[    0.574523] Found 1 acpi root devices
[    0.574596] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.574600] vgaarb: loaded
[    0.574601] vgaarb: bridge control possible 0000:01:00.0
[    0.574724] SCSI subsystem initialized
[    0.574771] libata version 3.00 loaded.
[    0.574787] ACPI: bus type USB registered
[    0.574799] usbcore: registered new interface driver usbfs
[    0.574805] usbcore: registered new interface driver hub
[    0.574825] usbcore: registered new device driver usb
[    0.574929] PCI: Using ACPI for IRQ routing
[    0.576243] PCI: Discovered peer bus 3f
[    0.576245] PCI: root bus 3f: using default resources
[    0.576246] PCI: Probing PCI hardware (bus 3f)
[    0.576266] PCI host bridge to bus 0000:3f
[    0.576270] pci_bus 0000:3f: root bus resource [io  0x0000-0xffff]
[    0.576272] pci_bus 0000:3f: root bus resource [mem 0x00000000-0xfffffffff]
[    0.576275] pci_bus 0000:3f: No busn resource found for root bus, will use [bus 3f-ff]
[    0.576281] pci 0000:3f:00.0: [8086:2c51] type 00 class 0x060000
[    0.576312] pci 0000:3f:00.1: [8086:2c81] type 00 class 0x060000
[    0.576342] pci 0000:3f:02.0: [8086:2c90] type 00 class 0x060000
[    0.576370] pci 0000:3f:02.1: [8086:2c91] type 00 class 0x060000
[    0.576399] pci 0000:3f:03.0: [8086:2c98] type 00 class 0x060000
[    0.576425] pci 0000:3f:03.1: [8086:2c99] type 00 class 0x060000
[    0.576453] pci 0000:3f:03.4: [8086:2c9c] type 00 class 0x060000
[    0.576482] pci 0000:3f:04.0: [8086:2ca0] type 00 class 0x060000
[    0.576509] pci 0000:3f:04.1: [8086:2ca1] type 00 class 0x060000
[    0.576537] pci 0000:3f:04.2: [8086:2ca2] type 00 class 0x060000
[    0.576568] pci 0000:3f:04.3: [8086:2ca3] type 00 class 0x060000
[    0.576598] pci 0000:3f:05.0: [8086:2ca8] type 00 class 0x060000
[    0.576625] pci 0000:3f:05.1: [8086:2ca9] type 00 class 0x060000
[    0.576652] pci 0000:3f:05.2: [8086:2caa] type 00 class 0x060000
[    0.576680] pci 0000:3f:05.3: [8086:2cab] type 00 class 0x060000
[    0.576717] pci_bus 0000:3f: busn_res: [bus 3f-ff] end is updated to 3f
[    0.576720] PCI: pci_cache_line_size set to 64 bytes
[    0.576772] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.576775] e820: reserve RAM buffer [mem 0x0009e400-0x0009ffff]
[    0.576777] e820: reserve RAM buffer [mem 0xdb6cfc00-0xdbffffff]
[    0.576838] NetLabel: Initializing
[    0.576840] NetLabel:  domain hash size = 128
[    0.576842] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.576854] NetLabel:  unlabeled traffic allowed by default
[    0.576914] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.576922] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 40, 41, 42, 43, 44, 0
[    0.576928] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.578967] hpet: hpet2 irq 40 for MSI
[    0.579007] hpet: hpet3 irq 41 for MSI
[    0.579039] hpet: hpet4 irq 42 for MSI
[    0.579081] hpet: hpet5 irq 43 for MSI
[    0.579122] hpet: hpet6 irq 44 for MSI
[    0.579223] Switched to clocksource hpet
[    0.582971] AppArmor: AppArmor Filesystem Enabled
[    0.583008] pnp: PnP ACPI init
[    0.583020] ACPI: bus type PNP registered
[    0.585375] system 00:00: [io  0x0800-0x085f] could not be reserved
[    0.585379] system 00:00: [io  0x0c00-0x0c7f] has been reserved
[    0.585382] system 00:00: [io  0x0860-0x08ff] has been reserved
[    0.585385] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.585654] pnp 00:01: [dma 4]
[    0.585669] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.585882] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.586081] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.586293] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.592722] pnp 00:05: [dma 0 disabled]
[    0.592774] pnp 00:05: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.597188] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.606296] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.606300] pnp: PnP ACPI: found 8 devices
[    0.606302] ACPI: bus type PNP unregistered
[    0.612302] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.612306] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.612308] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.612314] pci 0000:00:1c.4: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
[    0.612316] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    0.612318] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff] to [bus 03] add_size 200000
[    0.612327] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.612329] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.612331] pci 0000:00:1c.4: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.612332] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.612334] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.612336] pci 0000:00:1c.4: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.612339] pci 0000:00:1c.0: BAR 14: assigned [mem 0xdc000000-0xdc1fffff]
[    0.612343] pci 0000:00:1c.0: BAR 15: assigned [mem 0xdc200000-0xdc3fffff 64bit pref]
[    0.612346] pci 0000:00:1c.4: BAR 14: assigned [mem 0xdc400000-0xdc5fffff]
[    0.612350] pci 0000:00:1c.4: BAR 15: assigned [mem 0xdc600000-0xdc7fffff 64bit pref]
[    0.612353] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.612356] pci 0000:00:1c.4: BAR 13: assigned [io  0x2000-0x2fff]
[    0.612359] pci 0000:00:03.0: PCI bridge to [bus 01]
[    0.612362] pci 0000:00:03.0:   bridge window [io  0xd000-0xdfff]
[    0.612366] pci 0000:00:03.0:   bridge window [mem 0xf7d00000-0xf7efffff]
[    0.612370] pci 0000:00:03.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.612375] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.612378] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.612383] pci 0000:00:1c.0:   bridge window [mem 0xdc000000-0xdc1fffff]
[    0.612387] pci 0000:00:1c.0:   bridge window [mem 0xdc200000-0xdc3fffff 64bit pref]
[    0.612392] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.612395] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    0.612400] pci 0000:00:1c.4:   bridge window [mem 0xdc400000-0xdc5fffff]
[    0.612404] pci 0000:00:1c.4:   bridge window [mem 0xdc600000-0xdc7fffff 64bit pref]
[    0.612410] pci 0000:00:1e.0: PCI bridge to [bus 04]
[    0.612420] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.612421] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.612423] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.612424] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000effff]
[    0.612426] pci_bus 0000:00: resource 8 [mem 0x000f0000-0x000fffff]
[    0.612427] pci_bus 0000:00: resource 9 [mem 0xdb800000-0xf7ffffff]
[    0.612429] pci_bus 0000:00: resource 10 [mem 0xff87c000-0xff87ffff]
[    0.612430] pci_bus 0000:00: resource 11 [mem 0xff870000-0xff8707ff]
[    0.612431] pci_bus 0000:00: resource 12 [mem 0xfed20000-0xfed9ffff]
[    0.612433] pci_bus 0000:00: resource 13 [mem 0xfeda6000-0xfeda6fff]
[    0.612434] pci_bus 0000:00: resource 14 [mem 0xfeda7000-0xfeda7fff]
[    0.612436] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.612437] pci_bus 0000:01: resource 1 [mem 0xf7d00000-0xf7efffff]
[    0.612438] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.612440] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.612441] pci_bus 0000:02: resource 1 [mem 0xdc000000-0xdc1fffff]
[    0.612443] pci_bus 0000:02: resource 2 [mem 0xdc200000-0xdc3fffff 64bit pref]
[    0.612444] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.612446] pci_bus 0000:03: resource 1 [mem 0xdc400000-0xdc5fffff]
[    0.612447] pci_bus 0000:03: resource 2 [mem 0xdc600000-0xdc7fffff 64bit pref]
[    0.612449] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.612450] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.612452] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.612453] pci_bus 0000:04: resource 7 [mem 0x000c0000-0x000effff]
[    0.612455] pci_bus 0000:04: resource 8 [mem 0x000f0000-0x000fffff]
[    0.612456] pci_bus 0000:04: resource 9 [mem 0xdb800000-0xf7ffffff]
[    0.612457] pci_bus 0000:04: resource 10 [mem 0xff87c000-0xff87ffff]
[    0.612459] pci_bus 0000:04: resource 11 [mem 0xff870000-0xff8707ff]
[    0.612460] pci_bus 0000:04: resource 12 [mem 0xfed20000-0xfed9ffff]
[    0.612462] pci_bus 0000:04: resource 13 [mem 0xfeda6000-0xfeda6fff]
[    0.612463] pci_bus 0000:04: resource 14 [mem 0xfeda7000-0xfeda7fff]
[    0.612465] pci_bus 0000:3f: resource 4 [io  0x0000-0xffff]
[    0.612467] pci_bus 0000:3f: resource 5 [mem 0x00000000-0xfffffffff]
[    0.612490] NET: Registered protocol family 2
[    0.612613] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.612807] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.613065] TCP: Hash tables configured (established 65536 bind 65536)
[    0.613085] TCP: reno registered
[    0.613096] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.613151] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.613243] NET: Registered protocol family 1
[    0.614822] pci 0000:01:00.0: Boot video device
[    0.614839] PCI: CLS 64 bytes, default 64
[    0.614880] Trying to unpack rootfs image as initramfs...
[    0.771081] Freeing initrd memory: 10740K (ffff880036af6000 - ffff880037573000)
[    0.771089] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.771092] software IO TLB [mem 0xd76cf000-0xdb6cf000] (64MB) mapped at [ffff8800d76cf000-ffff8800db6cefff]
[    0.771126] Simple Boot Flag at 0x7a set to 0x1
[    0.771335] microcode: CPU0 sig=0x106e5, pf=0x2, revision=0x3
[    0.771342] microcode: CPU1 sig=0x106e5, pf=0x2, revision=0x3
[    0.771349] microcode: CPU2 sig=0x106e5, pf=0x2, revision=0x3
[    0.771356] microcode: CPU3 sig=0x106e5, pf=0x2, revision=0x3
[    0.771363] microcode: CPU4 sig=0x106e5, pf=0x2, revision=0x3
[    0.771369] microcode: CPU5 sig=0x106e5, pf=0x2, revision=0x3
[    0.771375] microcode: CPU6 sig=0x106e5, pf=0x2, revision=0x3
[    0.771381] microcode: CPU7 sig=0x106e5, pf=0x2, revision=0x3
[    0.771454] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.771457] Scanning for low memory corruption every 60 seconds
[    0.771682] Initialise system trusted keyring
[    0.771725] audit: initializing netlink socket (disabled)
[    0.771734] type=2000 audit(1398886260.660:1): initialized
[    0.794049] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.795122] VFS: Disk quotas dquot_6.5.2
[    0.795158] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.795523] fuse init (API version 7.22)
[    0.795586] msgmni has been set to 15817
[    0.795629] Key type big_key registered
[    0.796029] Key type asymmetric registered
[    0.796032] Asymmetric key parser 'x509' registered
[    0.796055] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.796099] io scheduler noop registered
[    0.796101] io scheduler deadline registered (default)
[    0.796120] io scheduler cfq registered
[    0.797440] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.797451] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.797481] vesafb: mode is 1280x800x32, linelength=5120, pages=0
[    0.797483] vesafb: scrolling: redraw
[    0.797486] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    0.797658] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90004e80000, using 4032k, total 4032k
[    0.928113] Console: switching to colour frame buffer device 160x50
[    1.059702] fb0: VESA VGA frame buffer device
[    1.060537] intel_idle: MWAIT substates: 0x1120
[    1.060547] intel_idle: v0.4 model 0x1E
[    1.060548] intel_idle: lapic_timer_reliable_states 0x2
[    1.060696] ipmi message handler version 39.2
[    1.061548] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.063082] ACPI: Power Button [VBTN]
[    1.063806] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.065192] ACPI: Power Button [PWRF]
[    1.066003] GHES: HEST is not enabled!
[    1.066765] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.088411] 00:06: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.111463] 0000:00:16.3: ttyS4 at I/O 0xec98 (irq = 17, base_baud = 115200) is a 16550A
[    1.113332] Linux agpgart interface v0.103
[    1.115184] brd: module loaded
[    1.116337] loop: module loaded
[    1.117621] scsi0 : ata_generic
[    1.118262] scsi1 : ata_generic
[    1.118871] ata1: PATA max UDMA/100 cmd 0xfe80 ctl 0xfe90 bmdma 0xfef0 irq 18
[    1.120215] ata2: PATA max UDMA/100 cmd 0xfea0 ctl 0xfeb0 bmdma 0xfef8 irq 18
[    1.121721] libphy: Fixed MDIO Bus: probed
[    1.122547] tun: Universal TUN/TAP device driver, 1.6
[    1.123492] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.124756] PPP generic driver version 2.4.2
[    1.125641] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.126865] ehci-pci: EHCI PCI platform driver
[    1.128115] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.129100] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.170538] ehci-pci 0000:00:1a.0: debug port 2
[    1.215256] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.215272] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7fdd000
[    1.263925] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.304159] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.344712] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.385197] usb usb1: Product: EHCI Host Controller
[    1.425342] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    1.465791] usb usb1: SerialNumber: 0000:00:1a.0
[    1.506195] hub 1-0:1.0: USB hub found
[    1.546395] hub 1-0:1.0: 3 ports detected
[    1.587014] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.627522] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.668166] ehci-pci 0000:00:1d.0: debug port 2
[    1.711845] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.711861] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7fde000
[    1.760495] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.768460] tsc: Refined TSC clocksource calibration: 2793.000 MHz
[    1.840483] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.881091] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.921626] usb usb2: Product: EHCI Host Controller
[    1.952750] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.002461] usb usb2: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    2.043444] usb usb2: SerialNumber: 0000:00:1d.0
[    2.084153] hub 2-0:1.0: USB hub found
[    2.101570] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    2.101571] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.101966] hub 1-1:1.0: USB hub found
[    2.102168] hub 1-1:1.0: 6 ports detected
[    2.281746] hub 2-0:1.0: 3 ports detected
[    2.319048] ehci-platform: EHCI generic platform driver
[    2.355998] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.392788] ohci-pci: OHCI PCI platform driver
[    2.429620] ohci-platform: OHCI generic platform driver
[    2.466384] uhci_hcd: USB Universal Host Controller Interface driver
[    2.503158] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.542741] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.579295] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.615676] mousedev: PS/2 mouse device common for all mice
[    2.649367] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.690306] rtc_cmos 00:04: RTC can wake from S4
[    2.728513] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.766842] rtc_cmos 00:04: alarms up to one day, 242 bytes nvram, hpet irqs
[    2.805935] Switched to clocksource tsc
[    2.805994] device-mapper: uevent: version 1.0.3
[    2.806147] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    2.806153] ledtrig-cpu: registered to indicate activity on CPUs
[    2.806235] TCP: cubic registered
[    2.806293] NET: Registered protocol family 10
[    2.806413] NET: Registered protocol family 17
[    2.806417] Key type dns_resolver registered
[    2.806805] Loading compiled-in X.509 certificates
[    2.807547] Loaded X.509 cert 'Magrathea: Glacier signing key: 00a5a65759de474bc5c43120880c1b94a539f431'
[    2.807555] registered taskstats version 1
[    2.809810] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    2.809812] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.810150] Key type trusted registered
[    2.810164] hub 2-1:1.0: USB hub found
[    2.810346] hub 2-1:1.0: 8 ports detected
[    2.812501] Key type encrypted registered
[    2.814510] AppArmor: AppArmor sha1 policy hashing enabled
[    2.814512] IMA: No TPM chip found, activating TPM-bypass!
[    2.814726] regulator-dummy: disabling
[    2.814783]   Magic number: 10:735:547
[    2.814791] tty ttyS23: hash matches
[    3.081833] usb 2-1.1: new low-speed USB device number 3 using ehci-pci
[    3.182200] usb 2-1.1: New USB device found, idVendor=046d, idProduct=c05a
[    3.182202] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.182203] usb 2-1.1: Product: USB Optical Mouse
[    3.182204] usb 2-1.1: Manufacturer: Logitech
[    3.254146] usb 2-1.2: new low-speed USB device number 4 using ehci-pci
[    3.355624] usb 2-1.2: New USB device found, idVendor=413c, idProduct=2106
[    3.355625] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.355626] usb 2-1.2: Product: Dell QuietKey Keyboard
[    3.355627] usb 2-1.2: Manufacturer: DELL
[    4.047130] rtc_cmos 00:04: setting system clock to 2014-04-30 19:31:03 UTC (1398886263)
[    4.088401] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.127507] EDD information not available.
[    4.166821] PM: Hibernation image not present or could not be loaded.
[    4.167970] Freeing unused kernel memory: 1332K (ffffffff81d1e000 - ffffffff81e6b000)
[    4.208983] Write protecting the kernel read-only data: 12288k
[    4.252009] Freeing unused kernel memory: 844K (ffff88000172d000 - ffff880001800000)
[    4.295308] Freeing unused kernel memory: 708K (ffff880001b4f000 - ffff880001c00000)
[    4.396287] systemd-udevd[153]: starting version 204
[    4.446740] pps_core: LinuxPPS API ver. 1 registered
[    4.488252] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    4.532014] PTP clock support registered
[    4.574787] ahci 0000:00:1f.2: version 3.0
[    4.575232] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    4.578355] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    4.591294] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x1f impl SATA mode
[    4.591296] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pmp fbs pio ems sxs apst 
[    4.591302] ahci 0000:00:1f.2: port 0 is not capable of FBS
[    4.591330] ahci 0000:00:1f.2: port 1 is not capable of FBS
[    4.599277] ahci 0000:00:1f.2: port 2 is not capable of FBS
[    4.607284] ahci 0000:00:1f.2: port 3 is not capable of FBS
[    4.623649] scsi2 : ahci
[    4.623711] scsi3 : ahci
[    4.623763] scsi4 : ahci
[    4.623817] scsi5 : ahci
[    4.623869] scsi6 : ahci
[    4.623923] scsi7 : ahci
[    4.623950] ata3: SATA max UDMA/133 abar m2048@0xff870000 port 0xff870100 irq 45
[    4.623951] ata4: SATA max UDMA/133 abar m2048@0xff870000 port 0xff870180 irq 45
[    4.623953] ata5: SATA max UDMA/133 abar m2048@0xff870000 port 0xff870200 irq 45
[    4.623954] ata6: SATA max UDMA/133 abar m2048@0xff870000 port 0xff870280 irq 45
[    4.623955] ata7: SATA max UDMA/133 abar m2048@0xff870000 port 0xff870300 irq 45
[    4.623956] ata8: DUMMY
[    4.943753] ata7: SATA link down (SStatus 0 SControl 300)
[    5.115972] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.115984] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.115996] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.116007] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.116527] ata4.00: ATAPI: TSSTcorp DVD+/-RW TS-H653G, DW10, max UDMA/100
[    5.116529] ata4.00: applying bridge limits
[    5.116628] ata6.00: ATA-9: WDC WD2003FZEX-00Z4SA0, 01.01A01, max UDMA/133
[    5.116629] ata6.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    5.116718] ata5.00: ATA-9: WDC WD2003FZEX-00Z4SA0, 01.01A01, max UDMA/133
[    5.116719] ata5.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    5.117286] ata4.00: configured for UDMA/100
[    5.117320] ata5.00: configured for UDMA/133
[    5.117389] ata6.00: configured for UDMA/133
[    5.117623] ata3.00: ATA-8: WDC WD5000AAKS-75V0A0, 05.01D05, max UDMA/133
[    5.117626] ata3.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    5.118884] ata3.00: configured for UDMA/133
[    5.119096] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-7 05.0 PQ: 0 ANSI: 5
[    5.119222] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    5.119252] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    5.119298] sd 2:0:0:0: [sda] Write Protect is off
[    5.119299] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.119311] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.119964] scsi 3:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H653G DW10 PQ: 0 ANSI: 5
[    5.122309] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.122310] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.122393] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    5.122440] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    5.122694] scsi 4:0:0:0: Direct-Access     ATA      WDC WD2003FZEX-0 01.0 PQ: 0 ANSI: 5
[    5.122853] sd 4:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    5.122854] sd 4:0:0:0: [sdb] 4096-byte physical blocks
[    5.122872] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    5.122941] sd 4:0:0:0: [sdb] Write Protect is off
[    5.122943] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.122990] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.122992] scsi 5:0:0:0: Direct-Access     ATA      WDC WD2003FZEX-0 01.0 PQ: 0 ANSI: 5
[    5.123091] sd 5:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    5.123092] sd 5:0:0:0: [sdc] 4096-byte physical blocks
[    5.123115] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    5.123158] sd 5:0:0:0: [sdc] Write Protect is off
[    5.123160] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.123189] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.131984]  sdc: sdc1
[    5.132172] sd 5:0:0:0: [sdc] Attached SCSI disk
[    5.132736]  sdb: sdb1
[    5.133005] sd 4:0:0:0: [sdb] Attached SCSI disk
[    5.162430]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    5.162755] sd 2:0:0:0: [sda] Attached SCSI disk
[    6.813835] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    6.853039] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    6.878541] random: nonblocking pool is initialized
[    6.934822] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[    6.935073] md: bind<sdb1>
[    6.977788] md: bind<sdc1>
[    7.020296] md: raid0 personality registered for level 0
[    7.061299] md0: Warning: Device sdb1 is misaligned
[    7.101734] md/raid0:md0: md_size is 7814050816 sectors.
[    7.142887] md: RAID0 configuration for md0 - 2 zones
[    7.154886] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 84:2b:2b:a1:c6:09
[    7.154891] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    7.154928] e1000e 0000:00:19.0 eth0: MAC: 9, PHY: 9, PBA No: A002FF-0FF
[    7.314287] md: zone0=[sdc1/sdb1]
[    7.356665]       zone-offset=         0KB, device-offset=         0KB, size=3907023872KB
[    7.399919] md: zone1=[sdb1]
[    7.442332]       zone-offset=3907023872KB, device-offset=1953511936KB, size=      1536KB
[    7.485951] 
[    7.528579] md0: detected capacity change from 0 to 4000794017792
[    7.574470]  md0: unknown partition table
[    8.991426] md: linear personality registered for level -1
[    8.993712] md: multipath personality registered for level -4
[    8.997484] md: raid1 personality registered for level 1
[    9.067771] raid6: sse2x1    7199 MB/s
[    9.135837] raid6: sse2x2    8412 MB/s
[    9.203909] raid6: sse2x4    9407 MB/s
[    9.204579] raid6: using algorithm sse2x4 (9407 MB/s)
[    9.205491] raid6: using ssse3x2 recovery algorithm
[    9.207442] xor: measuring software checksum speed
[    9.247945]    prefetch64-sse: 12010.000 MB/sec
[    9.287984]    generic_sse: 12027.000 MB/sec
[    9.288746] xor: using function: generic_sse (12027.000 MB/sec)
[    9.290901] async_tx: api initialized (async)
[    9.298119] md: raid6 personality registered for level 6
[    9.299082] md: raid5 personality registered for level 5
[    9.300048] md: raid4 personality registered for level 4
[    9.306290] md: raid10 personality registered for level 10
[    9.341044] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    9.342280] EXT4-fs (sda6): write access will be enabled during recovery
[   12.619278] EXT4-fs (sda6): orphan cleanup on readonly fs
[   12.631686] EXT4-fs (sda6): 3 orphan inodes deleted
[   12.632574] EXT4-fs (sda6): recovery complete
[   12.735221] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   31.799057] Adding 4113404k swap on /dev/sda7.  Priority:-1 extents:1 across:4113404k FS
[   31.854964] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.046414] systemd-udevd[449]: starting version 204
[   32.714360] parport_pc 00:05: reported by Plug and Play ACPI
[   32.714415] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   32.731304] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   32.738417] lp: driver loaded but no devices found
[   32.741548] device-mapper: multipath: version 1.6.0 loaded
[   32.811939] lp0: using parport0 (interrupt-driven).
[   32.963752] ppdev: user-space parallel port driver
[   33.658189] type=1400 audit(1398886294.310:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=624 comm="apparmor_parser"
[   33.658280] type=1400 audit(1398886294.310:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=624 comm="apparmor_parser"
[   33.658363] type=1400 audit(1398886294.310:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=624 comm="apparmor_parser"
[   33.674825] type=1400 audit(1398886294.326:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=623 comm="apparmor_parser"
[   33.674983] type=1400 audit(1398886294.326:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=623 comm="apparmor_parser"
[   33.675130] type=1400 audit(1398886294.326:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=623 comm="apparmor_parser"
[   34.052897] init: Failed to obtain startpar-bridge instance: Unknown parameter: INSTANCE
[   34.101630] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,user_xattr
[   34.367991] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   34.383389] XFS (md0): Mounting Filesystem
[   34.511183] XFS (md0): Starting recovery (logdev: internal)
[   34.849546] XFS (md0): Ending recovery (logdev: internal)
[   35.044171] init: failsafe main process (866) killed by TERM signal
[   35.220074] FS-Cache: Loaded
[   35.274881] RPC: Registered named UNIX socket transport module.
[   35.274882] RPC: Registered udp transport module.
[   35.274882] RPC: Registered tcp transport module.
[   35.274882] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   35.322199] init: bluetooth main process (934) terminated with status 1
[   35.322207] init: bluetooth main process ended, respawning
[   35.417938] FS-Cache: Netfs 'nfs' registered for caching
[   35.531498] init: bluetooth main process (993) terminated with status 1
[   35.531513] init: bluetooth main process ended, respawning
[   35.548651] init: bluetooth main process (1017) terminated with status 1
[   35.548661] init: bluetooth main process ended, respawning
[   35.566158] init: bluetooth main process (1041) terminated with status 1
[   35.566169] init: bluetooth main process ended, respawning
[   35.582573] init: bluetooth main process (1065) terminated with status 1
[   35.582584] init: bluetooth main process ended, respawning
[   35.606499] init: bluetooth main process (1089) terminated with status 1
[   35.606510] init: bluetooth main process ended, respawning
[   35.611478] init: avahi-cups-reload main process (1107) terminated with status 1
[   35.627677] init: bluetooth main process (1120) terminated with status 1
[   35.627688] init: bluetooth main process ended, respawning
[   35.644987] init: bluetooth main process (1144) terminated with status 1
[   35.644995] init: bluetooth main process ended, respawning
[   35.664274] init: bluetooth main process (1174) terminated with status 1
[   35.664284] init: bluetooth main process ended, respawning
[   35.682944] init: bluetooth main process (1202) terminated with status 1
[   35.682952] init: bluetooth main process ended, respawning
[   35.702468] init: bluetooth main process (1226) terminated with status 1
[   35.702498] init: bluetooth respawning too fast, stopped
[   35.992895] type=1400 audit(1398886296.642:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1165 comm="apparmor_parser"
[   35.993290] type=1400 audit(1398886296.642:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=1165 comm="apparmor_parser"
[   35.995685] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   36.050326] type=1400 audit(1398886296.698:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/share/gdm/guest-session/Xsession" pid=1257 comm="apparmor_parser"
[   36.087886] type=1400 audit(1398886296.738:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/libvirt/virt-aa-helper" pid=1262 comm="apparmor_parser"
[   36.974493] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   37.076068] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   37.076192] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.076442] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.088057] init: samba-ad-dc main process (1310) terminated with status 1
[   38.834048] audit_printk_skb: 54 callbacks suppressed
[   38.834050] type=1400 audit(1398886299.482:30): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=1260 comm="apparmor_parser"
[   38.834448] type=1400 audit(1398886299.482:31): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=1260 comm="apparmor_parser"
[   38.835087] type=1400 audit(1398886299.482:32): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=1260 comm="apparmor_parser"
[   38.835391] type=1400 audit(1398886299.482:33): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=1260 comm="apparmor_parser"
[   38.835869] type=1400 audit(1398886299.482:34): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=1260 comm="apparmor_parser"
[   38.836142] type=1400 audit(1398886299.482:35): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=1260 comm="apparmor_parser"
[   39.502049] init: udev-fallback-graphics main process (1371) terminated with status 1
[   39.699467] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory

```

---

### Post by icoming on 2014-04-30
Another thing I don't quite understand is that dmesg shows the kernel fails to launch hybrid-gfx. But Ubuntu 14.04 doesn't have this executable any more.
BTW, I upgrade from Ubuntu 12.04.

---

### Post by Bashing-om on 2014-04-30
icoming; Yuk !

Not a good introduction to release 14,04.

Let's see what we can do.
This:
> 
configuration: driver=radeon latency=0

says you do have the open source driver 'radeon' installed.  I see no harm,  - as the keyboard is also a component of Xorg - in seeing what might result if the modules were (RE-)installed.
Let's try to boot the 3.13 kernel; at the grub boot menu with that kernel highlighted press the 'e' key for edit mode -> boot parameters screen;
arrown down to the line similar to "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff" arrow across and replace "quiet splash" with the term text. key combo ctl+x to continue the boot process to a text terminal login - as we do not want the GUI active at this time. 
Still with a keyboard ? login here with username and password. 
Let's now try and re-configure xserver-org, and hope in that re-configuration that the keyboard is picked up for the GUI:
```

sudo apt-get install --reinstall xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-initramfs -u

```

OK, still with a keyboard ? Let's try it and see what the GUI situation is:
```

sudo service lightdm start

``` == I do not have 14.04 installed, and I must take for granted this command remains the same to start the GUI. ==

What now is the situation ?

dmesg output:
"0.526055] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM"
" 0.542022] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge"
Card is found and loaded driver:
"0.574596] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.574600] vgaarb: loaded
[    0.574601] vgaarb: bridge control possible 0000:01:00.0"
vesa driver is running:
"vesafb: mode is 1280x800x32, linelength=5120, pages=0"

Not at all sure what is going on here ?????? Keyboard re-assigned to irq 12 ? 
"2.542741] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.579295] serio: i8042 AUX port at 0x60,0x64 irq 12"
but the keyboard is identified !
"3.355626] usb 2-1.2: Product: Dell QuietKey Keyboard"
---------not good but not related to present problem -----------
"7.061299] md0: Warning: Device sdb1 is misaligned"
" 7.574470]  md0: unknown partition table"
//
-------------------------------hybrid-gfx----------------
-> 39.502049] init: udev-fallback-graphics main process (1371) terminated with status 1
[   39.699467] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory
Bug supposedly fixed: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1026787](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1026787)
sudo apt-get install ubuntu-drivers-common -> [https://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg29575.html](https://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg29575.html)
Has to do with audio - pulseaudio ??? maybe too the mouse , Nvidia grahics card ? ->
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1289420](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1289420)
do anyway:
```

dpkg -l ubuntu-drivers-common

```
ubuntu-drivers-common (1:0.2.89.6) will solve the problem.
------------------------------
hybrid-gfx maybe related maybe not.
OK, rather than holding up this thread, let's see where we stand when xserver-org is re-configured, and go again. 

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by icoming on 2014-05-01
Hello Bashing-om,

I lose my keyboard even when I boot ubuntu from the text terminal. It's so weird that I lose my keyboard but the kernel doesn't print any related error messages.

I have tried to reinstall and reconfigure xserver-xorg multiple times, but it didn't fix the problem.

I have ubuntu-drivers-common 1:0.2.91.4, so the bug should have been fixed. I don't understand why I still get the error of hybrid-gfx.

---

### Post by Bashing-om on 2014-05-01
icoming; Weeellll ........

I also do not presently understand what is not going on.
Keyboard worked with 12.04 release, upgraded to 14.04 and lost the capability, even though dmesg says the kernel has the keyboard loaded.
The keyboard works up and until the kernel is loaded, so the problem must lie at some point in the loading of the kernel, If it were a driver problem, I would expect the keyboard to function in a 'text' mode and maybe be lost when the GUI was activated. Such now is not the case -> back to what the kernel is doing.

What type keyboard are you using ? USB or ps/2 ? I have seen cases where bios must be adjusted - though begs the question as to why it was working in release 12.04 and not now. Prior to installing kernel version 3.13 was there any problem ? maybe back out of 3.13 and try and (re)-install kernel version 3.13 from the package manager ???

The keyboard is under the control of xorg, let's see what the log file for xorg has to relate:
```

cat /var/log/Xorg.0.log

```

I will read over this log and enlist the aid of others in the pursuit of the solution.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by icoming on 2014-05-01
The keyboard works when I use kernel 3.2 in Ubuntu 14.04.
It's definitely some kernel problem. It's a usb keyboard.
I'll show Xorg.0.log later.

---

### Post by drplix on 2014-05-02
I have exactly the same problem.  No keyboard and very limited display resolution.  Just like you I updated from 13.04 to 13.09 to 14.04 and for some reason I was left with kernel 3.2.x.   I wanted to get a new DVB-T stick working so I have manually installed kernel 3.13.x  - but it fails to work in the same way as for you.

If I use 3.13.x from grub I lose the keyboard, the netkwork configuration causes problem (even though its very basic static IP) and the display is 800x600.
If I choose 3.2.x from grub all is well again

FYI I have intel chipset and intel graphics - in fact the machine as about as vanilla as you can get.

All help gratefully received.

---

### Post by drplix on 2014-05-02
OK I have fixed my problem.  It seems you can't just manually install linux-image-3.13.x package. You need the dependencies too.

Fixed it with this...

sudo apt-get install linux-image-generic

This installs a bunch of extras too.

---

### Post by Bashing-om on 2014-05-02
@ drplix;
[INDENT]Thanks for the sharing !
In this situation I too am considering what updating to that "transitional" image entails.[/INDENT]

@ icoming; I think, I do

That we want to get you up on kernel image 3.13.0-24.46 - with all the dependencies satisfied.
To that end, let's see what is, and what might be.
```

dpkg -l | grep linux-image-
apt-cache policy "linux-image*"
apt-cache policy "linux-image*" | grep Installed

```
And yes now let's see what happens when we try and update the kernel.
```

sudo apt-get update
sudo apt-get install linux-generic linux-headers-generic linux-image-generic

```
I do not have 14.04 installed so can not make comparisons, it is possible that some tweaking must be done, depending on what the output of the 'dpkg' command relates (-pae ??).

As much as I may want to know why, the expediency is to fix it.

[INDENT]fix it and 
[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT]

---

### Post by james_mcl on 2014-07-12
I'm coming a bit late to this thread, but I've been having keyboard problems in Precise ever since upgrading to 3.13 (on one out of every two boots, it won't respond to keyboard input - which I worked around by going back to 3.11), and while googling I found this:

[https://www.archlinux.org/news/linux-313-warning-ps2-keyboard-support-is-now-modular/](https://www.archlinux.org/news/linux-313-warning-ps2-keyboard-support-is-now-modular/)

The wording of the article suggests that this new "modular" keyboard support affects all systems with the 3.13 kernel, not just Arch Linux. Although it only refers to PS/2 keyboards, perhaps some similar change could have been made which affects USB keyboards like icoming's - I don't know.

It suggests a cause and workaround - which I will try and post the results of:

> 
There's a downside to all this: On some motherboards (mostly ancient ones, but also a few new ones), the i8042 controller cannot be automatically detected. It's rare, but some people will surely be without keyboard. You can detect this situation in advance:

$ dmesg -t | grep '^i8042'
i8042: PNP: No PS/2 controller found. Probing ports directly.

If you have a PS/2 port and get this message, add atkbd to the MODULES= line in mkinitcpio.conf and run mkinitcpio -P. If you just noticed that you are without keyboard after rebooting, fear not! Simply add

earlymodules=atkbd modules-load=atkbd

to your kernel command line in your bootloader.


EDIT: The computer I'm experiencing this problem on is a Lenovo Z560 Ideapad laptop - which I bought because it had an excellent reputation for Linux compatibility at the time.

---

