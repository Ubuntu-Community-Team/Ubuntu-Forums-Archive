---
title: "ATI graphics driver problems migrating from 12.04 to 14.04"
date: 2015-05-09
forum: Installation &amp; Upgrades
---

### Post by Ubugim on 2015-05-09
These are the devices I have on my computer

lspci -nn | grep VGA

00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series] [1002:6840] (rev ff)

I have been using an ATI driver on ubuntu 12.04 with inbuilt + amd graphics without any problem. Once I upgraded to ubuntu 14.04 the old drivers were not not supported. I uninstalled and installed the latest fglrx driver. But I get the message when I start AMD Catalyst after installing:

There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following. No AMD graphics driver is installed, or the AMD driver is not functioning properly. Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig. 

What could be the problem ? Clearly Radeon HD 7500M/7600M Series seems to be supported by fglrx as per AMD website.

Thanks

---

### Post by kagashe on 2015-05-09
The open source Radeon Driver is working very well on Kernel 3.16 on Ubuntu 14.04. Kernel 3.16 is available through [LTS Enablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

I suggest you try it before going for ATI.

Kamalakar

---

### Post by Ubugim on 2015-05-17
Sorry for the late reply but, I have the above suggestion did not work for me because the system has 2 graphics cards as listed above .
 1> It always shows only intel graphics card after boot, how do I choose between radeon and intel ?
2> I have two locations for the .config files /usr/share/X11/xorg.conf.d/ contains files like 
10-evdev.conf             20-intel.conf      50-vmmouse.conf
10-quirks.conf            20-intel.conf~     50-wacom.conf
11-evdev-quirks.conf      20-radeon.conf     51-synaptics-quirks.conf
11-evdev-trackpoint.conf  50-synaptics.conf
 and /etc/X11/ which only contains xorg.conf files of many versions
where do I make the radeon.conf file

3> Also there is almost no get started radeon config file. I need atleast to have a .conf file with basic settings already in there to get started. The radeon man page is just impossible for a beginner. 

To summarise -> choose radeon ATI card and getting started, 

Thanks

---

### Post by kagashe on 2015-05-17
I still feel you should give a try to open source Radeon Driver.
Is it possible for you to download Ubuntu 14.04.2 and try a live CD/USB session?
When you boot into the live session just click on System_Settings/System/Details and see which Graphics driver is in use.

I need to ask you another related question since it is a case of hybrid graphics.
How did you manage the two graphic cards on 12.04 to ensure that Intel graphic cards was not used?
Can you disable the Intel Card in the BIOS to force Ubuntu to use AMD Card in the Live session?

Kamalakar

---

### Post by Ubugim on 2015-05-18
yes I too believe I should try open source radeon,

In 12.04 I was using the fglrx driver, here I could choose between the two graphics cards and on restart my option would work ( I wasnt able to switch when it was on, a restart was necessary to take effect)

I will give BIOS a try, but first I have a question. Should I change something in my .conf file first before disabling in BIOS ?

---

### Post by kagashe on 2015-05-18
> **Ubugim said:**
> yes I too believe I should try open source radeon,

I suggest that you do this by running a Live Session of Ubuntu 14.04.2.

> 
In 12.04 I was using the fglrx driver, here I could choose between the two graphics cards and on restart my option would work ( I wasnt able to switch when it was on, a restart was necessary to take effect)

I will give BIOS a try, but first I have a question. Should I change something in my .conf file first before disabling in BIOS ?

I am suggesting to touch BIOS only for Live Session of Ubuntu 14.04.2 since I am not sure whether we can switch between the two cards in a Live session. You will have to change the settings back to what they are now for your installed Ubuntu 14.04.

Kamalakar

---

### Post by kagashe on 2015-05-18
While you run the Live Session of Ubuntu 14.04.2 use the following command to know which driver is in use:
```
$ lspci -nnk | grep -i vga -A3 | grep 'in use'
```

and the following command to know how it is working:
```
$ /usr/lib/nux/unity_support_test -p
```

Kamalakar

---

### Post by Ubugim on 2015-05-25
Hi, these are the outputs you requested for,

lspci -nnk | grep -i vga -A3 | grep 'in use'
    Kernel driver in use: i915
    Kernel driver in use: radeon

/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL version string:  3.0 Mesa 10.1.3

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

there is no option for me to disable graphics in BIOS

---

### Post by mastablasta on 2015-05-25
you should have removed the drivers before doing the upgrade. 

do the full purge, replace with open source and then reinstall and initialize for hybrid use. read on how to here: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by kagashe on 2015-05-25
> **Ubugim said:**
> Hi, these are the outputs you requested for,

lspci -nnk | grep -i vga -A3 | grep 'in use'
    Kernel driver in use: i915
    Kernel driver in use: radeon

/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL version string:  3.0 Mesa 10.1.3

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

there is no option for me to disable graphics in BIOS
It seems that open source radeon driver is working well, however, I am not sure about how it can work in hybrid system. By the way did you remove/purge the ati driver on Ubuntu 12.04 before upgrading to 14.04 as advised by mastablasta?

---

### Post by Ubugim on 2015-05-26
Hi kagashe and [[COLOR=#000000]mastablasta[/COLOR]]("http://ubuntuforums.org/member.php?u=964486"),

I had not removed amd drivers before updating, however I did a purge and installed amd propreity driver again, but no use: when I do a aticonfig, It still says hardware not supported.

I found an interesting thing researching online: 

sudo xrandr --listproviders
Providers: number : 1
Provider 0: id: 0x48 cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 5 associated providers: 0 name:Intel

Do you know why providers not equal to 2 ? and there is no Provider 1 ??
This could be a problem.

---

### Post by kagashe on 2015-05-27
> **Ubugim said:**
> Hi kagashe and [[COLOR=#000000]mastablasta[/COLOR]]("http://ubuntuforums.org/member.php?u=964486"),

I had not removed amd drivers before updating, however I did a purge and installed amd propreity driver again, but no use: when I do a aticonfig, It still says hardware not supported.

I found an interesting thing researching online: 

sudo xrandr --listproviders
Providers: number : 1
Provider 0: id: 0x48 cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 5 associated providers: 0 name:Intel

Do you know why providers not equal to 2 ? and there is no Provider 1 ??
This could be a problem.
The output is showing that Provided number 1 is "intel"

The other provider i.e. "ati" is not available.

Kamalakar

---

### Post by Ubugim on 2015-05-27
Yes, Ati is not available, How do I make it available?  Here are a few more parameters. Maybe the reason fglrx says hardware not detected is because its off/not booted I am not sure. but then I don't know how lspci detects it.  

cat /sys/class/drm/card1/device/enable
0
cat /sys/class/drm/card0/device/enable
1
cat /sys/class/drm/card1/device/boot_vga
0
cat /sys/class/drm/card1/device/boot_vga
1

Are  these parameters a problem? are there more parameters? How do I change  these to become 1 ? a simple sudo editing returns Fsync failed

Thank you for your continual help, I know we are very close to solving the problem.

---

### Post by mastablasta on 2015-05-27
what does```
 dmesg 
```command show?

did you do this:
```
sudo amdconfig --initial
```

reboot 

and then to check if it's working this ```
fglrxinfo
```

and then the switching should be available in catalyst center.

---

### Post by Ubugim on 2015-05-27
dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-53-generic (buildd@phianna) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #89-Ubuntu SMP Wed May 20 10:34:39 UTC 2015 (Ubuntu 3.13.0-53.89-generic 3.13.11-ckt19)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-53-generic root=UUID=542e85ff-8abd-48de-998d-7eeecee29db0 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d3ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x000000008ffaffff] usable
[    0.000000] BIOS-e820: [mem 0x000000008ffb0000-0x00000000913affff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000913b0000-0x000000009a3befff] usable
[    0.000000] BIOS-e820: [mem 0x000000009a3bf000-0x000000009aebefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009aebf000-0x000000009afbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009afbf000-0x000000009affefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009afff000-0x000000009affffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b000000-0x000000009f9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000015f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Dell Inc. Inspiron 3521/0XF308, BIOS A07 04/18/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x15f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 09B000000 mask FFF000000 uncachable
[    0.000000]   3 base 09C000000 mask FFC000000 uncachable
[    0.000000]   4 base 0FFA00000 mask FFFE00000 write-protect
[    0.000000]   5 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   6 base 100000000 mask F80000000 write-back
[    0.000000]   7 base 15F600000 mask FFFE00000 uncachable
[    0.000000]   8 base 15F800000 mask FFF800000 uncachable
[    0.000000]   9 base 160000000 mask FE0000000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0x9b000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fe1b0-0x000fe1bf] mapped at [ffff8800000fe1b0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x15f400000-0x15f5fffff]
[    0.000000]  [mem 0x15f400000-0x15f5fffff] page 2M
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x15c000000-0x15f3fffff]
[    0.000000]  [mem 0x15c000000-0x15f3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x15bffffff]
[    0.000000]  [mem 0x100000000-0x15bffffff] page 2M
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x40003fff] page 4k
[    0.000000] BRK [0x01fe7000, 0x01fe7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x40005000-0x8ffaffff]
[    0.000000]  [mem 0x40005000-0x401fffff] page 4k
[    0.000000]  [mem 0x40200000-0x8fdfffff] page 2M
[    0.000000]  [mem 0x8fe00000-0x8ffaffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x913b0000-0x9a3befff]
[    0.000000]  [mem 0x913b0000-0x913fffff] page 4k
[    0.000000]  [mem 0x91400000-0x9a1fffff] page 2M
[    0.000000]  [mem 0x9a200000-0x9a3befff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9afff000-0x9affffff]
[    0.000000]  [mem 0x9afff000-0x9affffff] page 4k
[    0.000000] RAMDISK: [mem 0x35afe000-0x36d76fff]
[    0.000000] ACPI: RSDP 00000000000fe020 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT 000000009affe210 00009C (v01 DELL    CL09    00000001      01000013)
[    0.000000] ACPI: FACP 000000009affb000 00010C (v05 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: DSDT 000000009afee000 0092F2 (v01 DELL    CL09    00000000 ASL  00040000)
[    0.000000] ACPI: FACS 000000009afb9000 000040
[    0.000000] ACPI: UEFI 000000009affd000 000236 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: ASF! 000000009affc000 0000A5 (v32 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: HPET 000000009affa000 000038 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: APIC 000000009aff9000 00008C (v03 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: MCFG 000000009aff8000 00003C (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SSDT 000000009afed000 0006FE (v01 COMPAL CRV ORB  00001000 ACPI 00040000)
[    0.000000] ACPI: BOOT 000000009afeb000 000028 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: ASPT 000000009afe9000 000034 (v07 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: DBGP 000000009afe8000 000034 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: FPDT 000000009afe6000 000044 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SSDT 000000009afe5000 0008E4 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009afe4000 000A92 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: DMAR 000000009afe3000 0000B8 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SSDT 000000009afe1000 001EED (v01 COMPAL CRV ORB  00001000 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000015f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x15f5fffff]
[    0.000000]   NODE_DATA [mem 0x15f5f5000-0x15f5f9fff]
[    0.000000]  [ffffea0000000000-ffffea00057fffff] PMD -> [ffff88015ac00000-ffff88015ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x15f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0x8ffaffff]
[    0.000000]   node   0: [mem 0x913b0000-0x9a3befff]
[    0.000000]   node   0: [mem 0x9afff000-0x9affffff]
[    0.000000]   node   0: [mem 0x100000000-0x15f5fffff]
[    0.000000] On node 0 totalpages: 1016667
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9719 pages used for memmap
[    0.000000]   DMA32 zone: 622015 pages, LIFO batch:31
[    0.000000]   Normal zone: 6104 pages used for memmap
[    0.000000]   Normal zone: 390656 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff]
[    0.000000] PM: Registered nosave memory: [mem 0x8ffb0000-0x913affff]
[    0.000000] PM: Registered nosave memory: [mem 0x9a3bf000-0x9aebefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9aebf000-0x9afbefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9afbf000-0x9affefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b000000-0x9f9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9fa00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffb7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffb80000-0xffffffff]
[    0.000000] e820: [mem 0x9fa00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88015f200000 s81536 r8192 d20864 u262144
[    0.000000] pcpu-alloc: s81536 r8192 d20864 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1000759
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-53-generic root=UUID=542e85ff-8abd-48de-998d-7eeecee29db0 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3898632K/4066668K available (7391K kernel code, 1146K rwdata, 3408K rodata, 1336K init, 1448K bss, 168036K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1795.854 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3591.70 BogoMIPS (lpj=7183416)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000041] Security Framework initialized
[    0.000064] AppArmor: AppArmor initialized
[    0.000065] Yama: becoming mindful.
[    0.000464] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001915] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002561] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.002570] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.002818] Initializing cgroup subsys memory
[    0.002825] Initializing cgroup subsys devices
[    0.002827] Initializing cgroup subsys freezer
[    0.002829] Initializing cgroup subsys blkio
[    0.002831] Initializing cgroup subsys perf_event
[    0.002834] Initializing cgroup subsys hugetlb
[    0.002863] CPU: Physical Processor ID: 0
[    0.002864] CPU: Processor Core ID: 0
[    0.002870] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002870] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.003396] mce: CPU supports 7 MCE banks
[    0.003410] CPU0: Thermal monitoring enabled (TM1)
[    0.003422] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.003422] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.003422] tlb_flushall_shift: 2
[    0.003583] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
[    0.005180] ACPI: Core revision 20131115
[    0.012413] ACPI: All ACPI Tables successfully acquired
[    0.024593] ftrace: allocating 28577 entries in 112 pages
[    0.042924] dmar: Host address width 36
[    0.042928] dmar: DRHD base: 0x000000fed90000 flags: 0x0
[    0.042935] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    0.042936] dmar: DRHD base: 0x000000fed91000 flags: 0x1
[    0.042942] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.042943] dmar: RMRR base: 0x0000009ae8c000 end: 0x0000009aeabfff
[    0.042945] dmar: RMRR base: 0x0000009b800000 end: 0x0000009f9fffff
[    0.043018] IOAPIC id 0 under DRHD base  0xfed91000 IOMMU 1
[    0.043020] HPET id 0 under DRHD base 0xfed91000
[    0.043219] Enabled IRQ remapping in x2apic mode
[    0.043220] Enabling x2apic
[    0.043222] Enabled x2apic
[    0.043228] Switched APIC routing to cluster x2apic.
[    0.043677] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.083349] smpboot: CPU0: Intel(R) Core(TM) i5-3337U CPU @ 1.80GHz (fam: 06, model: 3a, stepping: 09)
[    0.083359] TSC deadline timer enabled
[    0.083373] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.083381] ... version:                3
[    0.083382] ... bit width:              48
[    0.083383] ... generic registers:      4
[    0.083385] ... value mask:             0000ffffffffffff
[    0.083386] ... max period:             0000ffffffffffff
[    0.083387] ... fixed-purpose events:   3
[    0.083388] ... event mask:             000000070000000f
[    0.085541] x86: Booting SMP configuration:
[    0.099223] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.085544] .... node  #0, CPUs:      #1 #2 #3
[    0.126522] x86: Booted up 1 node, 4 CPUs
[    0.126526] smpboot: Total of 4 processors activated (14366.83 BogoMIPS)
[    0.130789] devtmpfs: initialized
[    0.134019] EVM: security.selinux
[    0.134020] EVM: security.SMACK64
[    0.134022] EVM: security.ima
[    0.134023] EVM: security.capability
[    0.134083] PM: Registering ACPI NVS region [mem 0x9aebf000-0x9afbefff] (1048576 bytes)
[    0.135215] pinctrl core: initialized pinctrl subsystem
[    0.135280] regulator-dummy: no parameters
[    0.135313] RTC time: 18:41:45, date: 05/27/15
[    0.135352] NET: Registered protocol family 16
[    0.135474] cpuidle: using governor ladder
[    0.135476] cpuidle: using governor menu
[    0.135523] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.135525] ACPI: bus type PCI registered
[    0.135527] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.135595] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.135599] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.170975] PCI: Using configuration type 1 for base access
[    0.170984] dmi type 0xB1 record - unknown flag
[    0.172052] bio: create slab <bio-0> at 0
[    0.172242] ACPI: Added _OSI(Module Device)
[    0.172244] ACPI: Added _OSI(Processor Device)
[    0.172246] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.172248] ACPI: Added _OSI(Processor Aggregator Device)
[    0.175781] ACPI: Executed 1 blocks of module-level executable AML code
[    0.183153] ACPI: SSDT 000000009ae17018 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20130117)
[    0.183598] ACPI: Dynamic OEM Table Load:
[    0.183601] ACPI: SSDT           (null) 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20130117)
[    0.186821] ACPI: SSDT 000000009ae18a98 000303 (v01  PmRef    ApIst 00003000 INTL 20130117)
[    0.187296] ACPI: Dynamic OEM Table Load:
[    0.187298] ACPI: SSDT           (null) 000303 (v01  PmRef    ApIst 00003000 INTL 20130117)
[    0.190664] ACPI: SSDT 000000009ae16d98 000119 (v01  PmRef    ApCst 00003000 INTL 20130117)
[    0.191097] ACPI: Dynamic OEM Table Load:
[    0.191099] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20130117)
[    0.195426] ACPI: Interpreter enabled
[    0.195434] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.195440] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.195457] ACPI: (supports S0 S3 S4 S5)
[    0.195459] ACPI: Using IOAPIC for interrupt routing
[    0.195492] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.195663] ACPI: No dock devices found.
[    0.450435] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.450442] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.450587] \_SB_.PCI0:_OSC invalid UUID
[    0.450588] _OSC request data:1 1f 0 
[    0.450593] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.451367] PCI host bridge to bus 0000:00
[    0.451371] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.451373] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.451376] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.451378] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.451380] pci_bus 0000:00: root bus resource [mem 0x9fa00000-0xfeafffff]
[    0.451390] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    0.451483] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.451524] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.451564] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.451604] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    0.451618] pci 0000:00:02.0: reg 0x10: [mem 0xc1000000-0xc13fffff 64bit]
[    0.451626] pci 0000:00:02.0: reg 0x18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.451631] pci 0000:00:02.0: reg 0x20: [io  0x4000-0x403f]
[    0.451738] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.451765] pci 0000:00:14.0: reg 0x10: [mem 0xc1600000-0xc160ffff 64bit]
[    0.451846] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.451900] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.451941] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.451968] pci 0000:00:16.0: reg 0x10: [mem 0xc1614000-0xc161400f 64bit]
[    0.452054] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.452143] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.452168] pci 0000:00:1a.0: reg 0x10: [mem 0xc1619000-0xc16193ff]
[    0.452270] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.452348] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.452367] pci 0000:00:1b.0: reg 0x10: [mem 0xc1610000-0xc1613fff 64bit]
[    0.452446] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.452522] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.452611] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.452667] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.452707] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    0.452797] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.452845] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.452895] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.452920] pci 0000:00:1d.0: reg 0x10: [mem 0xc1618000-0xc16183ff]
[    0.453021] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.453080] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.453117] pci 0000:00:1f.0: [8086:1e59] type 00 class 0x060100
[    0.453303] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.453327] pci 0000:00:1f.2: reg 0x10: [io  0x4088-0x408f]
[    0.453337] pci 0000:00:1f.2: reg 0x14: [io  0x4094-0x4097]
[    0.453348] pci 0000:00:1f.2: reg 0x18: [io  0x4080-0x4087]
[    0.453359] pci 0000:00:1f.2: reg 0x1c: [io  0x4090-0x4093]
[    0.453368] pci 0000:00:1f.2: reg 0x20: [io  0x4060-0x407f]
[    0.453379] pci 0000:00:1f.2: reg 0x24: [mem 0xc1617000-0xc16177ff]
[    0.453433] pci 0000:00:1f.2: PME# supported from D3hot
[    0.453501] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.453522] pci 0000:00:1f.3: reg 0x10: [mem 0xc1615000-0xc16150ff 64bit]
[    0.453547] pci 0000:00:1f.3: reg 0x20: [io  0x4040-0x405f]
[    0.453699] pci 0000:01:00.0: [1002:6840] type 00 class 0x030000
[    0.453711] pci 0000:01:00.0: reg 0x10: [mem 0xa0000000-0xafffffff 64bit pref]
[    0.453721] pci 0000:01:00.0: reg 0x18: [mem 0xc0000000-0xc001ffff 64bit]
[    0.453727] pci 0000:01:00.0: reg 0x20: [io  0x3000-0x30ff]
[    0.453737] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    0.453770] pci 0000:01:00.0: supports D1 D2
[    0.453854] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.462698] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    0.462702] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.462705] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc0ffffff]
[    0.462709] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    0.462876] pci 0000:07:00.0: [10ec:8136] type 00 class 0x020000
[    0.462949] pci 0000:07:00.0: reg 0x10: [io  0x2000-0x20ff]
[    0.463075] pci 0000:07:00.0: reg 0x18: [mem 0xc1404000-0xc1404fff 64bit pref]
[    0.463156] pci 0000:07:00.0: reg 0x20: [mem 0xc1400000-0xc1403fff 64bit pref]
[    0.463504] pci 0000:07:00.0: supports D1 D2
[    0.463506] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.474748] pci 0000:00:1c.0: PCI bridge to [bus 07]
[    0.474753] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.474763] pci 0000:00:1c.0:   bridge window [mem 0xc1400000-0xc14fffff 64bit pref]
[    0.474882] pci 0000:08:00.0: [168c:0032] type 00 class 0x028000
[    0.474934] pci 0000:08:00.0: reg 0x10: [mem 0xc1500000-0xc157ffff 64bit]
[    0.475054] pci 0000:08:00.0: reg 0x30: [mem 0xffff0000-0xffffffff pref]
[    0.475170] pci 0000:08:00.0: supports D1 D2
[    0.475172] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.486723] pci 0000:00:1c.1: PCI bridge to [bus 08]
[    0.486734] pci 0000:00:1c.1:   bridge window [mem 0xc1500000-0xc15fffff]
[    0.563163] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.563227] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.563287] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.563348] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.563407] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.563467] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.563532] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.563591] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.563879] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.563887] ACPI: \_SB_.PCI0: notify handler is installed
[    0.563950] Found 1 acpi root devices
[    0.563992] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.564103] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.564106] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.564111] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.564112] vgaarb: loaded
[    0.564114] vgaarb: bridge control possible 0000:01:00.0
[    0.564115] vgaarb: no bridge control possible 0000:00:02.0
[    0.564294] SCSI subsystem initialized
[    0.564354] libata version 3.00 loaded.
[    0.564376] ACPI: bus type USB registered
[    0.564393] usbcore: registered new interface driver usbfs
[    0.564403] usbcore: registered new interface driver hub
[    0.564430] usbcore: registered new device driver usb
[    0.564551] PCI: Using ACPI for IRQ routing
[    0.571980] PCI: pci_cache_line_size set to 64 bytes
[    0.572049] e820: reserve RAM buffer [mem 0x0009d400-0x0009ffff]
[    0.572051] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.572053] e820: reserve RAM buffer [mem 0x8ffb0000-0x8fffffff]
[    0.572055] e820: reserve RAM buffer [mem 0x9a3bf000-0x9bffffff]
[    0.572056] e820: reserve RAM buffer [mem 0x9b000000-0x9bffffff]
[    0.572058] e820: reserve RAM buffer [mem 0x15f600000-0x15fffffff]
[    0.572148] NetLabel: Initializing
[    0.572150] NetLabel:  domain hash size = 128
[    0.572151] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.572167] NetLabel:  unlabeled traffic allowed by default
[    0.572234] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.572240] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.574273] Switched to clocksource hpet
[    0.579513] AppArmor: AppArmor Filesystem Enabled
[    0.579540] pnp: PnP ACPI init
[    0.579554] ACPI: bus type PNP registered
[    0.579591] pnp 00:00: [dma 4]
[    0.579617] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.579639] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.579752] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.579789] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.579843] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.579846] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.579848] system 00:04: [io  0xffff] has been reserved
[    0.579850] system 00:04: [io  0xffff] has been reserved
[    0.579853] system 00:04: [io  0x0400-0x0453] could not be reserved
[    0.579855] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.579858] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.579860] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.579862] system 00:04: [io  0xfd60-0xfd63] has been reserved
[    0.579866] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.579896] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.579947] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.579951] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.580000] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.580038] pnp 00:08: Plug and Play ACPI device, IDs DLL0598 PNP0f13 (active)
[    0.650431] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.650434] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.650436] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.650438] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.650441] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.650443] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.650446] system 00:09: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.650448] system 00:09: [mem 0xff000000-0xff000fff] has been reserved
[    0.650450] system 00:09: [mem 0xff010000-0xffffffff] could not be reserved
[    0.650453] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.650455] system 00:09: [mem 0x9fa00000-0x9fa00fff] has been reserved
[    0.650458] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.650835] system 00:0a: [mem 0x20000000-0x201fffff] has been reserved
[    0.650838] system 00:0a: [mem 0x40004000-0x40004fff] has been reserved
[    0.650841] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.650861] pnp: PnP ACPI: found 11 devices
[    0.650863] ACPI: bus type PNP unregistered
[    0.657432] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.657436] pci 0000:08:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.657467] pci 0000:00:1c.1: BAR 15: assigned [mem 0x9fb00000-0x9fbfffff pref]
[    0.657471] pci 0000:01:00.0: BAR 6: assigned [mem 0xc0020000-0xc003ffff pref]
[    0.657474] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    0.657477] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.657480] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc0ffffff]
[    0.657484] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    0.657488] pci 0000:00:1c.0: PCI bridge to [bus 07]
[    0.657492] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.657501] pci 0000:00:1c.0:   bridge window [mem 0xc1400000-0xc14fffff 64bit pref]
[    0.657510] pci 0000:08:00.0: BAR 6: assigned [mem 0x9fb00000-0x9fb0ffff pref]
[    0.657512] pci 0000:00:1c.1: PCI bridge to [bus 08]
[    0.657518] pci 0000:00:1c.1:   bridge window [mem 0xc1500000-0xc15fffff]
[    0.657523] pci 0000:00:1c.1:   bridge window [mem 0x9fb00000-0x9fbfffff pref]
[    0.657532] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.657534] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.657537] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.657539] pci_bus 0000:00: resource 7 [mem 0x9fa00000-0xfeafffff]
[    0.657541] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.657543] pci_bus 0000:01: resource 1 [mem 0xc0000000-0xc0ffffff]
[    0.657546] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xafffffff 64bit pref]
[    0.657548] pci_bus 0000:07: resource 0 [io  0x2000-0x2fff]
[    0.657550] pci_bus 0000:07: resource 2 [mem 0xc1400000-0xc14fffff 64bit pref]
[    0.657552] pci_bus 0000:08: resource 1 [mem 0xc1500000-0xc15fffff]
[    0.657555] pci_bus 0000:08: resource 2 [mem 0x9fb00000-0x9fbfffff pref]
[    0.657590] NET: Registered protocol family 2
[    0.657852] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.657955] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.658059] TCP: Hash tables configured (established 32768 bind 32768)
[    0.658078] TCP: reno registered
[    0.658090] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.658109] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.658174] NET: Registered protocol family 1
[    0.658188] pci 0000:00:02.0: Video device with shadowed ROM
[    1.042261] PCI: CLS 64 bytes, default 64
[    1.042333] Trying to unpack rootfs image as initramfs...
[    1.449903] Freeing initrd memory: 18916K (ffff880035afe000 - ffff880036d77000)
[    1.449916] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.449919] software IO TLB [mem 0x963bf000-0x9a3bf000] (64MB) mapped at [ffff8800963bf000-ffff88009a3befff]
[    1.449965] Simple Boot Flag at 0x44 set to 0x1
[    1.450217] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x17
[    1.450225] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x17
[    1.450234] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x17
[    1.450244] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x17
[    1.450304] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.450306] Scanning for low memory corruption every 60 seconds
[    1.450614] Initialise system trusted keyring
[    1.450663] audit: initializing netlink socket (disabled)
[    1.450675] type=2000 audit(1432752105.428:1): initialized
[    1.487708] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.488834] zbud: loaded
[    1.489015] VFS: Disk quotas dquot_6.5.2
[    1.489059] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.489513] fuse init (API version 7.22)
[    1.489596] msgmni has been set to 7651
[    1.489654] Key type big_key registered
[    1.490136] Key type asymmetric registered
[    1.490139] Asymmetric key parser 'x509' registered
[    1.490173] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.490216] io scheduler noop registered
[    1.490218] io scheduler deadline registered (default)
[    1.490244] io scheduler cfq registered
[    1.490446] pcieport 0000:00:01.0: irq 42 for MSI/MSI-X
[    1.490767] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.490781] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.490820] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    1.490821] vesafb: scrolling: redraw
[    1.490823] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.490830] mtrr: no more MTRRs available
[    1.491432] vesafb: framebuffer at 0xb0000000, mapped to 0xffffc90010780000, using 4160k, total 4160k
[    1.495059] Console: switching to colour frame buffer device 170x48
[    1.498483] fb0: VESA VGA frame buffer device
[    1.498503] intel_idle: MWAIT substates: 0x21120
[    1.498505] intel_idle: v0.4 model 0x3A
[    1.498506] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.498619] ipmi message handler version 39.2
[    1.498661] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.498710] ACPI: AC Adapter [ACAD] (off-line)
[    1.498824] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C0C:00/input/input0
[    1.498829] ACPI: Power Button [PWRB]
[    1.498874] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.498896] ACPI: Lid Switch [LID0]
[    1.498929] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.498932] ACPI: Power Button [PWRF]
[    1.499166] GHES: HEST is not enabled!
[    1.499280] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.741954] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.741960] ACPI: Battery Slot [BAT1] (battery present)
[    1.742084] Linux agpgart interface v0.103
[    1.744169] brd: module loaded
[    1.744832] loop: module loaded
[    1.745188] libphy: Fixed MDIO Bus: probed
[    1.745273] tun: Universal TUN/TAP device driver, 1.6
[    1.745274] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.745325] PPP generic driver version 2.4.2
[    1.745369] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.745373] ehci-pci: EHCI PCI platform driver
[    1.745509] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.745516] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.745532] ehci-pci 0000:00:1a.0: debug port 2
[    1.749456] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.749478] ehci-pci 0000:00:1a.0: irq 16, io mem 0xc1619000
[    1.757916] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.757961] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.757964] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.757966] usb usb1: Product: EHCI Host Controller
[    1.757968] usb usb1: Manufacturer: Linux 3.13.0-53-generic ehci_hcd
[    1.757970] usb usb1: SerialNumber: 0000:00:1a.0
[    1.758108] hub 1-0:1.0: USB hub found
[    1.758116] hub 1-0:1.0: 2 ports detected
[    1.758326] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.758334] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.758349] ehci-pci 0000:00:1d.0: debug port 2
[    1.762237] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.762253] ehci-pci 0000:00:1d.0: irq 23, io mem 0xc1618000
[    1.773909] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.773957] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.773960] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.773962] usb usb2: Product: EHCI Host Controller
[    1.773964] usb usb2: Manufacturer: Linux 3.13.0-53-generic ehci_hcd
[    1.773966] usb usb2: SerialNumber: 0000:00:1d.0
[    1.774116] hub 2-0:1.0: USB hub found
[    1.774123] hub 2-0:1.0: 2 ports detected
[    1.774214] ehci-platform: EHCI generic platform driver
[    1.774224] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.774225] ohci-pci: OHCI PCI platform driver
[    1.774233] ohci-platform: OHCI generic platform driver
[    1.774239] uhci_hcd: USB Universal Host Controller Interface driver
[    1.774374] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.774379] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.774484] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.774510] xhci_hcd 0000:00:14.0: irq 43 for MSI/MSI-X
[    1.774576] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.774578] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.774580] usb usb3: Product: xHCI Host Controller
[    1.774582] usb usb3: Manufacturer: Linux 3.13.0-53-generic xhci_hcd
[    1.774584] usb usb3: SerialNumber: 0000:00:14.0
[    1.774720] hub 3-0:1.0: USB hub found
[    1.774732] hub 3-0:1.0: 4 ports detected
[    1.775095] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.775099] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.775139] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.775141] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.775143] usb usb4: Product: xHCI Host Controller
[    1.775145] usb usb4: Manufacturer: Linux 3.13.0-53-generic xhci_hcd
[    1.775147] usb usb4: SerialNumber: 0000:00:14.0
[    1.775284] hub 4-0:1.0: USB hub found
[    1.775295] hub 4-0:1.0: 4 ports detected
[    1.782009] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.798281] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.798287] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.798548] mousedev: PS/2 mouse device common for all mice
[    1.798915] rtc_cmos 00:05: RTC can wake from S4
[    1.799049] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.799083] rtc_cmos 00:05: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.799147] device-mapper: uevent: version 1.0.3
[    1.799223] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.799231] ledtrig-cpu: registered to indicate activity on CPUs
[    1.799343] TCP: cubic registered
[    1.799424] NET: Registered protocol family 10
[    1.799587] NET: Registered protocol family 17
[    1.799596] Key type dns_resolver registered
[    1.799916] Loading compiled-in X.509 certificates
[    1.801086] Loaded X.509 cert 'Magrathea: Glacier signing key: 9aac900abd0220fb93c8be10f20d6973dab829f5'
[    1.801098] registered taskstats version 1
[    1.804071] Key type trusted registered
[    1.808567] Key type encrypted registered
[    1.808572] AppArmor: AppArmor sha1 policy hashing enabled
[    1.808575] IMA: No TPM chip found, activating TPM-bypass!
[    1.808948] regulator-dummy: disabling
[    1.809035]   Magic number: 15:66:697
[    1.809135] rtc_cmos 00:05: setting system clock to 2015-05-27 18:41:46 UTC (1432752106)
[    1.809936] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.809938] EDD information not available.
[    1.809976] PM: Hibernation image not present or could not be loaded.
[    1.810761] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.810762] Write protecting the kernel read-only data: 12288k
[    1.812618] Freeing unused kernel memory: 788K (ffff88000173b000 - ffff880001800000)
[    1.813627] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.814430] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[    1.826399] systemd-udevd[123]: starting version 204
[    1.851301] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.851311] r8169 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.851545] r8169 0000:07:00.0: irq 44 for MSI/MSI-X
[    1.851715] r8169 0000:07:00.0 eth0: RTL8105e at 0xffffc9000064e000, 74:86:7a:0d:e9:c6, XID 00c00000 IRQ 44
[    1.852054] ahci 0000:00:1f.2: version 3.0
[    1.852185] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.865903] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    1.865909] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.875931] scsi0 : ahci
[    1.876045] scsi1 : ahci
[    1.876126] scsi2 : ahci
[    1.876198] scsi3 : ahci
[    1.876266] scsi4 : ahci
[    1.876335] scsi5 : ahci
[    1.876383] ata1: SATA max UDMA/133 abar m2048@0xc1617000 port 0xc1617100 irq 45
[    1.876385] ata2: DUMMY
[    1.876389] ata3: SATA max UDMA/133 abar m2048@0xc1617000 port 0xc1617200 irq 45
[    1.876391] ata4: DUMMY
[    1.876392] ata5: DUMMY
[    1.876394] ata6: DUMMY
[    2.069952] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.193865] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.197837] ata3.00: ATAPI: TSSTcorp DVD+/-RW SU-208CB, D200, max UDMA/100
[    2.201886] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.202616] ata3.00: configured for UDMA/100
[    2.202623] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    2.202626] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.202974] hub 1-1:1.0: USB hub found
[    2.203137] hub 1-1:1.0: 6 ports detected
[    2.230725] ata1.00: ATA-8: ST500LT012-9WS142, 0002SDM1, max UDMA/133
[    2.230729] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.276184] ata1.00: configured for UDMA/133
[    2.276363] scsi 0:0:0:0: Direct-Access     ATA      ST500LT012-9WS14 0002 PQ: 0 ANSI: 5
[    2.276650] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.276655] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.276669] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.276785] sd 0:0:0:0: [sda] Write Protect is off
[    2.276790] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.276834] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.278762] scsi 2:0:0:0: CD-ROM            TSSTcorp DVD+-RW SU-208CB D200 PQ: 0 ANSI: 5
[    2.286858] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.286862] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.287098] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.287259] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.313837] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.316916]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    2.317492] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.445737] tsc: Refined TSC clocksource calibration: 1795.920 MHz
[    2.446186] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    2.446189] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.446514] hub 2-1:1.0: USB hub found
[    2.446710] hub 2-1:1.0: 6 ports detected
[    2.536914] psmouse serio1: synaptics: queried max coordinates: x [..5674], y [..4754]
[    2.594559] psmouse serio1: synaptics: queried min coordinates: x [1268..], y [1098..]
[    2.613710] usb 3-2: new full-speed USB device number 2 using xhci_hcd
[    2.632159] usb 3-2: New USB device found, idVendor=0461, idProduct=4dfa
[    2.632162] usb 3-2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    2.632163] usb 3-2: Product: Wireless Optical Mouse
[    2.634938] hidraw: raw HID events driver (C) Jiri Kosina
[    2.637890] usbcore: registered new interface driver usbhid
[    2.637892] usbhid: USB HID core driver
[    2.639161] input: Wireless Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input6
[    2.639264] hid-generic 0003:0461:4DFA.0001: input,hidraw0: USB HID v1.11 Mouse [Wireless Optical Mouse] on usb-0000:00:14.0-2/input0
[    2.694706] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x26c00, board id: 2382, fw id: 1238635
[    2.701730] usb 1-1.1: new full-speed USB device number 3 using ehci-pci
[    2.762664] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    2.795702] usb 1-1.1: New USB device found, idVendor=0cf3, idProduct=e004
[    2.795712] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.795717] usb 1-1.1: Product: Bluetooth USB Host Controller
[    2.795721] usb 1-1.1: Manufacturer: Atheros Communications
[    2.795725] usb 1-1.1: SerialNumber: Alaska Day 2006
[    2.865672] usb 1-1.3: new high-speed USB device number 4 using ehci-pci
[    2.958777] usb 1-1.3: New USB device found, idVendor=0bda, idProduct=0129
[    2.958787] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.958793] usb 1-1.3: Product: USB2.0-CRW
[    2.958797] usb 1-1.3: Manufacturer: Generic
[    2.958801] usb 1-1.3: SerialNumber: 20100201396000000
[    3.029635] usb 1-1.4: new high-speed USB device number 5 using ehci-pci
[    3.122798] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    3.190797] usb 1-1.4: New USB device found, idVendor=064e, idProduct=8132
[    3.190801] usb 1-1.4: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    3.190803] usb 1-1.4: Product: Laptop_Integrated_Webcam_HD
[    3.190804] usb 1-1.4: Manufacturer: SuYin
[    3.445582] Switched to clocksource tsc
[    3.819748] random: nonblocking pool is initialized
[   19.714186] Adding 8130556k swap on /dev/sda5.  Priority:-1 extents:1 across:8130556k FS
[   19.753070] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.834272] systemd-udevd[341]: starting version 204
[   20.035025] lp: driver loaded but no devices found
[   20.049561] ppdev: user-space parallel port driver
[   20.202913] wmi: Mapper loaded
[   20.205627] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.217125] [drm] Initialized drm 1.1.0 20060810
[   20.218181] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   20.218190] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.218195] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 1 (20131115/utaddress-251)
[   20.218199] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 2 (20131115/utaddress-251)
[   20.218202] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.218204] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 1 (20131115/utaddress-251)
[   20.218207] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 2 (20131115/utaddress-251)
[   20.218211] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.218212] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   20.234836] cfg80211: Calling CRDA to update world regulatory domain
[   20.242953] mei_me 0000:00:16.0: irq 46 for MSI/MSI-X
[   20.266920] [drm] Memory usable by graphics device = 2048M
[   20.267018] checking generic (b0000000 410000) vs hw (b0000000 10000000)
[   20.267020] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   20.267039] Console: switching to colour dummy device 80x25
[   20.267770] [drm] radeon kernel modesetting enabled.
[   20.267783] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[   20.267839] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[   20.302725] ath: phy0: ASPM enabled: 0x43
[   20.302730] ath: EEPROM regdomain: 0x60
[   20.302731] ath: EEPROM indicates we should expect a direct regpair map
[   20.302734] ath: Country alpha2 being used: 00
[   20.302735] ath: Regpair used: 0x60
[   20.313751] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   20.314413] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffc90010880000, irq=17
[   20.328063] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[   20.328075] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   20.328077] [drm] Driver supports precise vblank timestamp query.
[   20.328216] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=none
[   20.341754] device-mapper: multipath: version 1.6.0 loaded
[   20.382529] Bluetooth: Core ver 2.17
[   20.382548] NET: Registered protocol family 31
[   20.382550] Bluetooth: HCI device and connection manager initialized
[   20.382558] Bluetooth: HCI socket layer initialized
[   20.382562] Bluetooth: L2CAP socket layer initialized
[   20.382566] Bluetooth: SCO socket layer initialized
[   20.384711] usbcore: registered new interface driver btusb
[   20.452027] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[   20.469261] fbcon: inteldrmfb (fb0) is primary device
[   20.559375] type=1400 audit(1432752125.249:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=497 comm="apparmor_parser"
[   20.559380] type=1400 audit(1432752125.249:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=497 comm="apparmor_parser"
[   20.559383] type=1400 audit(1432752125.249:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=497 comm="apparmor_parser"
[   20.559729] type=1400 audit(1432752125.249:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=497 comm="apparmor_parser"
[   20.559732] type=1400 audit(1432752125.249:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=497 comm="apparmor_parser"
[   20.559936] type=1400 audit(1432752125.253:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=497 comm="apparmor_parser"
[   20.929762] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   20.975311] usbcore: registered new interface driver ath3k
[   20.982142] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   21.179884] Console: switching to colour frame buffer device 170x48
[   21.182129] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   21.182138] i915 0000:00:02.0: registered panic notifier
[   21.182310] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   21.195239] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[   21.195314] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2c/LNXVIDEO:00/input/input8
[   21.196400] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   21.196492] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9
[   21.198464] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   21.199087] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   21.199285] [drm] initializing kernel modesetting (TURKS 0x1002:0x6840 0x1028:0x0598).
[   21.199319] [drm] register mmio base: 0xC0000000
[   21.199321] [drm] register mmio size: 131072
[   21.199323] vga_switcheroo: enabled
[   21.199446] ATPX version 1, functions 0x00000033
[   21.201333] usb 1-1.1: USB disconnect, device number 3
[   21.212567] SKU: Nid=0x1d sku_cfg=0x40e00001
[   21.212571] SKU: port_connectivity=0x1
[   21.212572] SKU: enable_pcbeep=0x0
[   21.212574] SKU: check_sum=0x00000000
[   21.212575] SKU: customization=0x00000000
[   21.212576] SKU: external_amp=0x0
[   21.212578] SKU: platform_type=0x0
[   21.212579] SKU: swap=0x0
[   21.212580] SKU: override=0x1
[   21.212792] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   21.212795]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   21.212796]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   21.212798]    mono: mono_out=0x0
[   21.212799]    inputs:
[   21.212801]      Mic=0x19
[   21.212803]      Internal Mic=0x12
[   21.212805] realtek: No valid SSID, checking pincfg 0x40e00001 for NID 0x1d
[   21.212807] realtek: Enabling init ASM_ID=0x0001 CODEC_ID=10ec0282
[   21.226946] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   21.227038] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   21.227114] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   21.344128] Linux video capture interface: v2.00
[   21.346560] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[   21.350552] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_HD (064e:8132)
[   21.352674] scsi6 : SCSI emulation for RTS5139 USB card reader
[   21.352820] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   21.353259] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   21.357570] usbcore: registered new interface driver rts5139
[   21.375061] input: Laptop_Integrated_Webcam_HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input13
[   21.375147] usbcore: registered new interface driver uvcvideo
[   21.375149] USB Video Class driver (1.1.1)
[   21.399762] usb 1-1.1: new full-speed USB device number 6 using ehci-pci
[   21.457325] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   21.468345] cfg80211: World regulatory domain updated:
[   21.468349] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.468350] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.468352] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.468353] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.468354] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.468355] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.493867] usb 1-1.1: New USB device found, idVendor=0cf3, idProduct=e004
[   21.493877] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   21.493882] usb 1-1.1: Product: Bluetooth USB Host Controller
[   21.493886] usb 1-1.1: Manufacturer: Atheros Communications
[   21.493890] usb 1-1.1: SerialNumber: Alaska Day 2006
[   21.677810] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   21.827885] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   22.512425] init: failsafe main process (908) killed by TERM signal
[   22.839879] ATOM BIOS: Dell/Compal
[   22.839969] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[   22.839971] radeon 0000:01:00.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[   22.839972] [drm] Detected VRAM RAM=1024M, BAR=256M
[   22.839973] [drm] RAM width 128bits DDR
[   22.840052] [TTM] Zone  kernel: Available graphics memory: 1960196 kiB
[   22.840054] [TTM] Initializing pool allocator
[   22.840057] [TTM] Initializing DMA pool allocator
[   22.840072] [drm] radeon: 1024M of VRAM memory ready
[   22.840074] [drm] radeon: 1024M of GTT memory ready.
[   22.840082] [drm] Loading TURKS Microcode
[   22.954557] type=1400 audit(1432752127.645:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=964 comm="apparmor_parser"
[   22.954564] type=1400 audit(1432752127.645:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=964 comm="apparmor_parser"
[   22.954933] type=1400 audit(1432752127.645:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=964 comm="apparmor_parser"
[   23.271281] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.271285] Bluetooth: BNEP filters: protocol multicast
[   23.271295] Bluetooth: BNEP socket layer initialized
[   23.272441] Bluetooth: RFCOMM TTY layer initialized
[   23.272452] Bluetooth: RFCOMM socket layer initialized
[   23.272457] Bluetooth: RFCOMM ver 1.11
[   23.700017] init: cups main process (965) killed by HUP signal
[   23.700026] init: cups main process ended, respawning
[   24.731734] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   24.732717] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[   24.735281] [drm] PCIE GART of 1024M enabled (table at 0x0000000000273000).
[   24.735376] radeon 0000:01:00.0: WB enabled
[   24.735379] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff880089776c00
[   24.735380] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff880089776c0c
[   24.736145] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc900110b2118
[   24.736147] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   24.736148] [drm] Driver supports precise vblank timestamp query.
[   24.736149] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[   24.736168] radeon 0000:01:00.0: irq 49 for MSI/MSI-X
[   24.736179] radeon 0000:01:00.0: radeon: using MSI.
[   24.736215] [drm] radeon: irq initialized.
[   24.752511] [drm] ring test on 0 succeeded in 1 usecs
[   24.752518] [drm] ring test on 3 succeeded in 3 usecs
[   24.947980] [drm] ring test on 5 succeeded in 1 usecs
[   24.947986] [drm] UVD initialized successfully.
[   24.948147] [drm] Enabling audio 0 support
[   24.948195] [drm] ib test on ring 0 succeeded in 0 usecs
[   24.948242] [drm] ib test on ring 3 succeeded in 0 usecs
[   25.108650] [drm] ib test on ring 5 succeeded
[   25.109087] [drm] Radeon Display Connectors
[   25.114691] [drm] Internal thermal controller without fan control
[   25.117338] [drm] radeon: dpm initialized
[   25.117539] radeon 0000:01:00.0: No connectors reported connected with modes
[   25.117541] [drm] Cannot find any crtc or sizes - going 1024x768
[   25.118924] [drm] fb mappable at 0xA0474000
[   25.118925] [drm] vram apper at 0xA0000000
[   25.118926] [drm] size 3145728
[   25.118926] [drm] fb depth is 24
[   25.118927] [drm]    pitch is 4096
[   25.119025] radeon 0000:01:00.0: fb1: radeondrmfb frame buffer device
[   25.119042] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 1
[   27.668675] r8169 0000:07:00.0 eth0: link down
[   27.668710] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.669754] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.686115] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.689137] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.285610] init: samba-ad-dc main process (1131) terminated with status 1
[   28.919756] wlan0: authenticate with 78:54:2e:54:c8:dc
[   28.937824] wlan0: send auth to 78:54:2e:54:c8:dc (try 1/3)
[   28.939943] wlan0: authenticated
[   28.941312] wlan0: associate with 78:54:2e:54:c8:dc (try 1/3)
[   28.945574] wlan0: RX AssocResp from 78:54:2e:54:c8:dc (capab=0xc11 status=0 aid=1)
[   28.945644] wlan0: associated
[   28.945662] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   28.945807] cfg80211: Calling CRDA for country: GB
[   28.947895] ath: EEPROM regdomain: 0x833a
[   28.947897] ath: EEPROM indicates we should expect a country code
[   28.947898] ath: doing EEPROM country->regdmn map search
[   28.947900] ath: country maps to regdmn code: 0x37
[   28.947901] ath: Country alpha2 being used: GB
[   28.947901] ath: Regpair used: 0x37
[   28.947902] ath: regdomain 0x833a dynamically updated by country IE
[   28.947922] cfg80211: Regulatory domain changed to country: GB
[   28.947923] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   28.947924] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   28.947925] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   28.947926] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   28.947927] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   28.947928] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[   30.291641] type=1400 audit(1432752134.985:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1231 comm="apparmor_parser"
[   30.291650] type=1400 audit(1432752134.985:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1231 comm="apparmor_parser"
[   30.291656] type=1400 audit(1432752134.985:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1231 comm="apparmor_parser"
[   30.292137] type=1400 audit(1432752134.985:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1231 comm="apparmor_parser"
[   30.292144] type=1400 audit(1432752134.985:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1231 comm="apparmor_parser"
[   30.292429] type=1400 audit(1432752134.985:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1231 comm="apparmor_parser"
[   30.296088] type=1400 audit(1432752134.989:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1230 comm="apparmor_parser"
[   30.296099] type=1400 audit(1432752134.989:18): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1230 comm="apparmor_parser"
[   30.296415] type=1400 audit(1432752134.989:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=1230 comm="apparmor_parser"
[   30.298496] type=1400 audit(1432752134.993:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=1232 comm="apparmor_parser"
[   30.908729] [drm] Disabling audio 0 support
[   31.376390] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory
[   32.242678] vboxdrv: module verification failed: signature and/or  required key missing - tainting kernel
[   32.245945] vboxdrv: Found 4 processor cores.
[   32.247775] vboxdrv: fAsync=0 offMin=0x246 offMax=0x2770
[   32.247869] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   32.247871] vboxdrv: Successfully loaded version 4.3.10_Ubuntu (interface 0x001a0007).
[   32.262679] vboxpci: IOMMU not found (not registered)
[   33.091203] Non-volatile memory driver v1.3
[   34.014600] ip_tables: (C) 2000-2006 Netfilter Core Team
[   34.114497] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   34.798440] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[   34.802067] [drm] PCIE GART of 1024M enabled (table at 0x0000000000273000).
[   34.802150] radeon 0000:01:00.0: WB enabled
[   34.802153] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff880089776c00
[   34.802155] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff880089776c0c
[   34.802929] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc900110b2118
[   34.819060] [drm] ring test on 0 succeeded in 1 usecs
[   34.819067] [drm] ring test on 3 succeeded in 3 usecs
[   35.004600] [drm] ring test on 5 succeeded in 1 usecs
[   35.004605] [drm] UVD initialized successfully.
[   35.004609] [drm] Enabling audio 0 support
[   35.004656] [drm] ib test on ring 0 succeeded in 0 usecs
[   35.004704] [drm] ib test on ring 3 succeeded in 0 usecs
[   35.165129] [drm] ib test on ring 5 succeeded
[   36.825987] init: plymouth-upstart-bridge main process ended, respawning
[   36.989802] init: plymouth-upstart-bridge main process ended, respawning
[   40.919167] [drm] Disabling audio 0 support
[   43.495110] init: anacron main process (1431) killed by TERM signal
[   53.079012] audit_printk_skb: 123 callbacks suppressed
[   53.079016] type=1400 audit(1432752157.786:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2171 comm="apparmor_parser"
[   53.079021] type=1400 audit(1432752157.786:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2171 comm="apparmor_parser"
[   53.079393] type=1400 audit(1432752157.786:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2171 comm="apparmor_parser"
```

---

### Post by Ubugim on 2015-05-27
sudo aticonfig --adapter=all --initial
aticonfig: No supported adapters detected


If I reboot it goes to blank screen since it is not configured I am guesssing.

---

### Post by mastablasta on 2015-05-28
i also don't see any fglrx loaded unless that's what radeon is in dmesg. hmm

---

### Post by kagashe on 2015-05-28
> **mastablasta said:**
> i also don't see any fglrx loaded unless that's what radeon is in dmesg. hmmradeon is open source driver. fglrx will come as ati.

Kamalakar

---

### Post by mastablasta on 2015-05-28
I've managed to get a hold of my PC. and kagashe is correct. you are running opensource drivers.

This is my dmesg (partial):
```
[   24.696148] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   24.696158] Disabling lock debugging due to kernel taint
[   24.716281] fglrx: module verification failed: signature and/or  required key missing - tainting kernel
[   24.728131] <6>[fglrx] Maximum main memory to use for locked dma buffers: 1493 MBytes.
[   24.728362] <6>[fglrx]   vendor: 1002 device: 9806 revision: 0 count: 1
[   24.728989] <6>[fglrx] ioport: bar 1, base 0x4000, size: 0x100
[   24.729666] <6>[fglrx] Kernel PAT support is enabled
[   24.729713] <6>[fglrx] module loaded - fglrx 15.20.2 [Feb 27 2015] with 1 minors

```

you need to:

1. install proprietary drivers
2. initialise it
3. reboot
4. then check if drivers are properly installed by running fglrxinfo which should give you something like this: 

```
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6320 Graphics
OpenGL version string: 4.4.13374 Compatibility Profile Context 13.35.1005

```

please read carefully the special case 4.2 section here: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)
you do not have to install the driver manually but you probably do need to do the initialise command.

---

### Post by Ubugim on 2015-05-31
After installing the propriety drivers I type this command :
```
 sudo amdconfig --initial

aticonfig: No supported adapters detected
```


If I reboot it goes to black screen. So i dont know what to do now. For now I am at a dead end

---

### Post by Ubugim on 2015-05-31
```
 lspci -vnn | grep -i VGA -A 1200:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:0598]
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at c1000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])
    Subsystem: Dell Device [1028:0598]
    Flags: bus master, medium devsel, latency 0, IRQ 43
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series] [1002:6840] (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: radeon

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0598]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    I/O ports at 2000 [size=256]
    Memory at c1404000 (64-bit, prefetchable) [size=4K]
    Memory at c1400000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169


```

This is with open source driver, If you see for AMD it uses radeon driver, and giver error: Unknown header type 7f
Also, as you said upgrading to 14.04 without "uninstalling" fglrx has "maybe" caused the device to be not detected or switched off in 14.04.

---

### Post by mastablasta on 2015-06-01
which is why I said remove & purge proprietary drivers first. reboot and then install proprietary again.

EDIT: btw dmesg shows what things are initialised and you can see what was found and what wasn't.

also if it frustrates too much - backup home folder and programs you wish to backup and just reinstall the whole system. it should be clean and it should work then.

---

