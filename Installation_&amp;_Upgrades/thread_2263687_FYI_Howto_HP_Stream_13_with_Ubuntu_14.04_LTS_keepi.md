---
title: "FYI: Howto HP Stream 13 with Ubuntu 14.04 LTS keeping Windows 8.1 in place"
date: 2015-02-02
forum: Installation &amp; Upgrades
---

### Post by sanderj on 2015-02-02
Hi,

I bought a HP Stream 13 laptop (HP 13-c000nd-N2840): Quite a nice laptop: not a power beast (Intel Celeron, 2GB), but a handy device for only 219 Euro including VAT.

I installed Ubuntu 14.04 LTS next to Windows 8.1 on it, and that works quite well. Here's my Howto from memory (so possibly with a typo here and there):

Use Unetbootin to put Ubuntu 14.04 live-edition 64-bit onto a USB stick. You can use Windows or an existing Ubuntu for that.
Note: as far as I know, you must use 64-bit because of UEFI. A 32-bit Ubuntu on the USB stick was not recognized.

Boot Windows 8.1. Use Windows' "Disk Manager" to resize the main partition (total size about 24GB) to about 15GB, creating a free space of 9 GB for Ubuntu.
Really turn off (as in "non-suspended") Windows 8.1 with "shutdown /s /t 0" 

Turn on your HP Stream 13, and start tapping ESC immediately. You should get the BIOS and boot menu. Choose F9, and select the USB stick. That should offer the Unetbootin / Ubuntu menu; choose "try Ubuntu without installing". That should boot into Ubuntu's GUI.

Try Ubuntu out. If it works, select "Install Ubuntu" from the desktop. In the partition menu, select "Other", in the free space you created, create a 2GB swap space, and a 7GB ext4 partition as "/". Let the install procedure complete. As soon as it finishes, reboot. Start tapping ESC again. It should offer the BIOS / boot menu. You have to find and choose "Ubuntu UEFI" somewhere there. Let Ubuntu boot.

If that works, put into /etc/modprobe.d/rtl8723be.conf these lines:

```
options rtl8723be fwlps=0
options MSI=1
```

That should solve the stability problem with the built-in wifi module. (I'm not sure about that last line, but just to be sure.) Then reload the wifi module:
```
sudo rmmod rtl8723be
sudo modprobe rtl8723be
```

To make Ubuntu the default OS to boot, reboot the system, start pressing ESC, then press F10 to go into the BIOS -> System Configuration -> UEFI Boot Order -> OS Boot Manager. You should see "Windows Boot Manager (MBG4GC)" and "ubuntu (MBG4GC)". Move Ubuntut to the top of the list.

Now let your computer boot into Ubuntu automatically. The GRUB menu also offers you to boot into Windows.

FWIW: some technical stuff:

lspci:
```

00:00.0 Host bridge: Intel Corporation ValleyView SSA-CUnit (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0e)
00:14.0 USB controller: Intel Corporation ValleyView USB xHCI Host Controller (rev 0e)
00:1a.0 Encryption controller: Intel Corporation ValleyView SEC (rev 0e)
00:1b.0 Audio device: Intel Corporation ValleyView High Definition Audio Controller (rev 0e)
00:1c.0 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.1 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.3 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1f.0 ISA bridge: Intel Corporation ValleyView Power Control Unit (rev 0e)
00:1f.3 SMBus: Intel Corporation ValleyView SMBus Controller (rev 0e)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
```

dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-45-generic (buildd@phianna) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 (Ubuntu 3.13.0-45.74-generic 3.13.11-ckt13)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-45-generic.efi.signed root=UUID=dba934e0-c15e-419b-a02a-96c8add96cf2 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000006efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000006f000-0x000000000006ffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000000070000-0x0000000000084fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000085000-0x0000000000086fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000087000-0x0000000000087fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000088000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001effffff] usable
[    0.000000] BIOS-e820: [mem 0x000000001f000000-0x000000001f0fffff] reserved
[    0.000000] BIOS-e820: [mem 0x000000001f100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000200fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020100000-0x000000007588efff] usable
[    0.000000] BIOS-e820: [mem 0x000000007588f000-0x00000000758b9fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000758ba000-0x00000000788b9fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000788ba000-0x00000000791c9fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000791ca000-0x00000000792c9fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000792ca000-0x0000000079309fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007930a000-0x0000000079ffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000e00f8000-0x00000000e00f8fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed01000-0x00000000fed01fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb80000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.40 by INSYDE Corp.
[    0.000000] efi:  ACPI 2.0=0x79309014  SMBIOS=0x78a96000 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] efi: mem01: type=2, attr=0xf, range=[0x0000000000001000-0x0000000000002000) (0MB)
[    0.000000] efi: mem02: type=7, attr=0xf, range=[0x0000000000002000-0x000000000006f000) (0MB)
[    0.000000] efi: mem03: type=10, attr=0xf, range=[0x000000000006f000-0x0000000000070000) (0MB)
[    0.000000] efi: mem04: type=7, attr=0xf, range=[0x0000000000070000-0x0000000000085000) (0MB)
[    0.000000] efi: mem05: type=0, attr=0xf, range=[0x0000000000085000-0x0000000000087000) (0MB)
[    0.000000] efi: mem06: type=3, attr=0xf, range=[0x0000000000087000-0x0000000000088000) (0MB)
[    0.000000] efi: mem07: type=6, attr=0x800000000000000f, range=[0x0000000000088000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem08: type=7, attr=0xf, range=[0x0000000000100000-0x0000000001000000) (15MB)
[    0.000000] efi: mem09: type=2, attr=0xf, range=[0x0000000001000000-0x0000000002403000) (20MB)
[    0.000000] efi: mem10: type=7, attr=0xf, range=[0x0000000002403000-0x000000001f000000) (459MB)
[    0.000000] efi: mem11: type=0, attr=0xf, range=[0x000000001f000000-0x000000001f100000) (1MB)
[    0.000000] efi: mem12: type=7, attr=0xf, range=[0x000000001f100000-0x0000000020000000) (15MB)
[    0.000000] efi: mem13: type=0, attr=0xf, range=[0x0000000020000000-0x0000000020100000) (1MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x0000000020100000-0x000000003eda8000) (492MB)
[    0.000000] efi: mem15: type=2, attr=0xf, range=[0x000000003eda8000-0x0000000040000000) (18MB)
[    0.000000] efi: mem16: type=7, attr=0xf, range=[0x0000000040000000-0x000000005251e000) (293MB)
[    0.000000] efi: mem17: type=2, attr=0xf, range=[0x000000005251e000-0x0000000070000000) (474MB)
[    0.000000] efi: mem18: type=4, attr=0xf, range=[0x0000000070000000-0x0000000070020000) (0MB)
[    0.000000] efi: mem19: type=7, attr=0xf, range=[0x0000000070020000-0x000000007579e000) (87MB)
[    0.000000] efi: mem20: type=2, attr=0xf, range=[0x000000007579e000-0x0000000075889000) (0MB)
[    0.000000] efi: mem21: type=7, attr=0xf, range=[0x0000000075889000-0x000000007588e000) (0MB)
[    0.000000] efi: mem22: type=2, attr=0xf, range=[0x000000007588e000-0x000000007588f000) (0MB)
[    0.000000] efi: mem23: type=5, attr=0x800000000000000f, range=[0x000000007588f000-0x00000000758ba000) (0MB)
[    0.000000] efi: mem24: type=7, attr=0xf, range=[0x00000000758ba000-0x00000000758bb000) (0MB)
[    0.000000] efi: mem25: type=2, attr=0xf, range=[0x00000000758bb000-0x00000000758be000) (0MB)
[    0.000000] efi: mem26: type=7, attr=0xf, range=[0x00000000758be000-0x00000000758c3000) (0MB)
[    0.000000] efi: mem27: type=2, attr=0xf, range=[0x00000000758c3000-0x00000000758c5000) (0MB)
[    0.000000] efi: mem28: type=7, attr=0xf, range=[0x00000000758c5000-0x00000000758c8000) (0MB)
[    0.000000] efi: mem29: type=2, attr=0xf, range=[0x00000000758c8000-0x00000000758ca000) (0MB)
[    0.000000] efi: mem30: type=7, attr=0xf, range=[0x00000000758ca000-0x00000000758cb000) (0MB)
[    0.000000] efi: mem31: type=2, attr=0xf, range=[0x00000000758cb000-0x00000000758cc000) (0MB)
[    0.000000] efi: mem32: type=7, attr=0xf, range=[0x00000000758cc000-0x00000000758cd000) (0MB)
[    0.000000] efi: mem33: type=2, attr=0xf, range=[0x00000000758cd000-0x00000000759ba000) (0MB)
[    0.000000] efi: mem34: type=7, attr=0xf, range=[0x00000000759ba000-0x0000000075a86000) (0MB)
[    0.000000] efi: mem35: type=1, attr=0xf, range=[0x0000000075a86000-0x0000000075bba000) (1MB)
[    0.000000] efi: mem36: type=7, attr=0xf, range=[0x0000000075bba000-0x0000000076dbe000) (18MB)
[    0.000000] efi: mem37: type=4, attr=0xf, range=[0x0000000076dbe000-0x0000000077700000) (9MB)
[    0.000000] efi: mem38: type=7, attr=0xf, range=[0x0000000077700000-0x000000007770c000) (0MB)
[    0.000000] efi: mem39: type=4, attr=0xf, range=[0x000000007770c000-0x0000000077835000) (1MB)
[    0.000000] efi: mem40: type=7, attr=0xf, range=[0x0000000077835000-0x0000000077839000) (0MB)
[    0.000000] efi: mem41: type=4, attr=0xf, range=[0x0000000077839000-0x00000000780ba000) (8MB)
[    0.000000] efi: mem42: type=7, attr=0xf, range=[0x00000000780ba000-0x00000000784d8000) (4MB)
[    0.000000] efi: mem43: type=3, attr=0xf, range=[0x00000000784d8000-0x00000000788ba000) (3MB)
[    0.000000] efi: mem44: type=5, attr=0x800000000000000f, range=[0x00000000788ba000-0x000000007894a000) (0MB)
[    0.000000] efi: mem45: type=6, attr=0x800000000000000f, range=[0x000000007894a000-0x0000000078bca000) (2MB)
[    0.000000] efi: mem46: type=0, attr=0xf, range=[0x0000000078bca000-0x00000000791ca000) (6MB)
[    0.000000] efi: mem47: type=10, attr=0xf, range=[0x00000000791ca000-0x00000000792ca000) (1MB)
[    0.000000] efi: mem48: type=9, attr=0xf, range=[0x00000000792ca000-0x000000007930a000) (0MB)
[    0.000000] efi: mem49: type=4, attr=0xf, range=[0x000000007930a000-0x000000007a000000) (12MB)
[    0.000000] efi: mem50: type=11, attr=0x8000000000000001, range=[0x00000000e00f8000-0x00000000e00f9000) (0MB)
[    0.000000] efi: mem51: type=11, attr=0x8000000000000000, range=[0x00000000fed01000-0x00000000fed02000) (0MB)
[    0.000000] efi: mem52: type=11, attr=0x8000000000000001, range=[0x00000000ffb80000-0x00000000ffc00000) (0MB)
[    0.000000] efi: mem53: type=11, attr=0x8000000000000000, range=[0x00000000ffc00000-0x0000000100000000) (4MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Hewlett-Packard HP Stream Notebook PC 13/802A, BIOS F.05 11/28/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x7a000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 07C000000 mask FFC000000 uncachable
[    0.000000]   3 base 07B000000 mask FFF000000 uncachable
[    0.000000]   4 base 07AE00000 mask FFFE00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff88000007f000] 7f000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x78200000-0x783fffff]
[    0.000000]  [mem 0x78200000-0x783fffff] page 2M
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x78000000-0x781fffff]
[    0.000000]  [mem 0x78000000-0x781fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x74000000-0x7588efff]
[    0.000000]  [mem 0x74000000-0x757fffff] page 2M
[    0.000000]  [mem 0x75800000-0x7588efff] page 4k
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x758ba000-0x77ffffff]
[    0.000000]  [mem 0x758ba000-0x759fffff] page 4k
[    0.000000]  [mem 0x75a00000-0x77ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1effffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1effffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x1f100000-0x1fffffff]
[    0.000000]  [mem 0x1f100000-0x1f1fffff] page 4k
[    0.000000]  [mem 0x1f200000-0x1fffffff] page 2M
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x20100000-0x73ffffff]
[    0.000000]  [mem 0x20100000-0x201fffff] page 4k
[    0.000000]  [mem 0x20200000-0x73ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x78400000-0x788b9fff]
[    0.000000]  [mem 0x78400000-0x787fffff] page 2M
[    0.000000]  [mem 0x78800000-0x788b9fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7930a000-0x79ffffff]
[    0.000000]  [mem 0x7930a000-0x793fffff] page 4k
[    0.000000]  [mem 0x79400000-0x79ffffff] page 2M
[    0.000000] RAMDISK: [mem 0x3eda8000-0x3fffafff]
[    0.000000] ACPI: RSDP 0000000079309014 000024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 0000000079309120 0000AC (v01 HPQOEM SLIC-MPC 00000003      01000013)
[    0.000000] ACPI: FACP 0000000079306000 00010C (v05 HPQOEM SLIC-MPC 00000003 HP   00040000)
[    0.000000] ACPI: DSDT 00000000792f5000 00BB6D (v02 HPQOEM SLIC-MPC 00000003 ACPI 00040000)
[    0.000000] ACPI: FACS 0000000079291000 000040
[    0.000000] ACPI: UEFI 0000000079308000 000236 (v01 HPQOEM 802A     00000001 HP   00040000)
[    0.000000] ACPI: MSDM 0000000079307000 000055 (v03 HPQOEM SLIC-MPC 00000001 HP   00040000)
[    0.000000] ACPI: HPET 0000000079305000 000038 (v01 HPQOEM 802A     00000003 HP   00040000)
[    0.000000] ACPI: LPIT 0000000079304000 000104 (v01 HPQOEM 802A     00000003 HP   00040000)
[    0.000000] ACPI: APIC 0000000079303000 000084 (v03 HPQOEM SLIC-MPC 00000003 HP   00040000)
[    0.000000] ACPI: MCFG 0000000079302000 00003C (v01 HPQOEM 802A     00000003 HP   00040000)
[    0.000000] ACPI: SSDT 0000000079301000 00053A (v01 HPQOEM 802A     00000003 INTL 00040000)
[    0.000000] ACPI: SSDT 00000000792f3000 0010A6 (v01 HPQOEM 802A     00000003 INTL 00040000)
[    0.000000] ACPI: SSDT 00000000792f2000 000763 (v01 HPQOEM 802A     00003000 INTL 00040000)
[    0.000000] ACPI: SSDT 00000000792f1000 000290 (v01 HPQOEM 802A     00003000 INTL 00040000)
[    0.000000] ACPI: SSDT 00000000792f0000 00017A (v01 HPQOEM 802A     00003000 INTL 00040000)
[    0.000000] ACPI: UEFI 00000000792ef000 000042 (v01 HPQOEM 802A     00000000 HP   00040000)
[    0.000000] ACPI: SSDT 00000000792e9000 005E55 (v01 HPQOEM 802A     00001000 INTL 00040000)
[    0.000000] ACPI: SSDT 00000000792e8000 0002F5 (v01 HPQOEM 802A     00001000 INTL 00040000)
[    0.000000] ACPI: FPDT 00000000792e7000 000044 (v01 HPQOEM SLIC-MPC 00000002 HP   00040000)
[    0.000000] ACPI: BGRT 00000000792e6000 000038 (v01 HPQOEM 802A     00000001 HP   00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000079ffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x79ffffff]
[    0.000000]   NODE_DATA [mem 0x784d2000-0x784d6fff]
[    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff880073800000-ffff8800757fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0006efff]
[    0.000000]   node   0: [mem 0x00070000-0x00084fff]
[    0.000000]   node   0: [mem 0x00087000-0x00087fff]
[    0.000000]   node   0: [mem 0x00100000-0x1effffff]
[    0.000000]   node   0: [mem 0x1f100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20100000-0x7588efff]
[    0.000000]   node   0: [mem 0x758ba000-0x788b9fff]
[    0.000000]   node   0: [mem 0x7930a000-0x79ffffff]
[    0.000000] On node 0 totalpages: 496393
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 22 pages reserved
[    0.000000]   DMA zone: 3972 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7744 pages used for memmap
[    0.000000]   DMA32 zone: 492421 pages, LIFO batch:31
[    0.000000] tboot: non-0 tboot_addr but it is not of type E820_RESERVED
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high level lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high level lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high level lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-86
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 103
[    0.000000] PM: Registered nosave memory: [mem 0x0006f000-0x0006ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x00085000-0x00086fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00088000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x1f000000-0x1f0fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x200fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7588f000-0x758b9fff]
[    0.000000] PM: Registered nosave memory: [mem 0x788ba000-0x791c9fff]
[    0.000000] PM: Registered nosave memory: [mem 0x791ca000-0x792c9fff]
[    0.000000] PM: Registered nosave memory: [mem 0x792ca000-0x79309fff]
[    0.000000] e820: [mem 0x7f000000-0xe00f7fff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff880076a00000 s82368 r8192 d24128 u524288
[    0.000000] pcpu-alloc: s82368 r8192 d24128 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 488563
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-45-generic.efi.signed root=UUID=dba934e0-c15e-419b-a02a-96c8add96cf2 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 1880180K/1985572K available (7383K kernel code, 1145K rwdata, 3408K rodata, 1336K init, 1444K bss, 105392K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-3.
[    0.000000] NR_IRQS:16640 nr_irqs:1024 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 8388608 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2166.754 MHz processor
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4333.50 BogoMIPS (lpj=8667016)
[    0.000009] pid_max: default: 32768 minimum: 301
[    0.001266] Security Framework initialized
[    0.001295] AppArmor: AppArmor initialized
[    0.001298] Yama: becoming mindful.
[    0.001578] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002505] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.002931] Mount-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.002941] Mountpoint-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.003274] Initializing cgroup subsys memory
[    0.003287] Initializing cgroup subsys devices
[    0.003291] Initializing cgroup subsys freezer
[    0.003295] Initializing cgroup subsys blkio
[    0.003298] Initializing cgroup subsys perf_event
[    0.003303] Initializing cgroup subsys hugetlb
[    0.003331] CPU: Physical Processor ID: 0
[    0.003334] CPU: Processor Core ID: 0
[    0.003340] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.003340] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.008111] mce: CPU supports 6 MCE banks
[    0.008120] CPU0: Thermal monitoring handled by SMI
[    0.008129] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.008129] Last level dTLB entries: 4KB 128, 2MB 0, 4MB 0
[    0.008129] tlb_flushall_shift: 6
[    0.008264] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
[    0.009514] ACPI: Core revision 20131115
[    0.027510] ACPI: All ACPI Tables successfully acquired
[    0.029647] ftrace: allocating 28554 entries in 112 pages
[    0.045491] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.085214] smpboot: CPU0: Intel(R) Celeron(R) CPU  N2840  @ 2.16GHz (fam: 06, model: 37, stepping: 08)
[    0.085228] TSC deadline timer enabled
[    0.085246] Performance Events: PEBS fmt2+, 8-deep LBR, Silvermont events, full-width counters, Intel PMU driver.
[    0.085258] ... version:                3
[    0.085260] ... bit width:              40
[    0.085262] ... generic registers:      2
[    0.085264] ... value mask:             000000ffffffffff
[    0.085266] ... max period:             000000ffffffffff
[    0.085268] ... fixed-purpose events:   3
[    0.085270] ... event mask:             0000000700000003
[    0.088162] x86: Booting SMP configuration:
[    0.103862] CPU1: Thermal monitoring handled by SMI
[    0.088168] .... node  #0, CPUs:      #1
[    0.105962] x86: Booted up 1 node, 2 CPUs
[    0.105969] smpboot: Total of 2 processors activated (8667.01 BogoMIPS)
[    0.106101] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.106728] devtmpfs: initialized
[    0.112994] EVM: security.selinux
[    0.112997] EVM: security.SMACK64
[    0.112999] EVM: security.ima
[    0.113001] EVM: security.capability
[    0.113093] PM: Registering ACPI NVS region [mem 0x0006f000-0x0006ffff] (4096 bytes)
[    0.113097] PM: Registering ACPI NVS region [mem 0x791ca000-0x792c9fff] (1048576 bytes)
[    0.114731] pinctrl core: initialized pinctrl subsystem
[    0.114862] regulator-dummy: no parameters
[    0.114900] RTC time: 19:11:56, date: 02/02/15
[    0.114970] NET: Registered protocol family 16
[    0.115185] cpuidle: using governor ladder
[    0.115188] cpuidle: using governor menu
[    0.115280] ACPI: bus type PCI registered
[    0.115284] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.115388] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.115393] PCI: not using MMCONFIG
[    0.115395] PCI: Using configuration type 1 for base access
[    0.117013] bio: create slab <bio-0> at 0
[    0.117322] ACPI: Added _OSI(Module Device)
[    0.117326] ACPI: Added _OSI(Processor Device)
[    0.117328] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.117331] ACPI: Added _OSI(Processor Aggregator Device)
[    0.139075] ACPI: SSDT 00000000791c1918 000440 (v01  PmRef  Cpu0Ist 00003000 INTL 20130117)
[    0.139998] ACPI: Dynamic OEM Table Load:
[    0.140003] ACPI: SSDT           (null) 000440 (v01  PmRef  Cpu0Ist 00003000 INTL 20130117)
[    0.140184] ACPI: SSDT 00000000791c1498 000433 (v01  PmRef  Cpu0Cst 00003001 INTL 20130117)
[    0.141090] ACPI: Dynamic OEM Table Load:
[    0.141095] ACPI: SSDT           (null) 000433 (v01  PmRef  Cpu0Cst 00003001 INTL 20130117)
[    0.146442] ACPI: SSDT 00000000791c3e18 00015F (v01  PmRef    ApIst 00003000 INTL 20130117)
[    0.147394] ACPI: Dynamic OEM Table Load:
[    0.147399] ACPI: SSDT           (null) 00015F (v01  PmRef    ApIst 00003000 INTL 20130117)
[    0.150144] ACPI: SSDT 00000000791c2f18 00008D (v01  PmRef    ApCst 00003000 INTL 20130117)
[    0.151057] ACPI: Dynamic OEM Table Load:
[    0.151061] ACPI: SSDT           (null) 00008D (v01  PmRef    ApCst 00003000 INTL 20130117)
[    6.181952] ACPI: Interpreter enabled
[    6.181966] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    6.181975] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    6.182003] ACPI: (supports S0 S3 S4 S5)
[    6.182006] ACPI: Using IOAPIC for interrupt routing
[    6.182050] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    6.182869] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in ACPI motherboard resources
[    6.190175] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    6.190545] ACPI: No dock devices found.
[    6.207988] ACPI: Power Resource [USBC] (on)
[    6.214637] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    6.214649] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    6.214726] \_SB_.PCI0:_OSC invalid UUID
[    6.214729] _OSC request data:1 1f 0 
[    6.214737] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    6.215201] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    6.215514] PCI host bridge to bus 0000:00
[    6.215520] pci_bus 0000:00: root bus resource [bus 00-ff]
[    6.215524] pci_bus 0000:00: root bus resource [io  0x0000-0x006f]
[    6.215528] pci_bus 0000:00: root bus resource [io  0x0078-0x0cf7]
[    6.215531] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    6.215535] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    6.215538] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    6.215542] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000fffff]
[    6.215546] pci_bus 0000:00: root bus resource [mem 0x90c00000-0x90ffffff]
[    6.215549] pci_bus 0000:00: root bus resource [mem 0x80000000-0x908ffffe]
[    6.215561] pci 0000:00:00.0: [8086:0f00] type 00 class 0x060000
[    6.215703] pci 0000:00:02.0: [8086:0f31] type 00 class 0x030000
[    6.215719] pci 0000:00:02.0: reg 0x10: [mem 0x90000000-0x903fffff]
[    6.215731] pci 0000:00:02.0: reg 0x18: [mem 0x80000000-0x8fffffff pref]
[    6.215743] pci 0000:00:02.0: reg 0x20: [io  0x2050-0x2057]
[    6.215897] pci 0000:00:14.0: [8086:0f35] type 00 class 0x0c0330
[    6.215918] pci 0000:00:14.0: reg 0x10: [mem 0x90800000-0x9080ffff 64bit]
[    6.215979] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    6.216078] pci 0000:00:14.0: System wakeup disabled by ACPI
[    6.216151] pci 0000:00:1a.0: [8086:0f18] type 00 class 0x108000
[    6.216181] pci 0000:00:1a.0: reg 0x10: [mem 0x90700000-0x907fffff]
[    6.216196] pci 0000:00:1a.0: reg 0x14: [mem 0x90600000-0x906fffff]
[    6.216304] pci 0000:00:1a.0: PME# supported from D0 D3hot
[    6.216428] pci 0000:00:1b.0: [8086:0f04] type 00 class 0x040300
[    6.216453] pci 0000:00:1b.0: reg 0x10: [mem 0x90810000-0x90813fff 64bit]
[    6.216525] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    6.216641] pci 0000:00:1c.0: [8086:0f48] type 01 class 0x060400
[    6.216703] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    6.216780] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    6.216837] pci 0000:00:1c.1: [8086:0f4a] type 01 class 0x060400
[    6.216898] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    6.216974] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    6.217026] pci 0000:00:1c.3: [8086:0f4e] type 01 class 0x060400
[    6.217087] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    6.217162] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    6.217221] pci 0000:00:1f.0: [8086:0f1c] type 00 class 0x060100
[    6.217405] pci 0000:00:1f.3: [8086:0f12] type 00 class 0x0c0500
[    6.217443] pci 0000:00:1f.3: reg 0x10: [mem 0x90814000-0x9081401f]
[    6.217515] pci 0000:00:1f.3: reg 0x20: [io  0x2000-0x201f]
[    6.217784] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    6.217883] pci 0000:02:00.0: [10ec:b723] type 00 class 0x028000
[    6.217912] pci 0000:02:00.0: reg 0x10: [io  0x1000-0x10ff]
[    6.217971] pci 0000:02:00.0: reg 0x18: [mem 0x90500000-0x90503fff 64bit]
[    6.218116] pci 0000:02:00.0: supports D1 D2
[    6.218119] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    6.225977] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    6.225983] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    6.225989] pci 0000:00:1c.1:   bridge window [mem 0x90500000-0x905fffff]
[    6.226104] pci 0000:03:00.0: [10ec:5229] type 00 class 0xff0000
[    6.226143] pci 0000:03:00.0: reg 0x10: [mem 0x9040f000-0x9040ffff]
[    6.226265] pci 0000:03:00.0: supports D1 D2
[    6.226269] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
[    6.234009] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    6.234016] pci 0000:00:1c.3:   bridge window [mem 0x90400000-0x904fffff]
[    6.238778] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    6.238899] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    6.239018] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    6.239136] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    6.239254] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    6.239372] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    6.239490] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    6.239608] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    6.242199] ACPI: Enabled 7 GPEs in block 00 to 3F
[    6.242253] ACPI: \_SB_.PCI0: notify handler is installed
[    6.242372] Found 1 acpi root devices
[    6.242556] ACPI : EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    6.242745] vgaarb: setting as boot device: PCI:0000:00:02.0
[    6.242749] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    6.242754] vgaarb: loaded
[    6.242757] vgaarb: bridge control possible 0000:00:02.0
[    6.243054] SCSI subsystem initialized
[    6.243133] libata version 3.00 loaded.
[    6.243174] ACPI: bus type USB registered
[    6.243209] usbcore: registered new interface driver usbfs
[    6.243227] usbcore: registered new interface driver hub
[    6.243281] usbcore: registered new device driver usb
[    6.243497] PCI: Using ACPI for IRQ routing
[    6.244896] PCI: pci_cache_line_size set to 64 bytes
[    6.244970] e820: reserve RAM buffer [mem 0x0006f000-0x0006ffff]
[    6.244974] e820: reserve RAM buffer [mem 0x00085000-0x0008ffff]
[    6.244977] e820: reserve RAM buffer [mem 0x00088000-0x0008ffff]
[    6.244980] e820: reserve RAM buffer [mem 0x1f000000-0x1fffffff]
[    6.244982] e820: reserve RAM buffer [mem 0x7588f000-0x77ffffff]
[    6.244985] e820: reserve RAM buffer [mem 0x788ba000-0x7bffffff]
[    6.244988] e820: reserve RAM buffer [mem 0x7a000000-0x7bffffff]
[    6.245127] NetLabel: Initializing
[    6.245130] NetLabel:  domain hash size = 128
[    6.245132] NetLabel:  protocols = UNLABELED CIPSOv4
[    6.245152] NetLabel:  unlabeled traffic allowed by default
[    6.245264] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    6.245272] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    6.247336] Switched to clocksource hpet
[    6.255899] AppArmor: AppArmor Filesystem Enabled
[    6.255950] pnp: PnP ACPI init
[    6.255973] ACPI: bus type PNP registered
[    6.256053] pnp 00:00: Plug and Play ACPI device, IDs PNP0b00 (active)
[    6.256163] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    6.256792] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    6.256874] system 00:03: [io  0x0680-0x069f] has been reserved
[    6.256879] system 00:03: [io  0x0400-0x047f] has been reserved
[    6.256883] system 00:03: [io  0x0500-0x05fe] has been reserved
[    6.256887] system 00:03: [io  0x0600-0x061f] has been reserved
[    6.256893] system 00:03: [mem 0xfed40000-0xfed44fff] has been reserved
[    6.256898] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    6.256994] pnp 00:04: Plug and Play ACPI device, IDs HPQ8001 PNP0303 (active)
[    6.259461] pnp 00:05: Plug and Play ACPI device, IDs SYN1ee1 SYN1e00 SYN0002 PNP0f13 (active)
[    6.260030] system 00:06: [mem 0xe0000000-0xefffffff] could not be reserved
[    6.260036] system 00:06: [mem 0xfed01000-0xfed01fff] has been reserved
[    6.260041] system 00:06: [mem 0xfed03000-0xfed03fff] has been reserved
[    6.260048] system 00:06: [mem 0xfed04000-0xfed04fff] has been reserved
[    6.260053] system 00:06: [mem 0xfed0c000-0xfed0ffff] has been reserved
[    6.260057] system 00:06: [mem 0xfed08000-0xfed08fff] has been reserved
[    6.260061] system 00:06: [mem 0xfed1c000-0xfed1cfff] has been reserved
[    6.260065] system 00:06: [mem 0xfee00000-0xfeefffff] has been reserved
[    6.260069] system 00:06: [mem 0xfef00000-0xfeffffff] has been reserved
[    6.260074] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    6.261825] pnp 00:07: Plug and Play ACPI device, IDs INT33bd (active)
[    6.261971] pnp 00:08: Plug and Play ACPI device, IDs INT3401 (active)
[    6.262174] pnp: PnP ACPI: found 9 devices
[    6.262177] ACPI: bus type PNP unregistered
[    6.270516] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
[    6.270525] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000
[    6.270529] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 01] add_size 200000
[    6.270550] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    6.270554] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    6.270558] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    6.270566] pci 0000:00:1c.0: BAR 14: assigned [mem 0x90c00000-0x90dfffff]
[    6.270572] pci 0000:00:1c.0: BAR 15: assigned [mem 0x90e00000-0x90ffffff 64bit pref]
[    6.270578] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    6.270582] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    6.270587] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    6.270593] pci 0000:00:1c.0:   bridge window [mem 0x90c00000-0x90dfffff]
[    6.270599] pci 0000:00:1c.0:   bridge window [mem 0x90e00000-0x90ffffff 64bit pref]
[    6.270606] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    6.270610] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    6.270616] pci 0000:00:1c.1:   bridge window [mem 0x90500000-0x905fffff]
[    6.270624] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    6.270630] pci 0000:00:1c.3:   bridge window [mem 0x90400000-0x904fffff]
[    6.270639] pci_bus 0000:00: resource 4 [io  0x0000-0x006f]
[    6.270643] pci_bus 0000:00: resource 5 [io  0x0078-0x0cf7]
[    6.270646] pci_bus 0000:00: resource 6 [io  0x0d00-0xffff]
[    6.270650] pci_bus 0000:00: resource 7 [mem 0x000a0000-0x000bffff]
[    6.270653] pci_bus 0000:00: resource 8 [mem 0x000c0000-0x000dffff]
[    6.270657] pci_bus 0000:00: resource 9 [mem 0x000e0000-0x000fffff]
[    6.270661] pci_bus 0000:00: resource 10 [mem 0x90c00000-0x90ffffff]
[    6.270664] pci_bus 0000:00: resource 11 [mem 0x80000000-0x908ffffe]
[    6.270668] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    6.270672] pci_bus 0000:01: resource 1 [mem 0x90c00000-0x90dfffff]
[    6.270675] pci_bus 0000:01: resource 2 [mem 0x90e00000-0x90ffffff 64bit pref]
[    6.270679] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    6.270682] pci_bus 0000:02: resource 1 [mem 0x90500000-0x905fffff]
[    6.270686] pci_bus 0000:03: resource 1 [mem 0x90400000-0x904fffff]
[    6.270741] NET: Registered protocol family 2
[    6.271091] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    6.271164] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    6.271240] TCP: Hash tables configured (established 16384 bind 16384)
[    6.271287] TCP: reno registered
[    6.271297] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    6.271316] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    6.271443] NET: Registered protocol family 1
[    6.271469] pci 0000:00:02.0: Video device with shadowed ROM
[    6.271816] PCI: CLS 64 bytes, default 64
[    6.271927] Trying to unpack rootfs image as initramfs...
[    6.728683] Freeing initrd memory: 18764K (ffff88003eda8000 - ffff88003fffb000)
[    6.728979] microcode: CPU0 sig=0x30678, pf=0x8, revision=0x830
[    6.728990] microcode: CPU1 sig=0x30678, pf=0x8, revision=0x830
[    6.729079] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    6.729083] Scanning for low memory corruption every 60 seconds
[    6.729533] Initialise system trusted keyring
[    6.729608] audit: initializing netlink socket (disabled)
[    6.729629] type=2000 audit(1422904322.720:1): initialized
[    6.769236] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    6.771154] zbud: loaded
[    6.771383] VFS: Disk quotas dquot_6.5.2
[    6.771457] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    6.772295] fuse init (API version 7.22)
[    6.772424] msgmni has been set to 3780
[    6.772514] Key type big_key registered
[    6.773141] Key type asymmetric registered
[    6.773145] Asymmetric key parser 'x509' registered
[    6.773205] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    6.773269] io scheduler noop registered
[    6.773273] io scheduler deadline registered (default)
[    6.773321] io scheduler cfq registered
[    6.773924] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    6.773950] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    6.774020] efifb: probing for efifb
[    6.774611] efifb: framebuffer at 0x80000000, mapped to 0xffffc90004400000, using 4128k, total 4128k
[    6.774614] efifb: mode is 1366x768x32, linelength=5504, pages=1
[    6.774616] efifb: scrolling: redraw
[    6.774620] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    6.781056] Console: switching to colour frame buffer device 170x48
[    6.787295] fb0: EFI VGA frame buffer device
[    6.787341] intel_idle: does not run on family 6 model 55
[    6.787353] ipmi message handler version 39.2
[    6.787822] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    6.788313] ACPI: AC Adapter [ACAD] (on-line)
[    6.788599] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    6.789086] ACPI: Lid Switch [LID0]
[    6.789149] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    6.789156] ACPI: Power Button [PWRB]
[    6.789224] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    6.789229] ACPI: Power Button [PWRF]
[    6.791262] Monitor-Mwait will be used to enter C-1 state
[    6.791271] Monitor-Mwait will be used to enter C-2 state
[    6.791296] ACPI: acpi_idle registered with cpuidle
[    6.799513] thermal LNXTHERM:00: registered as thermal_zone0
[    6.799518] ACPI: Thermal Zone [TZ01] (44 C)
[    6.799561] GHES: HEST is not enabled!
[    6.799710] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    6.820066] serial8250: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    6.881860] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    6.881874] ACPI: Battery Slot [BAT0] (battery present)
[    6.882029] Linux agpgart interface v0.103
[    6.884583] brd: module loaded
[    6.885905] loop: module loaded
[    6.886527] libphy: Fixed MDIO Bus: probed
[    6.886679] tun: Universal TUN/TAP device driver, 1.6
[    6.886682] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    6.886759] PPP generic driver version 2.4.2
[    6.886839] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    6.886847] ehci-pci: EHCI PCI platform driver
[    6.886866] ehci-platform: EHCI generic platform driver
[    6.886878] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    6.886881] ohci-pci: OHCI PCI platform driver
[    6.886894] ohci-platform: OHCI generic platform driver
[    6.886905] uhci_hcd: USB Universal Host Controller Interface driver
[    6.887126] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    6.887137] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    6.887542] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    6.887575] xhci_hcd 0000:00:14.0: irq 103 for MSI/MSI-X
[    6.887688] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    6.887692] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    6.887696] usb usb1: Product: xHCI Host Controller
[    6.887699] usb usb1: Manufacturer: Linux 3.13.0-45-generic xhci_hcd
[    6.887703] usb usb1: SerialNumber: 0000:00:14.0
[    6.887905] hub 1-0:1.0: USB hub found
[    6.887922] hub 1-0:1.0: 6 ports detected
[    6.888626] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    6.888635] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    6.888702] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    6.888706] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    6.888710] usb usb2: Product: xHCI Host Controller
[    6.888713] usb usb2: Manufacturer: Linux 3.13.0-45-generic xhci_hcd
[    6.888716] usb usb2: SerialNumber: 0000:00:14.0
[    6.888877] hub 2-0:1.0: USB hub found
[    6.888891] hub 2-0:1.0: 1 port detected
[    6.895987] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    6.902765] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.902775] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.902983] mousedev: PS/2 mouse device common for all mice
[    6.903284] rtc_cmos 00:00: RTC can wake from S4
[    6.903432] rtc_cmos 00:00: rtc core: registered rtc_cmos as rtc0
[    6.903464] rtc_cmos 00:00: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    6.903594] device-mapper: uevent: version 1.0.3
[    6.903708] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    6.903720] ledtrig-cpu: registered to indicate activity on CPUs
[    6.903723] EFI Variables Facility v0.08 2004-May-17
[    6.915646] TCP: cubic registered
[    6.915803] NET: Registered protocol family 10
[    6.916093] NET: Registered protocol family 17
[    6.916122] Key type dns_resolver registered
[    6.916588] Loading compiled-in X.509 certificates
[    6.918335] Loaded X.509 cert 'Magrathea: Glacier signing key: 34992139f3da40b620bd5517597ba85af5797c9a'
[    6.918365] registered taskstats version 1
[    6.922053] Key type trusted registered
[    6.925373] Key type encrypted registered
[    6.928704] AppArmor: AppArmor sha1 policy hashing enabled
[    6.928711] IMA: No TPM chip found, activating TPM-bypass!
[    6.929030] regulator-dummy: disabling
[    6.929104]   Magic number: 3:755:191
[    6.929164] acpi device:1d: hash matches
[    6.929222] rtc_cmos 00:00: setting system clock to 2015-02-02 19:12:03 UTC (1422904323)
[    6.929789] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    6.929792] EDD information not available.
[    6.929859] PM: Hibernation image not present or could not be loaded.
[    6.931536] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    6.931542] Write protecting the kernel read-only data: 12288k
[    6.935054] Freeing unused kernel memory: 796K (ffff880001739000 - ffff880001800000)
[    6.937901] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[    6.955333] systemd-udevd[103]: starting version 204
[    6.973568] sdhci: Secure Digital Host Controller Interface driver
[    6.973572] sdhci: Copyright(c) Pierre Ossman
[    6.976080] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    6.979626] sdhci-acpi 80860F14:00: dummy supplies not allowed
[    6.979631] mmc0: no vqmmc regulator found
[    6.979634] sdhci-acpi 80860F14:00: dummy supplies not allowed
[    6.979636] mmc0: no vmmc regulator found
[    6.980761] mmc0: SDHCI controller on ACPI [80860F14:00] using ADMA
[    7.008048] rtsx_pci 0000:03:00.0: irq 104 for MSI/MSI-X
[    7.008080] rtsx_pci 0000:03:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 104
[    7.085832] mmc0: BKOPS_EN bit is not set
[    7.133480] mmc0: new HS200 MMC card at address 0001
[    7.136953] mmcblk0: mmc0:0001 MBG4GC 29.1 GiB 
[    7.137068] mmcblk0boot0: mmc0:0001 MBG4GC partition 1 4.00 MiB
[    7.137176] mmcblk0boot1: mmc0:0001 MBG4GC partition 2 4.00 MiB
[    7.137267] mmcblk0rpmb: mmc0:0001 MBG4GC partition 3 4.00 MiB
[    7.139538]  mmcblk0: p1 p2 p3 p4 p5 p6
[    7.141708]  mmcblk0boot1: unknown partition table
[    7.142483]  mmcblk0boot0: unknown partition table
[    7.200157] usb 1-4: new high-speed USB device number 2 using xhci_hcd
[    7.217422] usb 1-4: New USB device found, idVendor=05e3, idProduct=0608
[    7.217427] usb 1-4: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    7.217430] usb 1-4: Product: USB2.0 Hub
[    7.217966] hub 1-4:1.0: USB hub found
[    7.218251] hub 1-4:1.0: 4 ports detected
[    7.254182] EXT4-fs (mmcblk0p5): mounted filesystem with ordered data mode. Opts: (null)
[    7.365364] random: init urandom read with 94 bits of entropy available
[    7.410210] init: plymouth-upstart-bridge main process (155) terminated with status 1
[    7.410234] init: plymouth-upstart-bridge main process ended, respawning
[    7.421256] init: plymouth-upstart-bridge main process (165) terminated with status 1
[    7.421281] init: plymouth-upstart-bridge main process ended, respawning
[    7.428533] init: plymouth-upstart-bridge main process (168) terminated with status 1
[    7.428557] init: plymouth-upstart-bridge main process ended, respawning
[    7.439046] init: plymouth-upstart-bridge main process (170) terminated with status 1
[    7.439069] init: plymouth-upstart-bridge main process ended, respawning
[    7.488598] usb 1-4.1: new low-speed USB device number 3 using xhci_hcd
[    7.508768] usb 1-4.1: New USB device found, idVendor=046d, idProduct=c05a
[    7.508774] usb 1-4.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    7.508777] usb 1-4.1: Product: USB Optical Mouse
[    7.508780] usb 1-4.1: Manufacturer: Logitech
[    7.508912] usb 1-4.1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    7.580671] usb 1-4.3: new full-speed USB device number 4 using xhci_hcd
[    7.597033] usb 1-4.3: No LPM exit latency info found.  Power management will be impacted.
[    7.598244] usb 1-4.3: New USB device found, idVendor=0bda, idProduct=b001
[    7.598251] usb 1-4.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    7.598254] usb 1-4.3: Product: Bluetooth Radio 
[    7.598257] usb 1-4.3: Manufacturer: Realtek 
[    7.598259] usb 1-4.3: SerialNumber: 00e04c000001
[    7.718058] Adding 2427900k swap on /dev/mmcblk0p6.  Priority:-1 extents:1 across:2427900k SSFS
[    7.728566] tsc: Refined TSC clocksource calibration: 2166.666 MHz
[    7.933400] systemd-udevd[289]: starting version 204
[    7.941502] random: nonblocking pool is initialized
[    7.974089] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xf00123/0x840300/0x12e800, board id: 3003, fw id: 1738305
[    8.024654] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    8.059869] lp: driver loaded but no devices found
[    8.082239] ppdev: user-space parallel port driver
[    8.125776] Initializing HPQ6001 module
[    8.126016] input: HP Wireless hotkeys as /devices/virtual/input/input6
[    8.158093] wmi: Mapper loaded
[    8.181698] [drm] Initialized drm 1.1.0 20060810
[    8.231439] cfg80211: Calling CRDA to update world regulatory domain
[    8.235634] [drm] Memory usable by graphics device = 2048M
[    8.235643] checking generic (80000000 408000) vs hw (80000000 10000000)
[    8.235646] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
[    8.235674] Console: switching to colour dummy device 80x25
[    8.297216] Bluetooth: Core ver 2.17
[    8.297344] NET: Registered protocol family 31
[    8.297348] Bluetooth: HCI device and connection manager initialized
[    8.297359] Bluetooth: HCI socket layer initialized
[    8.297363] Bluetooth: L2CAP socket layer initialized
[    8.297371] Bluetooth: SCO socket layer initialized
[    8.298940] i915 0000:00:02.0: irq 105 for MSI/MSI-X
[    8.298958] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    8.298960] [drm] Driver supports precise vblank timestamp query.
[    8.321822] usbcore: registered new interface driver btusb
[    8.411182] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[    8.419179] hidraw: raw HID events driver (C) Jiri Kosina
[    8.428675] usbcore: registered new interface driver usbhid
[    8.428681] usbhid: USB HID core driver
[    8.473472] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    8.527766] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.528113] rtlwifi: wireless switch is on
[    8.548597] kvm: disabled by bios
[    8.592953] kvm: disabled by bios
[    8.629881] type=1400 audit(1422900725.195:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=363 comm="apparmor_parser"
[    8.629893] type=1400 audit(1422900725.195:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=363 comm="apparmor_parser"
[    8.629900] type=1400 audit(1422900725.195:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=363 comm="apparmor_parser"
[    8.630793] type=1400 audit(1422900725.195:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=363 comm="apparmor_parser"
[    8.630806] type=1400 audit(1422900725.195:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=363 comm="apparmor_parser"
[    8.631263] type=1400 audit(1422900725.195:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=363 comm="apparmor_parser"
[    8.739870] Switched to clocksource tsc
[    8.920003] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.0/input/input8
[    8.921054] hid-generic 0003:046D:C05A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:14.0-4.1/input0
[    8.952133] cfg80211: World regulatory domain updated:
[    8.952139] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.952142] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.952144] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.952146] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.952149] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.952151] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.306245] input: HP WMI hotkeys as /devices/virtual/input/input7
[   10.007365] EXT4-fs (mmcblk0p5): re-mounted. Opts: errors=remount-ro
[   10.510896] init: failsafe main process (545) killed by TERM signal
[   10.665753] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.665759] Bluetooth: BNEP filters: protocol multicast
[   10.665772] Bluetooth: BNEP socket layer initialized
[   10.686722] Bluetooth: RFCOMM TTY layer initialized
[   10.686739] Bluetooth: RFCOMM socket layer initialized
[   10.686749] Bluetooth: RFCOMM ver 1.11
[   10.809790] type=1400 audit(1422900727.373:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=630 comm="apparmor_parser"
[   10.809802] type=1400 audit(1422900727.373:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=630 comm="apparmor_parser"
[   10.814514] type=1400 audit(1422900727.377:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=630 comm="apparmor_parser"
[   11.111448] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[   11.430389] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.430783] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.719810] [drm] GMBUS [i915 gmbus dpc] timed out, falling back to bit banging on pin 4
[   11.826428] fbcon: inteldrmfb (fb0) is primary device
[   11.833108] [drm] Enabling RC6 states: RC6 off, RC6p off, RC6pp off
[   12.039359] init: alsa-restore main process (811) terminated with status 19
[   12.373412] wlan0: authenticate with c0:4a:00:2c:dc:bd
[   12.383785] wlan0: send auth to c0:4a:00:2c:dc:bd (try 1/3)
[   12.385859] wlan0: authenticated
[   12.388368] wlan0: associate with c0:4a:00:2c:dc:bd (try 1/3)
[   12.391844] wlan0: RX AssocResp from c0:4a:00:2c:dc:bd (capab=0x421 status=0 aid=1)
[   12.391942] wlan0: associated
[   12.391954] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   12.392608] cfg80211: Calling CRDA for country: US
[   12.396155] cfg80211: Regulatory domain changed to country: US
[   12.396156] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.396159] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   12.396160] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   12.396161] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.396162] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.396164] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.396165] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   12.396166] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[   13.221624] Console: switching to colour frame buffer device 170x48
[   13.227977] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   13.227979] i915 0000:00:02.0: registered panic notifier
[   13.229848] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.232602] acpi device:1b: registered as cooling_device2
[   13.232832] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   13.233128] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.234574] snd_hda_intel 0000:00:1b.0: irq 106 for MSI/MSI-X
[   13.378461] SKU: Nid=0x1d sku_cfg=0x40f00001
[   13.378462] SKU: port_connectivity=0x1
[   13.378463] SKU: enable_pcbeep=0x1
[   13.378463] SKU: check_sum=0x00000000
[   13.378464] SKU: customization=0x00000000
[   13.378464] SKU: external_amp=0x0
[   13.378465] SKU: platform_type=0x0
[   13.378465] SKU: swap=0x0
[   13.378466] SKU: override=0x1
[   13.379195] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   13.379196]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   13.379197]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   13.379198]    mono: mono_out=0x0
[   13.379198]    inputs:
[   13.379200]      Mic=0x19
[   13.379201]      Internal Mic=0x12
[   13.379202] realtek: No valid SSID, checking pincfg 0x40f00001 for NID 0x1d
[   13.379203] realtek: Enabling init ASM_ID=0x0001 CODEC_ID=10ec0282
[   13.411265] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   13.411452] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   13.411631] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   15.257636] init: plymouth-upstart-bridge main process ended, respawning
[   15.338378] init: plymouth-upstart-bridge main process ended, respawning

```

Speed of built-in eMMC

```
$ sudo hdparm -tT /dev/mmcblk0

/dev/mmcblk0:
 Timing cached reads:   2274 MB in  2.00 seconds = 1136.67 MB/sec
 Timing buffered disk reads: 390 MB in  3.01 seconds = 129.77 MB/sec
```

Octane 2.0 score with Chromium:
```

Octane Score: 7872

```

---

### Post by sanderj on 2015-02-02
PS: not all is well: dmesg sometimes shows this:

```

[ 2666.946287] sdhci: Timeout waiting for Buffer Read Ready interrupt during tuning procedure, falling back to fixed sampling clock
[ 2666.948450] ------------[ cut here ]------------
[ 2666.948477] WARNING: CPU: 0 PID: 3597 at /build/buildd/linux-3.13.0/drivers/mmc/host/sdhci.c:989 sdhci_send_command+0xc32/0xd60 [sdhci]()
[ 2666.948479] Modules linked in: snd_hda_codec_hdmi snd_hda_codec_realtek rfcomm bnep nls_iso8859_1 hid_generic hp_wmi sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event intel_rapl snd_rawmidi coretemp arc4 kvm crct10dif_pclmul crc32_pclmul usbhid snd_seq hid ghash_clmulni_intel rtl8723be btcoexist cryptd snd_seq_device rtl8723_common snd_timer rtl_pci rtlwifi btusb bluetooth mac80211 serio_raw snd rtsx_pci_ms memstick i915_bdw cfg80211 intel_ips drm_kms_helper soundcore drm i2c_algo_bit wmi hp_wireless video parport_pc ppdev joydev mac_hid lp parport mmc_block rtsx_pci_sdmmc psmouse rtsx_pci sdhci_acpi sdhci
[ 2666.948522] CPU: 0 PID: 3597 Comm: chromium-browse Not tainted 3.13.0-45-generic #74-Ubuntu
[ 2666.948524] Hardware name: Hewlett-Packard HP Stream Notebook PC 13/802A, BIOS F.05 11/28/2014
[ 2666.948527]  0000000000000009 ffff880076a03d28 ffffffff81720eb6 0000000000000000
[ 2666.948531]  ffff880076a03d60 ffffffff810677cd 0000000000000002 ffff88003fb7ac00
[ 2666.948535]  ffff880071b77ad0 ffff880071b77b10 ffff88003f9b74c0 ffff880076a03d70
[ 2666.948539] Call Trace:
[ 2666.948542]  <IRQ>  [<ffffffff81720eb6>] dump_stack+0x45/0x56
[ 2666.948554]  [<ffffffff810677cd>] warn_slowpath_common+0x7d/0xa0
[ 2666.948557]  [<ffffffff810678aa>] warn_slowpath_null+0x1a/0x20
[ 2666.948564]  [<ffffffffa0003aa2>] sdhci_send_command+0xc32/0xd60 [sdhci]
[ 2666.948569]  [<ffffffff813709aa>] ? delay_tsc+0x4a/0x80
[ 2666.948573]  [<ffffffff813708dc>] ? __const_udelay+0x2c/0x30
[ 2666.948579]  [<ffffffffa0001164>] ? sdhci_reset+0xa4/0x1b0 [sdhci]
[ 2666.948585]  [<ffffffffa00043e5>] sdhci_finish_data+0x115/0x3c0 [sdhci]
[ 2666.948591]  [<ffffffffa0004c00>] sdhci_irq+0x350/0x8e3 [sdhci]
[ 2666.948596]  [<ffffffff810bfa5e>] handle_irq_event_percpu+0x3e/0x1d0
[ 2666.948600]  [<ffffffff810bfc2d>] handle_irq_event+0x3d/0x60
[ 2666.948604]  [<ffffffff810c2e4a>] handle_fasteoi_irq+0x5a/0x100
[ 2666.948608]  [<ffffffff81015e5e>] handle_irq+0x1e/0x30
[ 2666.948613]  [<ffffffff81733c9d>] do_IRQ+0x4d/0xc0
[ 2666.948618]  [<ffffffff817293ad>] common_interrupt+0x6d/0x6d
[ 2666.948619]  <EOI>  [<ffffffff81728d4b>] ? _raw_spin_unlock_irqrestore+0x1b/0x40
[ 2666.948627]  [<ffffffff810aaf80>] __wake_up_sync_key+0x50/0x60
[ 2666.948632]  [<ffffffff811c66dd>] pipe_write+0x43d/0x520
[ 2666.948637]  [<ffffffff811bd45a>] do_sync_write+0x5a/0x90
[ 2666.948641]  [<ffffffff811bdbe4>] vfs_write+0xb4/0x1f0
[ 2666.948644]  [<ffffffff811be619>] SyS_write+0x49/0xa0
[ 2666.948648]  [<ffffffff81731b7f>] tracesys+0xe1/0xe6
[ 2666.948651] ---[ end trace 6d4cc2b5a74f9ad2 ]---
[ 2666.950730] mmcblk0: error -84 transferring data, sector 36853392, nr 8, cmd response 0x0, card status 0x0
[ 2666.950736] mmcblk0: retrying using single block read

```

I'll see if I can find or file a bug report.

EDIT: bug reported [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1417263](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1417263)

---

### Post by jerrylamos on 2015-09-27
HP Stream 13 with Win 8.1 now upgraded to Win 10
Successfully boots Ubuntu Wily 15.10 from usb SSD hard drive

Looked around a bunch of sites (!) did a million monkeys on a million keyboards 
As far as I remember:
Boot, push F9 to get to bios
Turn off Security
Turn on Legacy
Boot, get to 2nd screen select Power
Shift Restart to get to boot selections mode
select Troubleshooting
select EFI device
select usb drive
Ubuntu boots O.K.

Now on subsequent boots,
quick push F9
select usb drive

If a little slow pushing F9,
select power on 2nd screen
shift Restart
then as above.

Now after an hour or so Wily Beta 2 hung 
I didn't have any swap space, the hp stream 13 comes with 2G and 2 processors
Just created a 4G swap space will try again.
Of course, Wily still in development mode so bugs may/will occur....

BTW, for what I run response is just fine.  Mostly internet & internet video, some office, and of course will do ubuntu development level downloads & installs.

---

### Post by sanderj on 2015-09-27
FWIW: I'm now running Ubuntu 15.04 on my HP Stream 13 (with updated firmeware) and it's quite OK.


However, with 3.19.0-28-generic dmesg shows these messages:
```


[ 1748.427313] Corrupted low memory at ffff8800000013d0 (13d0 phys) = 132b000000000000
[ 1748.427336] Corrupted low memory at ffff8800000013d8 (13d8 phys) = 00003306
[ 1748.427464] ------------[ cut here ]------------
[ 1748.427494] WARNING: CPU: 0 PID: 2788 at /build/linux-5xFjum/linux-3.19.0/arch/x86/kernel/check.c:140 check_for_bios_corruption+0xcb/0x120()
[ 1748.427503] Memory corruption detected in low memory
[ 1748.427512] Modules linked in: ctr ccm nls_iso8859_1 btusb hp_wmi bluetooth hid_generic sparse_keymap joydev snd_hda_codec_hdmi intel_rapl intel_soc_dts_thermal intel_powerclamp coretemp snd_hda_codec_realtek snd_hda_codec_generic kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel cryptd serio_raw uvcvideo snd_hda_intel videobuf2_vmalloc arc4 snd_intel_sst_acpi snd_hda_controller snd_soc_rt5640 snd_intel_sst_core videobuf2_memops snd_soc_sst_mfld_platform rtl8723be snd_soc_rl6231 snd_hda_codec videobuf2_core snd_soc_core btcoexist v4l2_common snd_hwdep rtl8723_common snd_compress snd_pcm_dmaengine rtl_pci videodev rtlwifi media snd_pcm mac80211 usbhid snd_seq_midi cfg80211 snd_seq_midi_event rtsx_pci_ms snd_rawmidi memstick wmi snd_seq snd_seq_device i915 dw_dmac snd_timer int3400_thermal
[ 1748.427736]  dw_dmac_core acpi_thermal_rel processor_thermal_device int3403_thermal intel_smartconnect snd video rfkill_gpio i2c_hid drm_kms_helper hid 8250_dw drm i2c_designware_platform snd_soc_sst_acpi i2c_designware_core soundcore i2c_algo_bit spi_pxa2xx_platform shpchp mei_txe pwm_lpss_platform mei pwm_lpss iosf_mbi lpc_ich mac_hid hp_wireless parport_pc ppdev lp parport autofs4 mmc_block rtsx_pci_sdmmc psmouse rtsx_pci sdhci_acpi sdhci
[ 1748.427875] CPU: 0 PID: 2788 Comm: kworker/0:2 Not tainted 3.19.0-28-generic #30-Ubuntu
[ 1748.427886] Hardware name: Hewlett-Packard HP Stream Notebook PC 13/802A, BIOS F.06 01/06/2015
[ 1748.427904] Workqueue: events check_corruption
[ 1748.427917]  ffffffff81a92cc8 ffff880066ec3cf8 ffffffff817c458f 0000000000000007
[ 1748.427936]  ffff880066ec3d48 ffff880066ec3d38 ffffffff81076a6a ffff8800000013d8
[ 1748.427954]  0000000000000000 ffff880000020000 ffffffff81ede390 0000000000000001
[ 1748.427972] Call Trace:
[ 1748.427999]  [<ffffffff817c458f>] dump_stack+0x45/0x57
[ 1748.428019]  [<ffffffff81076a6a>] warn_slowpath_common+0x8a/0xc0
[ 1748.428038]  [<ffffffff81076ae6>] warn_slowpath_fmt+0x46/0x50
[ 1748.428060]  [<ffffffff810135e0>] ? __switch_to+0x150/0x5e0
[ 1748.428081]  [<ffffffff8105d8bb>] check_for_bios_corruption+0xcb/0x120
[ 1748.428102]  [<ffffffff8105d91e>] check_corruption+0xe/0x40
[ 1748.428121]  [<ffffffff8108fd58>] process_one_work+0x158/0x430
[ 1748.428139]  [<ffffffff8109089b>] worker_thread+0x5b/0x530
[ 1748.428159]  [<ffffffff81090840>] ? rescuer_thread+0x3a0/0x3a0
[ 1748.428178]  [<ffffffff81095939>] kthread+0xc9/0xe0
[ 1748.428199]  [<ffffffff81095870>] ? kthread_create_on_node+0x1c0/0x1c0
[ 1748.428217]  [<ffffffff817cb618>] ret_from_fork+0x58/0x90
[ 1748.428237]  [<ffffffff81095870>] ? kthread_create_on_node+0x1c0/0x1c0
[ 1748.428250] ---[ end trace 9dfa2e8e4ff26320 ]---
```

and

```
[ 2831.289027] [drm:intel_pipe_update_end [i915]] *ERROR* Atomic update failure on pipe A (start=47646 end=47647)
```

---

