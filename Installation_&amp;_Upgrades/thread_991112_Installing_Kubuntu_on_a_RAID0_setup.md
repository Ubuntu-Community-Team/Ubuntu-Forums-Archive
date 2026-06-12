---
title: "Installing Kubuntu on a RAID0 setup?"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by Swooper86 on 2008-11-23
Hello.
I've been meaning to dual-boot my new (3 months old) desktop PC, currently running Vista Home Premium 32bit, with Kubuntu for a while now. A friend of mine gave me a 8.04 LiveCD earlier this autumn, and tonight I finally took the time and effort to try to install it. I followed [these](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm) instructions, knowing Ubuntu and Kubuntu are similar enough that it should work. I hit a brick wall when I got to stage 4 of 7 on the third page of that guide - choosing a partition to install Kubuntu to. Firstly, it didn't give me the option to 'use the largest continuous free space', so I tried manual. The screen I got then didn't seem very understandable, other than that I seemed to be able to choose one out of my two 500GB Samsung Spinpoint hard drives. I did not like those options, because these hard drives are currently [RAID0](http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_0)'ed together. Choosing either one would surely collapse the fragile structure that RAID0 is and destroy my Windows partition, complete with all data (although I regularly backup my files to a removable HD, it'd still hurt). After a failed attempt at googling for information, I found no quick (or understandable) solution and was forced to give up for now.

So I turn to you. I'm sure someone out there has a solution for this problem. Right?

(This was also posted [here]("http://kubuntuforums.net/forums/index.php?topic=3099697.0"), but I figure I have better odds at getting help if I post here as well.)

---

### Post by inobe on 2008-11-23
the only other alternative i know of' opensuse 11, it will detect your array as 1 TB.

ubuntu is capable of raid' it is not fully supported, raid tools are not included on the live cd, you must use the alternative cd !

the odds of that cd working for you are experimental..

us linux junkies like to use hardware raid cards, me myself' i have a 3ware pci-e card, its a cake walk installing ubuntu or any os on that, software raid (built in/ onboard ) fake raid, is software raid.

the fact that it is not supported by ubuntu' you will be faced with trial and error, that said i would look elsewhere for a raid solution.

i do believe the next release 9.04 will have full raid support

---

### Post by caljohnsmith on 2008-11-23
If you want to use Kubuntu with RAID, you might find these links helpful:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Let me know if that helps. :)

---

### Post by Swooper86 on 2008-11-23
The first link looks helpful, thanks. I'm going to wait for a chance to do it when my linux-savvy friend is online so he can talk me through it in case I run into difficulties following the directions. I'll let you know if it works!

Edit: Change of plans. I'm gonna try the 8.10 alternate install CD, which supposedly comes with RAID support. Burning now.:-)

---

### Post by inobe on 2008-11-23
personally i would avoid it and use a distribution that **supports** soft/hybrid arrays !

---

### Post by Swooper86 on 2008-11-23
The 8.10 version is supposed to have enhanced RAID support over 8.04 according to [this]("https://wiki.ubuntu.com/DmraidSupport").

However, I just tried it, and sadly it didn't work. Installation failed when it got to the 'Detect disks' part of the install procedure. These are the messages I got:
> One or more drives containing Serial ATA RAID configurations have been found. Do you wish to activate these RAID devices?

Activate Serial ATA RAID devices?

<Go Back>     <Yes>  <No>
And the next step, after selecting <Yes>:
> An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Detect disks.

<Continue>
Do I have any options save waiting for 9.04, trying another Linux distro (which doesn't sound all that appealing) or trying Method 2 from [here]("https://help.ubuntu.com/community/FakeRaidHowto")?

---

### Post by inobe on 2008-11-23
if you searched the forum for raid0' you would notice a lot of failures, their are advanced setups that can still fail and need to be tested first !

opensuse is a fantastic distro and raid is fully supported' however ubuntu is one of the greatest but lacks that support.

if you don't wish to use another distribution' i will suggest waiting.

i am not trying to scare you off, i am simply trying to help :)

---

### Post by psusi on 2008-11-23
There is a known bug in the version of dmraid that shipped in Intrepid that causes it to fail to activate raid sets on Intel Software Matrix Raid controllers when you define more than one raid volume in the bios.  Do you have such a setup?

---

### Post by Swooper86 on 2008-11-23
I only have one defined RAID volume so nope (surely the unallocated space doesn't matter, right?). I am using the on-board RAID feature of an Intel motherboard however, it's a Gigabyte S775 GA-X38-DS4.

In case it matters in some way, here's the rest of my setup:

**Intel Core 2 Duo E8500** 3.16GHz CPU
2x**2GB 800MHz Corsair** RAM
2x **ATI Radeon HD4850 512MB** GPUs, Crossfire'd together
2x **500GB SATA2 Samsung Spinpoint F1** hard disks in aforementioned RAID0 array, 789.01GB allocated in a single NTFS partition running 32bit Windows Vista Home Premium, 142.51GB unallocated (thought it was 146 but oh well).

---

### Post by psusi on 2008-11-23
Post the output of sudo dmraid -tay -vvvv -dddd

---

### Post by Swooper86 on 2008-11-23
Will do tomorrow, however, it's 3am here so I should sleep.

---

### Post by Swooper86 on 2008-11-24
Well that didn't work - the Alternate Install CD doesn't work as a Live CD so I can't access the OS from it, and the 8.10 Live CD doesn't have RAID support included.

Now what? :confused:

---

### Post by psusi on 2008-11-24
Install the dmraid package on the livecd, or you can just switch to a terminal in the alternate cd to do it.  Hit alt and either left/right arrow keys to cycle through the terminals, or alt-Fn to switch to a specific one.  The first one should be the default one with the installer running on it, one of them should have debugging output from the installer, and one of them should be sitting at a login prompt.

---

### Post by Swooper86 on 2008-11-24
Oh great. I booted from the alternate CD and found the terminal after some fidgeting. Running the command you gave me outputs:

/bin/sh: dmraid: not found

I tried alt+arrow key to change terminal, found one other terminal and got the same result. I then typed in 'shutdown' to exit the terminal and restarted. Now I get:

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

when I try to boot my PC normally :( What the hell did I do!?

---

### Post by psusi on 2008-11-24
That's really strange.  You shouldn't have done anything that would modify the drives.  Did you try a cold boot?  And dmraid HAS to be installed in the alternate cd.

---

### Post by Swooper86 on 2008-11-24
Very strange yes, I didn't think I had access to changing anything but the RAM with that cd except if I chose to actually install from it, which I most certainly didn't. The only thing I can think of that I did which might possibly have affected it (and only because I didn't understand exactly what it was) is pressing F6 in the Kubuntu equivalent of [this screen]("http://apcmag.com/images/apcapc/howto/Dualboot_-_Vista___Ubuntu__Vista_first__images/ubuntu_01.jpg"). It showed a (to me) unintelligible CLI linux command which I don't remember but I guess I can find it again by booting from the cd. Hitting Enter gave me the terminal where I ran your command.

And yeah, cold boot was the first thing I tried.

---

### Post by Swooper86 on 2008-11-24
Thank god, set the boot order back to HD->CD->* and it starts up again. That leaves me back on square one. Still no Kubuntu on my RAID array :(

---

### Post by psusi on 2008-11-24
Run dmraid -tay -dddd -vvvv ( from the livecd if you have to ) and post the output.

---

### Post by Swooper86 on 2008-11-25
This is after getting dmraid working on the 8.04 live cd:
> ubuntu@ubuntu:~$ dmraid -tay -vvvv -dddd
NOTICE: creating directory /var/lock/dmraid
ERROR: you must be root
I used my limited linux knowledge to realise 'sudo' was missing there. The results of that:
> ubuntu@ubuntu:~$ sudo dmraid -tay -vvvv -dddd
WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: isw metadata discovered
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
DEBUG: _find_set: searching isw_gajjjcjci
DEBUG: _find_set: not found isw_gajjjcjci
DEBUG: _find_set: searching isw_gajjjcjci_Volume0
DEBUG: _find_set: searching isw_gajjjcjci_Volume0
DEBUG: _find_set: not found isw_gajjjcjci_Volume0
DEBUG: _find_set: not found isw_gajjjcjci_Volume0
NOTICE: added /dev/sdb to RAID set "isw_gajjjcjci"
DEBUG: checking isw device "/dev/sdb"
ERROR: isw device for volume "Volume0" broken on /dev/sdb in RAID set "isw_gajjjcjci_Volume0"
ERROR: isw: wrong # of devices in RAID set "isw_gajjjcjci_Volume0" [1/2] on /dev/sdb
DEBUG: set status of set "isw_gajjjcjci_Volume0" to 2
DEBUG: set status of set "isw_gajjjcjci" to 4
isw_gajjjcjci_Volume0: 0 976766208 linear /dev/zero 0
INFO: Activating GROUP RAID set "isw_gajjjcjci"
WARN: unlocking /var/lock/dmraid/.lock
DEBUG: freeing devices of RAID set "isw_gajjjcjci_Volume0"
DEBUG: freeing device "isw_gajjjcjci_Volume0", path "/dev/sdb"
DEBUG: freeing devices of RAID set "isw_gajjjcjci"
DEBUG: freeing device "isw_gajjjcjci", path "/dev/sdb"
I'm gonna leave the live cd running now and wait for further instructions...

Edit: Also, /dev/mapper is empty apart from something called 'control'. According to [this]("https://help.ubuntu.com/community/FakeRaidHowto"), that's not good.

---

### Post by psusi on 2008-11-25
Hrm... it isn't recognizing the raid signature on sda.  Post the output of dmesg.  My guess is that you have one of those damn motherboards that uses the host protected area to make the disk pretend it is smaller than it really is for no good reason.  In 8.04 the kernel ignores this and uses the real size of the disk by default, but because the bios respects the pretend size, it places the metadata in the wrong place.  8.10 should work if this is the case since it respects the HPA by default.

---

### Post by Swooper86 on 2008-11-25
dmesg output:
```
ubuntu@ubuntu:/dev/mapper$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.
3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19
.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000096c00 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a HIGHMEM64G enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f52b0
[    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->  1048576
[    0.000000] On node 0 totalpages: 1048576
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 6400 pages used for memmap
[    0.000000]   HighMem zone: 812800 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6CA0 checksum 0
[    0.000000] ACPI: RSDP 000F6CA0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT CFEE3040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010
101)
[    0.000000] ACPI: FACP CFEE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010
101)
[    0.000000] ACPI: DSDT CFEE3180, 4BC9 (r1 GBT    GBTUACPI     1000 MSFT  1000
00C)
[    0.000000] ACPI: FACS CFEE0000, 0040
[    0.000000] ACPI: HPET CFEE7EC0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU
 98)
[    0.000000] ACPI: MCFG CFEE7F40, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010
101)
[    0.000000] ACPI: APIC CFEE7DC0, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010
101)
[    0.000000] ACPI: SSDT CFEE7FC0, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040
311)
[    0.000000] ACPI: SSDT CFEE8450, 0275 (r1  PmRef    CpuPm     3000 INTL 20040
311)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 7:7 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 7:7 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at d0000000 (gap: cff00000:2010
0000)
[    0.000000] swsusp: Registered nosave memory region: 0000000000096000 - 00000
000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000
000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 00000
00000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pag
es: 1040384
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/prese
ed/kubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3166.423 MHz processor.
[   53.711006] Console: colour VGA+ 80x25
[   53.711008] console [tty0] enabled
[   53.711143] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   53.711294] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   53.816055] Memory: 3359692k/4194304k available (2177k kernel code, 45728k re
served, 1006k data, 368k init, 2489216k highmem)
[   53.816059] virtual kernel memory layout:
[   53.816060]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   53.816061]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   53.816061]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   53.816062]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   53.816062]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   53.816063]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   53.816063]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   53.816065] Checking if this processor honours the WP bit even in supervisor
mode... Ok.
[   53.816089] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, N
odes=1
[   53.816170] hpet clockevent registered
[   53.896074] Calibrating delay using timer specific routine.. 6336.78 BogoMIPS
 (lpj=12673576)
[   53.896086] Security Framework initialized
[   53.896090] SELinux:  Disabled at boot.
[   53.896097] AppArmor: AppArmor initialized
[   53.896099] Failure registering capabilities with primary security module.
[   53.896104] Mount-cache hash table entries: 512
[   53.896175] Initializing cgroup subsys ns
[   53.896178] Initializing cgroup subsys cpuacct
[   53.896184] CPU: After generic identify, caps: bfebfbff 20100000 00000000 000
00000 0008e3fd 00000000 00000001 00000000
[   53.896188] monitor/mwait feature present.
[   53.896189] using mwait in idle threads.
[   53.896191] CPU: L1 I cache: 32K, L1 D cache: 32K
[   53.896192] CPU: L2 cache: 6144K
[   53.896194] CPU: Physical Processor ID: 0
[   53.896194] CPU: Processor Core ID: 0
[   53.896195] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0
008e3fd 00000000 00000001 00000000
[   53.896200] Compat vDSO mapped to ffffe000.
[   53.896207] Checking 'hlt' instruction... OK.
[   53.912351] SMP alternatives: switching to UP code
[   53.913393] Early unpacking initramfs... done
[   54.110964] ACPI: Core revision 20070126
[   54.110988] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not
found.
[   54.113003] CPU0: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz stepping 06
[   54.113014] SMP alternatives: switching to SMP code
[   54.113528] Booting processor 1/1 eip 3000
[   54.123958] Initializing CPU#1
[   54.203682] Calibrating delay using timer specific routine.. 6332.57 BogoMIPS
 (lpj=12665149)
[   54.203686] CPU: After generic identify, caps: bfebfbff 20100000 00000000 000
00000 0008e3fd 00000000 00000001 00000000
[   54.203689] monitor/mwait feature present.
[   54.203691] CPU: L1 I cache: 32K, L1 D cache: 32K
[   54.203692] CPU: L2 cache: 6144K
[   54.203693] CPU: Physical Processor ID: 0
[   54.203694] CPU: Processor Core ID: 1
[   54.203695] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0
008e3fd 00000000 00000001 00000000
[   54.204471] CPU1: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz stepping 06
[   54.204483] Total of 2 processors activated (12669.36 BogoMIPS).
[   54.204619] ENABLING IO-APIC IRQs
[   54.204774] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   54.351562] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   54.371546] Brought up 2 CPUs
[   54.371562] CPU0 attaching sched-domain:
[   54.371564]  domain 0: span 03
[   54.371565]   groups: 01 02
[   54.371566] CPU1 attaching sched-domain:
[   54.371567]  domain 0: span 03
[   54.371568]   groups: 02 01
[   54.371687] net_namespace: 64 bytes
[   54.371694] Booting paravirtualized kernel on bare hardware
[   54.371936] Time: 17:30:09  Date: 11/25/08
[   54.371951] NET: Registered protocol family 16
[   54.372047] EISA bus registered
[   54.372049] ACPI: bus type pci registered
[   54.377758] PCI: PCI BIOS revision 3.00 entry at 0xfb400, last bus=6
[   54.377759] PCI: Using configuration type 1
[   54.377773] Setting up standard PCI resources
[   54.380983] ACPI: EC: Look up EC in DSDT
[   54.383983] ACPI: Interpreter enabled
[   54.383987] ACPI: (supports S0 S3 S4 S5)
[   54.383997] ACPI: Using IOAPIC for interrupt routing
[   54.386677] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   54.387232] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   54.387234] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   54.387934] PCI: Transparent bridge - 0000:00:1e.0
[   54.387958] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   54.388037] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   54.388076] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   54.388117] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[   54.388155] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   54.396678] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15
)
[   54.396733] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15
)
[   54.396786] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15
)
[   54.396839] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 *15
)
[   54.396893] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15)
 *0, disabled.
[   54.396946] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15
)
[   54.396999] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 *14 15
)
[   54.397053] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15
)
[   54.397117] Linux Plug and Play Support v0.97 (c) Adam Belay
[   54.397132] pnp: PnP ACPI init
[   54.397136] ACPI: bus type pnp registered
[   54.398421] pnpacpi: exceeded the max number of mem resources: 12
[   54.398492] pnp: PnP ACPI: found 13 devices
[   54.398493] ACPI: ACPI bus type pnp unregistered
[   54.398496] PnPBIOS: Disabled by ACPI PNP
[   54.398609] PCI: Using ACPI for IRQ routing
[   54.398611] PCI: If a device doesn't work, try "pci=routeirq".  If it helps,
post a report
[   54.451380] NET: Registered protocol family 8
[   54.451382] NET: Registered protocol family 20
[   54.451408] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   54.451411] hpet0: 4 64-bit timers, 14318180 Hz
[   54.452433] AppArmor: AppArmor Filesystem Enabled
[   54.455370] Time: tsc clocksource has been installed.
[   54.455376] Switched to high resolution mode on CPU 0
[   54.455439] Switched to high resolution mode on CPU 1
[   54.471347] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   54.471349] system 00:01: ioport range 0x290-0x29f has been reserved
[   54.471352] system 00:01: ioport range 0x800-0x87f has been reserved
[   54.471354] system 00:01: ioport range 0x290-0x294 has been reserved
[   54.471357] system 00:01: ioport range 0x880-0x88f has been reserved
[   54.471366] system 00:09: ioport range 0x400-0x4bf could not be reserved
[   54.471371] system 00:0a: iomem range 0xf0000000-0xf3ffffff could not be rese
rved
[   54.471375] system 00:0b: iomem range 0xd7200-0xd7fff has been reserved
[   54.471378] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[   54.471380] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[   54.471382] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[   54.471384] system 00:0b: iomem range 0xcfee0000-0xcfefffff could not be rese
rved
[   54.471386] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   54.471389] system 00:0b: iomem range 0x100000-0xcfedffff could not be reserv
ed
[   54.471391] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be rese
rved
[   54.471393] system 00:0b: iomem range 0xfed10000-0xfed1dfff could not be rese
rved
[   54.471395] system 00:0b: iomem range 0xfed20000-0xfed8ffff could not be rese
rved
[   54.471398] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be rese
rved
[   54.471400] system 00:0b: iomem range 0xffb00000-0xffb7ffff could not be rese
rved
[   54.501594] PCI: Bridge: 0000:00:01.0
[   54.501595]   IO window: a000-afff
[   54.501597]   MEM window: f6000000-f7ffffff
[   54.501599]   PREFETCH window: d0000000-dfffffff
[   54.501601] PCI: Bridge: 0000:00:06.0
[   54.501602]   IO window: b000-bfff
[   54.501603]   MEM window: f4000000-f5ffffff
[   54.501605]   PREFETCH window: e0000000-efffffff
[   54.501607] PCI: Bridge: 0000:00:1c.0
[   54.501608]   IO window: 9000-9fff
[   54.501611]   MEM window: disabled.
[   54.501613]   PREFETCH window: disabled.
[   54.501615] PCI: Bridge: 0000:00:1c.3
[   54.501617]   IO window: c000-cfff
[   54.501620]   MEM window: fa000000-fa0fffff
[   54.501622]   PREFETCH window: disabled.
[   54.501625] PCI: Bridge: 0000:00:1c.5
[   54.501626]   IO window: d000-dfff
[   54.501629]   MEM window: f8000000-f9ffffff
[   54.501631]   PREFETCH window: fa200000-fa2fffff
[   54.501634] PCI: Bridge: 0000:00:1e.0
[   54.501635]   IO window: 8000-8fff
[   54.501638]   MEM window: disabled.
[   54.501640]   PREFETCH window: disabled.
[   54.501648] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ
 16
[   54.501650] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   54.501655] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 16 (level, low) -> IRQ
 16
[   54.501657] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   54.501668] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ
 16
[   54.501671] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   54.501682] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ
 17
[   54.501685] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   54.501697] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ
 18
[   54.501699] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   54.501706] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   54.501712] NET: Registered protocol family 2
[   54.539279] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   54.539411] TCP established hash table entries: 131072 (order: 8, 1048576 byt
es)
[   54.539631] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   54.539733] TCP: Hash tables configured (established 131072 bind 65536)
[   54.539734] TCP reno registered
[   54.551306] checking if image is initramfs... it is
[   54.941288] Freeing initrd memory: 7939k freed
[   54.941694] audit: initializing netlink socket (disabled)
[   54.941703] audit(1227634209.001:1): initialized
[   54.941861] highmem bounce pool size: 64 pages
[   54.942851] VFS: Disk quotas dquot_6.5.1
[   54.942889] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   54.942958] io scheduler noop registered
[   54.942959] io scheduler anticipatory registered
[   54.942960] io scheduler deadline registered
[   54.942967] io scheduler cfq registered (default)
[   54.943063] Boot video device is 0000:01:00.0
[   54.943120] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   54.943139] assign_interrupt_mode Found MSI capability
[   54.943155] Allocate Port Service[0000:00:01.0:pcie00]
[   54.943194] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   54.943212] assign_interrupt_mode Found MSI capability
[   54.943226] Allocate Port Service[0000:00:06.0:pcie00]
[   54.943264] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   54.943292] assign_interrupt_mode Found MSI capability
[   54.943313] Allocate Port Service[0000:00:1c.0:pcie00]
[   54.943329] Allocate Port Service[0000:00:1c.0:pcie02]
[   54.943377] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   54.943404] assign_interrupt_mode Found MSI capability
[   54.943425] Allocate Port Service[0000:00:1c.3:pcie00]
[   54.943442] Allocate Port Service[0000:00:1c.3:pcie02]
[   54.943490] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   54.943517] assign_interrupt_mode Found MSI capability
[   54.943539] Allocate Port Service[0000:00:1c.5:pcie00]
[   54.943556] Allocate Port Service[0000:00:1c.5:pcie02]
[   54.943686] isapnp: Scanning for PnP cards...
[   55.296197] isapnp: No Plug & Play device found
[   55.308675] Real Time Clock Driver v1.12ac
[   55.308770] hpet_resources: 0xfed00000 is busy
[   55.308792] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing
enabled
[   55.308880] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   55.309201] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   55.309574] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bloc
ksize
[   55.309608] input: Macintosh mouse button emulation as /devices/virtual/input
/input0
[   55.309677] PNP: No PS/2 controller found. Probing ports directly.
[   55.309953] serio: i8042 KBD port at 0x60,0x64 irq 1
[   55.309957] serio: i8042 AUX port at 0x60,0x64 irq 12
[   55.322315] mice: PS/2 mouse device common for all mice
[   55.322394] EISA: Probing bus 0 at eisa.0
[   55.322412] Cannot allocate resource for EISA slot 8
[   55.322413] EISA: Detected 0 cards.
[   55.322414] cpuidle: using governor ladder
[   55.322415] cpuidle: using governor menu
[   55.322453] NET: Registered protocol family 1
[   55.322467] Using IPI No-Shortcut mode
[   55.322480] registered taskstats version 1
[   55.322542]   Magic number: 0:192:543
[   55.322557] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   55.322558] EDD information not available.
[   55.322658] Freeing unused kernel memory: 368k freed
[   56.431332] fuse init (API version 7.9)
[   56.443381] ACPI: Processor [CPU0] (supports 8 throttling states)
[   56.443447] ACPI: SSDT CFEE83C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040
311)
[   56.443522] ACPI: Processor [CPU1] (supports 8 throttling states)
[   56.443529] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Dev
ice is not present [20070126]
[   56.443535] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Dev
ice is not present [20070126]
[   56.601678] usbcore: registered new interface driver usbfs
[   56.601690] usbcore: registered new interface driver hub
[   56.607105] usbcore: registered new device driver usb
[   56.607995] USB Universal Host Controller Interface driver v3.0
[   56.608026] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ
 16
[   56.608033] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   56.608035] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   56.608148] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus numbe
r 1
[   56.608169] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e100
[   56.608233] usb usb1: configuration #1 chosen from 1 choice
[   56.608245] hub 1-0:1.0: USB hub found
[   56.608247] hub 1-0:1.0: 2 ports detected
[   56.630185] SCSI subsystem initialized
[   56.646177] libata version 3.00 loaded.
[   56.712559] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ
 19
[   56.712567] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   56.712570] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   56.712582] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus numbe
r 2
[   56.712602] uhci_hcd 0000:00:1a.1: irq 19, io base 0x0000e200
[   56.712661] usb usb2: configuration #1 chosen from 1 choice
[   56.712673] hub 2-0:1.0: USB hub found
[   56.712676] hub 2-0:1.0: 2 ports detected
[   56.816407] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ
 20
[   56.816412] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   56.816415] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   56.816425] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus numbe
r 3
[   56.816444] uhci_hcd 0000:00:1a.2: irq 20, io base 0x0000e000
[   56.816498] usb usb3: configuration #1 chosen from 1 choice
[   56.816512] hub 3-0:1.0: USB hub found
[   56.816514] hub 3-0:1.0: 2 ports detected
[   56.916358] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ
 20
[   56.916366] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   56.916368] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   56.916379] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus numbe
r 4
[   56.920279] PCI: cache line size of 32 is not supported by device 0000:00:1a.
7
[   56.920281] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfa104000
[   56.948195] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   56.961178] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec
2004
[   56.961250] usb usb4: configuration #1 chosen from 1 choice
[   56.961270] hub 4-0:1.0: USB hub found
[   56.961274] hub 4-0:1.0: 6 ports detected
[   57.064100] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ
 21
[   57.064107] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   57.064110] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   57.064127] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus numbe
r 5
[   57.068015] PCI: cache line size of 32 is not supported by device 0000:00:1d.
7
[   57.068019] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xfa105000
[   57.080026] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec
2004
[   57.080103] usb usb5: configuration #1 chosen from 1 choice
[   57.080120] hub 5-0:1.0: USB hub found
[   57.080124] hub 5-0:1.0: 6 ports detected
[   57.183942] r8169 Gigabit Ethernet driver 2.2LK loaded
[   57.183961] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 17 (level, low) -> IRQ
 18
[   57.183973] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   57.184171] eth0: RTL8168b/8111b at 0xf8884000, 00:1d:7d:00:80:9d, XID 380000
00 IRQ 218
[   57.185246] ahci 0000:00:1f.2: version 3.0
[   57.185258] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ
 17
[   57.671272] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   57.847696] usb 1-2: configuration #1 chosen from 1 choice
[   58.186636] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f im
pl RAID mode
[   58.186639] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio
slum part
[   58.186643] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   58.186853] scsi0 : ahci
[   58.186933] scsi1 : ahci
[   58.187006] scsi2 : ahci
[   58.187082] scsi3 : ahci
[   58.187159] scsi4 : ahci
[   58.187240] scsi5 : ahci
[   58.187291] ata1: SATA max UDMA/133 abar m2048@0xfa106000 port 0xfa106100 irq
 217
[   58.187293] ata2: SATA max UDMA/133 abar m2048@0xfa106000 port 0xfa106180 irq
 217
[   58.187294] ata3: SATA max UDMA/133 abar m2048@0xfa106000 port 0xfa106200 irq
 217
[   58.187296] ata4: SATA max UDMA/133 abar m2048@0xfa106000 port 0xfa106280 irq
 217
[   58.187297] ata5: SATA max UDMA/133 abar m2048@0xfa106000 port 0xfa106300 irq
 217
[   58.187299] ata6: SATA max UDMA/133 abar m2048@0xfa106000 port 0xfa106380 irq
 217
[   58.825803] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   58.838419] ata1.00: HPA unlocked: 976771055 -> 976773168, native 976773168
[   58.838422] ata1.00: ATA-7: SAMSUNG HD502IJ, 1AA01112, max UDMA7
[   58.838425] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   58.844802] ata1.00: configured for UDMA/133
[   59.480968] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   59.487281] ata2.00: ATA-7: SAMSUNG HD502IJ, 1AA01112, max UDMA7
[   59.487283] ata2.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   59.493654] ata2.00: configured for UDMA/133
[   59.812546] ata3: SATA link down (SStatus 0 SControl 300)
[   60.451729] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   60.608376] ata4.00: ATAPI: TSSTcorp CDDVDW SH-S203D, SB00, max UDMA/100, ATA
PI AN
[   60.764182] ata4.00: configured for UDMA/100
[   61.082927] ata5: SATA link down (SStatus 0 SControl 300)
[   61.402519] ata6: SATA link down (SStatus 0 SControl 300)
[   61.402607] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD502IJ  1AA0 PQ
: 0 ANSI: 5
[   61.402679] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD502IJ  1AA0 PQ
: 0 ANSI: 5
[   61.403220] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203D  SB00 PQ
: 0 ANSI: 5
[   61.403284] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ
 17
[   62.405260] ahci 0000:04:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 imp
l SATA mode
[   62.405263] ahci 0000:04:00.0: flags: 64bit ncq pm led clo pmp pio slum part
[   62.405268] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   62.405358] scsi6 : ahci
[   62.405473] scsi7 : ahci
[   62.405501] ata7: SATA max UDMA/133 abar m8192@0xfa000000 port 0xfa000100 irq
 17
[   62.405504] ata8: SATA max UDMA/133 abar m8192@0xfa000000 port 0xfa000180 irq
 17
[   62.724842] ata7: SATA link down (SStatus 0 SControl 300)
[   63.044435] ata8: SATA link down (SStatus 0 SControl 300)
[   63.044484] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ
 21
[   63.044491] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   63.044494] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   63.044512] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus numbe
r 6
[   63.044536] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000e300
[   63.044592] usb usb6: configuration #1 chosen from 1 choice
[   63.044604] hub 6-0:1.0: USB hub found
[   63.044606] hub 6-0:1.0: 2 ports detected
[   63.050092] Driver 'sd' needs updating - please use bus_type methods
[   63.050123] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   63.050129] sd 0:0:0:0: [sda] Write Protect is off
[   63.050130] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   63.050138] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[   63.050162] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   63.050167] sd 0:0:0:0: [sda] Write Protect is off
[   63.050168] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   63.050176] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[   63.050177]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   63.055222]  sda1
[   63.055225]  sda: p1 exceeds device capacity
[   63.055265] sd 0:0:0:0: [sda] Attached SCSI disk
[   63.055301] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   63.055309] sd 1:0:0:0: [sdb] Write Protect is off
[   63.055311] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   63.055326] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[   63.055347] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   63.055352] sd 1:0:0:0: [sdb] Write Protect is off
[   63.055353] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   63.055361] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[   63.055363]  sdb: unknown partition table
[   63.065822] sd 1:0:0:0: [sdb] Attached SCSI disk
[   63.069237] sr0: scsi3-mmc drive: 32x/40x writer dvd-ram cd/rw xa/form2 cdda
tray
[   63.069239] Uniform CD-ROM driver Revision: 3.20
[   63.069268] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   63.071709] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   63.071718] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   63.071727] sr 3:0:0:0: Attached scsi generic sg2 type 5
[   63.149353] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ
 17
[   63.149361] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   63.149364] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   63.149380] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus numbe
r 7
[   63.149404] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e400
[   63.149463] usb usb7: configuration #1 chosen from 1 choice
[   63.149476] hub 7-0:1.0: USB hub found
[   63.149479] hub 7-0:1.0: 2 ports detected
[   63.182116] attempt to access beyond end of device
[   63.182119] sda: rw=0, want=1654667016, limit=976773168
[   63.182121] Buffer I/O error on device sda1, logical block 206833120
[   63.182124] attempt to access beyond end of device
[   63.182126] sda: rw=0, want=1654667016, limit=976773168
[   63.182128] Buffer I/O error on device sda1, logical block 206833120
[   63.182135] attempt to access beyond end of device
[   63.182137] sda: rw=0, want=1654667248, limit=976773168
[   63.182139] Buffer I/O error on device sda1, logical block 206833149
[   63.182141] attempt to access beyond end of device
[   63.182142] sda: rw=0, want=1654667248, limit=976773168
[   63.182144] Buffer I/O error on device sda1, logical block 206833149
[   63.182174] attempt to access beyond end of device
[   63.182176] sda: rw=0, want=1654667256, limit=976773168
[   63.182178] Buffer I/O error on device sda1, logical block 206833150
[   63.182180] attempt to access beyond end of device
[   63.182182] sda: rw=0, want=1654667256, limit=976773168
[   63.182184] Buffer I/O error on device sda1, logical block 206833150
[   63.182190] attempt to access beyond end of device
[   63.182191] sda: rw=0, want=1654667256, limit=976773168
[   63.182193] Buffer I/O error on device sda1, logical block 206833150
[   63.182198] attempt to access beyond end of device
[   63.182205] sda: rw=0, want=1654667256, limit=976773168
[   63.182206] Buffer I/O error on device sda1, logical block 206833150
[   63.182209] attempt to access beyond end of device
[   63.182210] sda: rw=0, want=1654667256, limit=976773168
[   63.182212] Buffer I/O error on device sda1, logical block 206833150
[   63.182215] attempt to access beyond end of device
[   63.182216] sda: rw=0, want=1654667256, limit=976773168
[   63.182217] Buffer I/O error on device sda1, logical block 206833150
[   63.182221] attempt to access beyond end of device
[   63.182222] sda: rw=0, want=1654667256, limit=976773168
[   63.182225] attempt to access beyond end of device
[   63.182226] sda: rw=0, want=1654667200, limit=976773168
[   63.182229] attempt to access beyond end of device
[   63.182230] sda: rw=0, want=1654667248, limit=976773168
[   63.182234] attempt to access beyond end of device
[   63.182235] sda: rw=0, want=1654667256, limit=976773168
[   63.182238] attempt to access beyond end of device
[   63.182239] sda: rw=0, want=1654667256, limit=976773168
[   63.253210] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ
 20
[   63.253216] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   63.253219] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   63.253235] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus numbe
r 8
[   63.253254] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000e500
[   63.253317] usb usb8: configuration #1 chosen from 1 choice
[   63.253328] hub 8-0:1.0: USB hub found
[   63.253331] hub 8-0:1.0: 2 ports detected
[   63.357778] PCI: Enabling device 0000:04:00.1 (0000 -> 0001)
[   63.357782] ACPI: PCI Interrupt 0000:04:00.1[B] -> GSI 16 (level, low) -> IRQ
 16
[   63.357803] PCI: Setting latency timer of device 0000:04:00.1 to 64
[   63.357812] ACPI: PCI interrupt for device 0000:04:00.1 disabled
[   63.359397] ACPI: PCI Interrupt 0000:04:00.1[B] -> GSI 16 (level, low) -> IRQ
 16
[   63.359415] PCI: Setting latency timer of device 0000:04:00.1 to 64
[   63.359623] scsi8 : pata_jmicron
[   63.359885] scsi9 : pata_jmicron
[   63.360153] ata9: PATA max UDMA/100 cmd 0xc000 ctl 0xc100 bmdma 0xc400 irq 16
[   63.360155] ata10: PATA max UDMA/100 cmd 0xc200 ctl 0xc300 bmdma 0xc408 irq 1
6
[   63.595720] usb 8-2: new low speed USB device using uhci_hcd and address 2
[   63.748719] attempt to access beyond end of device
[   63.748722] sda: rw=0, want=1654667016, limit=976773168
[   63.748724] attempt to access beyond end of device
[   63.748726] sda: rw=0, want=1654667016, limit=976773168
[   63.748733] attempt to access beyond end of device
[   63.748735] sda: rw=0, want=1654667248, limit=976773168
[   63.748737] attempt to access beyond end of device
[   63.748739] sda: rw=0, want=1654667248, limit=976773168
[   63.748769] attempt to access beyond end of device
[   63.748771] sda: rw=0, want=1654667256, limit=976773168
[   63.748773] attempt to access beyond end of device
[   63.748775] sda: rw=0, want=1654667256, limit=976773168
[   63.748781] attempt to access beyond end of device
[   63.748782] sda: rw=0, want=1654667256, limit=976773168
[   63.748788] attempt to access beyond end of device
[   63.748789] sda: rw=0, want=1654667256, limit=976773168
[   63.748794] attempt to access beyond end of device
[   63.748796] sda: rw=0, want=1654667256, limit=976773168
[   63.748801] attempt to access beyond end of device
[   63.748803] sda: rw=0, want=1654667256, limit=976773168
[   63.748812] attempt to access beyond end of device
[   63.748813] sda: rw=0, want=1654667256, limit=976773168
[   63.748817] attempt to access beyond end of device
[   63.748818] sda: rw=0, want=1654667200, limit=976773168
[   63.748821] attempt to access beyond end of device
[   63.748822] sda: rw=0, want=1654667248, limit=976773168
[   63.748825] attempt to access beyond end of device
[   63.748826] sda: rw=0, want=1654667256, limit=976773168
[   63.748829] attempt to access beyond end of device
[   63.748830] sda: rw=0, want=1654667256, limit=976773168
[   63.775699] usb 8-2: configuration #1 chosen from 1 choice
[   63.778722] usbcore: registered new interface driver hiddev
[   63.794327] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/000
0:00:1a.0/usb1/1-2/1-2:1.0/input/input1
[   63.823456] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mou
se] on usb-0000:00:1a.0-2
[   63.836693] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000
:00:1d.2/usb8/8-2/8-2:1.0/input/input2
[   63.847413] input,hidraw1: USB HID v1.10 Keyboard [Logitech Logitech USB Keyb
oard] on usb-0000:00:1d.2-2
[   63.878554] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000
:00:1d.2/usb8/8-2/8-2:1.1/input/input3
[   63.896351] input,hidraw2: USB HID v1.10 Device [Logitech Logitech USB Keyboa
rd] on usb-0000:00:1d.2-2
[   63.896360] usbcore: registered new interface driver usbhid
[   63.896363] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:US
B HID core driver
[   64.201741] ISO 9660 Extensions: Microsoft Joliet Level 3
[   64.242881] ISO 9660 Extensions: RRIP_1991A
[   64.495637] Registering unionfs 1.4
[   64.495638] unionfs: debugging is not enabled
[   64.500524] loop: module loaded
[   64.761487] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   86.473170] attempt to access beyond end of device
[   86.473172] sda: rw=0, want=1654667016, limit=976773168
[   86.473173] printk: 20 messages suppressed.
[   86.473175] Buffer I/O error on device sda1, logical block 206833120
[   86.473177] attempt to access beyond end of device
[   86.473178] sda: rw=0, want=1654667016, limit=976773168
[   86.473180] Buffer I/O error on device sda1, logical block 206833120
[   86.473184] attempt to access beyond end of device
[   86.473185] sda: rw=0, want=1654667248, limit=976773168
[   86.473186] Buffer I/O error on device sda1, logical block 206833149
[   86.473188] attempt to access beyond end of device
[   86.473189] sda: rw=0, want=1654667248, limit=976773168
[   86.473190] Buffer I/O error on device sda1, logical block 206833149
[   86.473209] attempt to access beyond end of device
[   86.473211] sda: rw=0, want=1654667256, limit=976773168
[   86.473212] attempt to access beyond end of device
[   86.473213] sda: rw=0, want=1654667256, limit=976773168
[   86.473217] attempt to access beyond end of device
[   86.473218] sda: rw=0, want=1654667256, limit=976773168
[   86.473221] attempt to access beyond end of device
[   86.473222] sda: rw=0, want=1654667256, limit=976773168
[   86.473225] attempt to access beyond end of device
[   86.473226] sda: rw=0, want=1654667256, limit=976773168
[   86.473229] attempt to access beyond end of device
[   86.473230] sda: rw=0, want=1654667256, limit=976773168
[   86.473234] attempt to access beyond end of device
[   86.473235] sda: rw=0, want=1654667256, limit=976773168
[   86.473238] attempt to access beyond end of device
[   86.473239] sda: rw=0, want=1654667200, limit=976773168
[   86.473242] attempt to access beyond end of device
[   86.473243] sda: rw=0, want=1654667248, limit=976773168
[   86.473247] attempt to access beyond end of device
[   86.473248] sda: rw=0, want=1654667256, limit=976773168
[   86.473251] attempt to access beyond end of device
[   86.473252] sda: rw=0, want=1654667256, limit=976773168
[   99.241861] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   99.825144] iTCO_vendor_support: vendor-support=0
[  100.276095] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  100.277685] input: PC Speaker as /devices/platform/pcspkr/input/input4
[  100.279536] input: Power Button (FF) as /devices/virtual/input/input5
[  100.365864] ACPI: Power Button (FF) [PWRF]
[  100.365909] input: Power Button (CM) as /devices/virtual/input/input6
[  100.373065] parport_pc 00:08: reported by Plug and Play ACPI
[  100.373104] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  100.408827] ACPI: Power Button (CM) [PWRB]
[  100.499060] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[  100.522306] attempt to access beyond end of device
[  100.522309] sda: rw=0, want=1654667016, limit=976773168
[  100.522310] printk: 11 messages suppressed.
[  100.522312] Buffer I/O error on device sda1, logical block 206833120
[  100.522314] attempt to access beyond end of device
[  100.522315] sda: rw=0, want=1654667016, limit=976773168
[  100.522316] Buffer I/O error on device sda1, logical block 206833120
[  100.522321] attempt to access beyond end of device
[  100.522322] sda: rw=0, want=1654667248, limit=976773168
[  100.522323] Buffer I/O error on device sda1, logical block 206833149
[  100.522324] attempt to access beyond end of device
[  100.522325] sda: rw=0, want=1654667248, limit=976773168
[  100.522347] attempt to access beyond end of device
[  100.522348] sda: rw=0, want=1654667256, limit=976773168
[  100.522350] attempt to access beyond end of device
[  100.522351] sda: rw=0, want=1654667256, limit=976773168
[  100.522354] attempt to access beyond end of device
[  100.522356] sda: rw=0, want=1654667256, limit=976773168
[  100.522359] attempt to access beyond end of device
[  100.522360] sda: rw=0, want=1654667256, limit=976773168
[  100.522362] attempt to access beyond end of device
[  100.522363] sda: rw=0, want=1654667256, limit=976773168
[  100.522366] attempt to access beyond end of device
[  100.522367] sda: rw=0, want=1654667256, limit=976773168
[  100.522370] attempt to access beyond end of device
[  100.522371] sda: rw=0, want=1654667256, limit=976773168
[  100.522375] attempt to access beyond end of device
[  100.522376] sda: rw=0, want=1654667200, limit=976773168
[  100.522379] attempt to access beyond end of device
[  100.522380] sda: rw=0, want=1654667248, limit=976773168
[  100.522383] attempt to access beyond end of device
[  100.522384] sda: rw=0, want=1654667256, limit=976773168
[  100.522387] attempt to access beyond end of device
[  100.522388] sda: rw=0, want=1654667256, limit=976773168
[  100.524669] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hard
ware
[  100.524675] iTCO_wdt: No card detected
[  101.276310] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ
 22
[  101.276323] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[  101.317487] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS.
..
[  101.349579] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 17 (level, low) -> IRQ
 18
[  101.349593] PCI: Setting latency timer of device 0000:01:00.1 to 64
[  101.395720] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 17 (level, low) -> IRQ
 18
[  101.395729] PCI: Setting latency timer of device 0000:02:00.1 to 64
[  102.480455] device-mapper: uevent: version 1.0.3
[  102.480472] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-d
[email]evel@redhat.com[/email]
[  104.099316] ip_tables: (C) 2000-2006 Netfilter Core Team
[  105.237582] No dock devices found.
[  111.802618] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  111.802620] apm: disabled - APM is not SMP safe.
[  112.619047] lp0: using parport0 (interrupt-driven).
[  113.067047] ppdev: user-space parallel port driver
[  113.721278] mtrr: type mismatch for d0000000,1000000 old: write-back new: wri
te-combining
[  121.665634] attempt to access beyond end of device
[  121.665640] sda: rw=0, want=1654667016, limit=976773168
[  121.665642] printk: 12 messages suppressed.
[  121.665644] Buffer I/O error on device sda1, logical block 206833120
[  121.665648] attempt to access beyond end of device
[  121.665649] sda: rw=0, want=1654667016, limit=976773168
[  121.665651] Buffer I/O error on device sda1, logical block 206833120
[  121.665658] attempt to access beyond end of device
[  121.665660] sda: rw=0, want=1654667248, limit=976773168
[  121.665662] Buffer I/O error on device sda1, logical block 206833149
[  121.665665] attempt to access beyond end of device
[  121.665667] sda: rw=0, want=1654667248, limit=976773168
[  121.665669] Buffer I/O error on device sda1, logical block 206833149
[  121.665706] attempt to access beyond end of device
[  121.665708] sda: rw=0, want=1654667256, limit=976773168
[  121.665711] attempt to access beyond end of device
[  121.665713] sda: rw=0, want=1654667256, limit=976773168
[  121.665718] attempt to access beyond end of device
[  121.665720] sda: rw=0, want=1654667256, limit=976773168
[  121.665725] attempt to access beyond end of device
[  121.665727] sda: rw=0, want=1654667256, limit=976773168
[  121.665732] attempt to access beyond end of device
[  121.665734] sda: rw=0, want=1654667256, limit=976773168
[  121.665739] attempt to access beyond end of device
[  121.665741] sda: rw=0, want=1654667256, limit=976773168
[  121.665746] attempt to access beyond end of device
[  121.665748] sda: rw=0, want=1654667256, limit=976773168
[  121.665754] attempt to access beyond end of device
[  121.665756] sda: rw=0, want=1654667200, limit=976773168
[  121.665761] attempt to access beyond end of device
[  121.665763] sda: rw=0, want=1654667248, limit=976773168
[  121.665768] attempt to access beyond end of device
[  121.665770] sda: rw=0, want=1654667256, limit=976773168
[  121.665775] attempt to access beyond end of device
[  121.665777] sda: rw=0, want=1654667256, limit=976773168
[  122.528522] r8169: eth0: link up
[  122.528529] r8169: eth0: link up
[  123.709171] Bluetooth: Core ver 2.11
[  123.709443] NET: Registered protocol family 31
[  123.709446] Bluetooth: HCI device and connection manager initialized
[  123.709448] Bluetooth: HCI socket layer initialized
[  124.106869] Bluetooth: L2CAP ver 2.9
[  124.106872] Bluetooth: L2CAP socket layer initialized
[  124.394483] Bluetooth: RFCOMM socket layer initialized
[  124.394491] Bluetooth: RFCOMM TTY layer initialized
[  124.394493] Bluetooth: RFCOMM ver 1.8
[  126.314996] NET: Registered protocol family 17
[  129.699772] NET: Registered protocol family 10
[  129.699942] lo: Disabled Privacy Extensions
[  140.011307] eth0: no IPv6 routers present
[  896.014832] device-mapper: table: 254:0: linear: dm-linear: Device lookup fai                                             led
[  896.014976] device-mapper: ioctl: error adding target to table
```
[This]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2736") is my motherboard if you can find some information about it I can't.

You think the 8.10 live cd should give improved results? I'm knee deep in this already, might as well try it if you think it will help.

---

### Post by psusi on 2008-11-25
> **Swooper86 said:**
> [   58.838419] ata1.00: HPA unlocked: 976771055 -> 976773168, native 976773168


Bingo.  Your bios has configured the disk to hide part of its space for some reason, so when the kernel opens it back up to the full space, the sector where the raid metadata is is no longer the last one on the disk.  You might ask the motherboard manufacturer why they are using an HPA and how you can disable it.  Otherwise you can either force the kernel to respect it, or use 8.10 which does so by default.

---

### Post by Swooper86 on 2008-11-25
I'm fine with using 8.10, I'd have upgraded to it anyway if I had gotten 8.04 to work - I was only using that because I had the live cd and didn't think it mattered. Anyway, I'm writing this from the 8.10 live cd, I have installed dmraid, and still it seems to not recognize the raid array. Something appears to have changed since 8.04, so I cannot check /dev/mapper/ to see if there's anything there - no /mapper/ subdirectory anymore for some reason and I don't know where to look instead.

Current sudo dmraid -tay -vvvv -dddd output:
```
ubuntu@ubuntu:~$ sudo dmraid -tay -vvvv -dddd
WARN: locking /var/lock/dmraid/.lock         
NOTICE: /dev/sdb: asr     discovering        
NOTICE: /dev/sdb: ddf1    discovering        
NOTICE: /dev/sdb: hpt37x  discovering        
NOTICE: /dev/sdb: hpt45x  discovering        
NOTICE: /dev/sdb: isw     discovering        
NOTICE: /dev/sdb: isw metadata discovered    
NOTICE: /dev/sdb: jmicron discovering        
NOTICE: /dev/sdb: lsi     discovering        
NOTICE: /dev/sdb: nvidia  discovering        
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
DEBUG: _find_set: searching isw_gajjjcjci
DEBUG: _find_set: not found isw_gajjjcjci
DEBUG: _find_set: searching isw_gajjjcjci_Volume0
DEBUG: _find_set: searching isw_gajjjcjci_Volume0
DEBUG: _find_set: not found isw_gajjjcjci_Volume0
DEBUG: _find_set: not found isw_gajjjcjci_Volume0
NOTICE: added /dev/sdb to RAID set "isw_gajjjcjci"
DEBUG: checking isw device "/dev/sdb"
ERROR: isw device for volume "Volume0" broken on /dev/sdb in RAID set "isw_gajjjcjci_Volume0"
ERROR: isw: wrong # of devices in RAID set "isw_gajjjcjci_Volume0" [1/2] on /dev/sdb
DEBUG: set status of set "isw_gajjjcjci_Volume0" to 2
DEBUG: set status of set "isw_gajjjcjci" to 4
isw_gajjjcjci_Volume0: 0 976766208 linear /dev/zero 0
INFO: Activating GROUP RAID set "isw_gajjjcjci"
WARN: unlocking /var/lock/dmraid/.lock
DEBUG: freeing devices of RAID set "isw_gajjjcjci_Volume0"
DEBUG: freeing device "isw_gajjjcjci_Volume0", path "/dev/sdb"
DEBUG: freeing devices of RAID set "isw_gajjjcjci"
DEBUG: freeing device "isw_gajjjcjci", path "/dev/sdb"
```

---

### Post by psusi on 2008-11-25
Hrm.... it's still not detecting the metadata on sda.  Check your dmesg again for the message about the HPA.  8.10 should say it detects the HPA but does not unlock it.

---

### Post by Swooper86 on 2008-11-26
Among a crapload of other things, dmesg gives...
```
[    3.436608] ata1.00: HPA unlocked: 976771055 -> 976773168, native 976773168  
```
...almost exactly the same line as it did with 8.04, I'm not sure of the significance of the first bracketed number though.

Also, the KDE4 versions of both Konsole and Yakuake terminals seem to cut off the top of such long outputs for some odd reason. :|

---

### Post by psusi on 2008-11-26
Are you SURE you are using an 8.10 livecd?  It should not be doing that.  The first number is the size of the disk ( in sectors ) that the bios told it to report, and the second is the real size, which the kernel is telling it to use.

Make sure you are using kernel 2.6.27.

You should be able to force it by adding break=modules to the kernel boot arguments, then when you get to the initramfs prompt, do:

```

echo options libata ignore_hpa=0 > /etc/modprobe.d/libata-options
exit

```

---

### Post by Swooper86 on 2008-11-26
I'm positive. The 8.04 does not come with KDE4, this one definitely does. How do I make sure I am using kernel 2.6.27? I think I need more accurate instructions on how exactly to force the kernel (remember, I'm a complete linux newbie, heh)... Where and how exactly do I add those break=modules? And what is this initramfs prompt?

Going to a sports practice now, will have all the time in the world to mess with this when I get back in a few hours.

---

### Post by psusi on 2008-11-26
The third line in your dmesg lists the kernel version.  On the livecd at the boot loader screen I think it says press F6 for more options, and lets you edit the kernel command line.  Change the words "splash" and "quiet" to nosplash and noquiet, and add break=modules at the end, with a space between it and the previous text.  That will make the system stop very early in the boot process and drop you to a command line.

---

### Post by Swooper86 on 2008-11-26
Freshly started (no updates or anything) 8.10 live cd says this:
```
ubuntu@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu   
[    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
...
```
Which is good. I will now attempt your method of forcing the kernel. Let's hope this works... :)

---

### Post by Swooper86 on 2008-11-26
Ok, ran those commands on startup, got lots of weird messages (something about trying to reach address beyond end of device, which may or may not be relevant - they went to fast to catch any of it and I obviously couldn't copy them or anything). Kubuntu started normally after this, I installed updates and raid driver. Just in case you wanted to see this now:
```
ubuntu@ubuntu:~$ dmraid -tay -vvvv -dddd
NOTICE: creating directory /var/lock/dmraid
ERROR: you must be root                    
ubuntu@ubuntu:~$ sudo dmraid -tay -vvvv -dddd   
WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: isw metadata discovered
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
DEBUG: _find_set: searching isw_gajjjcjci
DEBUG: _find_set: not found isw_gajjjcjci
ERROR: isw: unsupported map state 0x3 on /dev/sdb for Volume0
ERROR: adding /dev/sdb to RAID set "isw_gajjjcjci"
DEBUG: _find_set: searching isw_gajjjcjci
DEBUG: _find_set: found isw_gajjjcjci
ERROR: removing RAID set "isw_gajjjcjci"
DEBUG: freeing devices of RAID set "isw_gajjjcjci"
DEBUG: freeing device "isw_gajjjcjci", path "/dev/sdb"
No RAID sets
WARN: unlocking /var/lock/dmraid/.lock
```
Aaaaand the graphical installer STILL doesn't see my raid. What the crap? :(

---

### Post by inobe on 2008-11-26
tried it with my intel media series board with p35 chipset and intel matrix raid.

rebooted after setup, bios says no bootable disks.


i tried that on 8.10's release date, i searched the forum and many others encountered similar problems.

i wouldn't recommend the live cd setup.

---

### Post by Swooper86 on 2008-11-27
So... Given up on me, have you, psusi? :-?

---

### Post by psusi on 2008-11-27
I've been busy stuffing myself to the gills with turkey.  After you did what I said before, were you still seeing the HPA unlocked in your dmesg?

---

### Post by Swooper86 on 2008-11-28
I must have done something wrong when I ran through this kernel-forcing operation last time, because IT WORKS NOW! WOOO! The installer sees my raid :) I'm gonna finish setting up the dual boot and then report when I'm done.

---

### Post by Swooper86 on 2008-11-28
That didn't go too well :(

I took my eyes off the installation process for a moment and when I looked back there was just a small window that said the Ubiquity installer had unexpectedly crashed. I tried running it again, it still saw the raid but no free partition. I booted back into Vista and cleared up the partitions the installer had created (I don't know how to do that from Kubuntu).

I then once more booted up Kubuntu with the kernel force and installed again, this time watching the progress bar the whole time. It crashed at 94% - 'Configuring hardware'. What the hell? Now what? :confused:

First thought: If the graphical installer was the problem here, maybe this can somehow be done from the alternate install cd? I'd need directions with how to do this though, I think.

Edit:
Thought I'd add the dmesg output - or as much of it as Konsole will show me, it's so long it apparently cuts off the top. 21 page when copied into OpenOffice.org Writer. Relevant line bolded.
```
[    0.000000] ACPI: IRQ2 used by override.                                     
[    0.000000] ACPI: IRQ9 used by override.                                     
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs                    
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000                       
[    0.000000] Using ACPI (MADT) for SMP configuration information              
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs                             
[    0.000000] mapped APIC to ffffb000 (fee00000)                               
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)                             
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: cff00000:20100000)                                                                           
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data                   
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1                        
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 844096                                                                      
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.gz noquiet nosplash break=modules --                                                                          
[    0.000000] Enabling fast FPU save and restore... done.                      
[    0.000000] Enabling unmasked SIMD FPU exception support... done.            
[    0.000000] Initializing CPU#0                                               
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)            
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.                       
[    0.000000] TSC: using PIT calibration value                                 
[    0.000000] Detected 3166.276 MHz processor.                                 
[    0.004000] Console: colour VGA+ 80x25                                       
[    0.004000] console [tty0] enabled                                           
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes) 
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)   
[    0.004000] Memory: 3361260k/3406720k available (2572k kernel code, 44152k reserved, 1160k data, 424k init, 2489216k highmem)                                
[    0.004000] virtual kernel memory layout:                                    
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)                
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)                
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)                
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)                
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)                
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)                
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)                
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                                                                      
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated             
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1                                                                          
[    0.004000] hpet clockevent registered                                       
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 6332.55 BogoMIPS (lpj=12665104)                                       
[    0.004000] Security Framework initialized                                   
[    0.004000] SELinux:  Disabled at boot.                                      
[    0.004000] AppArmor: AppArmor initialized                                   
[    0.004000] Mount-cache hash table entries: 512                              
[    0.004000] Initializing cgroup subsys ns                                    
[    0.004000] Initializing cgroup subsys cpuacct                               
[    0.004000] Initializing cgroup subsys memory                                
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K                            
[    0.004000] CPU: L2 cache: 6144K                                             
[    0.004000] CPU: Physical Processor ID: 0                                    
[    0.004000] CPU: Processor Core ID: 0                                        
[    0.004000] using mwait in idle threads.                                     
[    0.004000] Checking 'hlt' instruction... OK.                                
[    0.017331] ACPI: Core revision 20080609                                     
[    0.018747] ACPI: Checking initramfs for custom DSDT                         
[    0.239633] ENABLING IO-APIC IRQs                                            
[    0.239826] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1             
[    0.279544] CPU0: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz stepping 06
[    0.280017] Booting processor 1/1 ip 6000                                    
[    0.004000] Initializing CPU#1                                               
[    0.004000] Calibrating delay using timer specific routine.. 6332.51 BogoMIPS (lpj=12665025)                                                                 
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K                            
[    0.004000] CPU: L2 cache: 6144K                                             
[    0.004000] CPU: Physical Processor ID: 0                                    
[    0.004000] CPU: Processor Core ID: 1                                        
[    0.364723] CPU1: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz stepping 06
[    0.364971] checking TSC synchronization [CPU#0 -> CPU#1]: passed.           
[    0.368036] Brought up 2 CPUs                                                
[    0.368065] Total of 2 processors activated (12665.06 BogoMIPS).             
[    0.368108] CPU0 attaching sched-domain:                                     
[    0.368110]  domain 0: span 0-1 level MC                                     
[    0.368112]   groups: 0 1                                                    
[    0.368115] CPU1 attaching sched-domain:                                     
[    0.368117]  domain 0: span 0-1 level MC                                     
[    0.368118]   groups: 1 0                                                    
[    0.368167] net_namespace: 840 bytes                                         
[    0.368167] Booting paravirtualized kernel on bare hardware                  
[    0.368243] Time: 22:33:21  Date: 11/28/08                                   
[    0.368287] NET: Registered protocol family 16                               
[    0.368326] EISA bus registered                                              
[    0.368326] ACPI: bus type pci registered                                    
[    0.368326] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63  
[    0.368326] PCI: MCFG area at f0000000 reserved in E820                      
[    0.368326] PCI: Using MMCONFIG for extended config space                    
[    0.368326] PCI: Using configuration type 1 for base access                  
[    0.368467] ACPI: EC: Look up EC in DSDT                                     
[    0.375529] ACPI: Interpreter enabled                                        
[    0.375563] ACPI: (supports S0 S3 S4 S5)                                     
[    0.375689] ACPI: Using IOAPIC for interrupt routing                         
[    0.376771] ACPI: PCI Root Bridge [PCI0] (0000:00)                           
[    0.376771] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold            
[    0.376771] pci 0000:00:01.0: PME# disabled                                  
[    0.376771] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold            
[    0.376771] pci 0000:00:06.0: PME# disabled                                  
[    0.376771] PCI: 0000:00:1a.0 reg 20 io port: [e100, e11f]                   
[    0.376771] PCI: 0000:00:1a.1 reg 20 io port: [e200, e21f]                   
[    0.376771] PCI: 0000:00:1a.2 reg 20 io port: [e000, e01f]                   
[    0.380060] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fa104000, fa1043ff]        
[    0.380116] PCI: 0000:00:1b.0 reg 10 64bit mmio: [fa100000, fa103fff]        
[    0.380144] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold            
[    0.380174] pci 0000:00:1b.0: PME# disabled                                  
[    0.380235] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold            
[    0.380265] pci 0000:00:1c.0: PME# disabled                                  
[    0.380329] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold            
[    0.380359] pci 0000:00:1c.3: PME# disabled                                  
[    0.380421] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold            
[    0.380451] pci 0000:00:1c.5: PME# disabled                                  
[    0.380511] PCI: 0000:00:1d.0 reg 20 io port: [e300, e31f]                   
[    0.380559] PCI: 0000:00:1d.1 reg 20 io port: [e400, e41f]                   
[    0.380606] PCI: 0000:00:1d.2 reg 20 io port: [e500, e51f]                   
[    0.380646] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fa105000, fa1053ff]        
[    0.380765] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO                                                                          
[    0.380798] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO   
[    0.380860] PCI: 0000:00:1f.2 reg 10 io port: [e600, e607]                   
[    0.380864] PCI: 0000:00:1f.2 reg 14 io port: [e700, e703]                   
[    0.380868] PCI: 0000:00:1f.2 reg 18 io port: [e800, e807]                   
[    0.380872] PCI: 0000:00:1f.2 reg 1c io port: [e900, e903]                   
[    0.380876] PCI: 0000:00:1f.2 reg 20 io port: [ea00, ea1f]                   
[    0.380880] PCI: 0000:00:1f.2 reg 24 32bit mmio: [fa106000, fa1067ff]        
[    0.380898] pci 0000:00:1f.2: PME# supported from D3hot                      
[    0.380927] pci 0000:00:1f.2: PME# disabled                                  
[    0.380967] PCI: 0000:00:1f.3 reg 10 64bit mmio: [fa107000, fa1070ff]        
[    0.380977] PCI: 0000:00:1f.3 reg 20 io port: [500, 51f]                     
[    0.381008] PCI: 0000:01:00.0 reg 10 32bit mmio: [d0000000, dfffffff]        
[    0.381017] PCI: 0000:01:00.0 reg 18 64bit mmio: [f7000000, f700ffff]        
[    0.381021] PCI: 0000:01:00.0 reg 20 io port: [a000, a0ff]                   
[    0.381028] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]                  
[    0.381039] pci 0000:01:00.0: supports D1                                    
[    0.381040] pci 0000:01:00.0: supports D2                                    
[    0.381058] PCI: 0000:01:00.1 reg 10 64bit mmio: [f7010000, f7013fff]        
[    0.381082] pci 0000:01:00.1: supports D1                                    
[    0.381083] pci 0000:01:00.1: supports D2                                    
[    0.381111] PCI: bridge 0000:00:01.0 io port: [a000, afff]                   
[    0.381113] PCI: bridge 0000:00:01.0 32bit mmio: [f6000000, f7ffffff]        
[    0.381116] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]   
[    0.381137] PCI: 0000:02:00.0 reg 10 32bit mmio: [e0000000, efffffff]        
[    0.381149] PCI: 0000:02:00.0 reg 18 64bit mmio: [f5000000, f500ffff]        
[    0.381153] PCI: 0000:02:00.0 reg 20 io port: [b000, b0ff]                   
[    0.381161] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]                  
[    0.381174] pci 0000:02:00.0: supports D1                                    
[    0.381175] pci 0000:02:00.0: supports D2                                    
[    0.381198] PCI: 0000:02:00.1 reg 10 64bit mmio: [f5010000, f5013fff]        
[    0.381227] pci 0000:02:00.1: supports D1                                    
[    0.381228] pci 0000:02:00.1: supports D2                                    
[    0.381257] PCI: bridge 0000:00:06.0 io port: [b000, bfff]                   
[    0.381259] PCI: bridge 0000:00:06.0 32bit mmio: [f4000000, f5ffffff]        
[    0.381262] PCI: bridge 0000:00:06.0 64bit mmio pref: [e0000000, efffffff]   
[    0.381290] PCI: bridge 0000:00:1c.0 io port: [9000, 9fff]                   
[    0.381373] PCI: 0000:04:00.0 reg 24 32bit mmio: [fa000000, fa001fff]        
[    0.381400] pci 0000:04:00.0: PME# supported from D3hot                      
[    0.381431] pci 0000:04:00.0: PME# disabled                                  
[    0.381491] PCI: 0000:04:00.1 reg 10 io port: [c000, c007]                   
[    0.381498] PCI: 0000:04:00.1 reg 14 io port: [c100, c103]                   
[    0.381506] PCI: 0000:04:00.1 reg 18 io port: [c200, c207]                   
[    0.381513] PCI: 0000:04:00.1 reg 1c io port: [c300, c303]                   
[    0.381520] PCI: 0000:04:00.1 reg 20 io port: [c400, c40f]                   
[    0.381583] PCI: bridge 0000:00:1c.3 io port: [c000, cfff]                   
[    0.381586] PCI: bridge 0000:00:1c.3 32bit mmio: [fa000000, fa0fffff]        
[    0.381637] PCI: 0000:05:00.0 reg 10 io port: [d000, d0ff]                   
[    0.381656] PCI: 0000:05:00.0 reg 18 64bit mmio: [f9000000, f9000fff]        
[    0.381675] PCI: 0000:05:00.0 reg 30 32bit mmio: [0, ffff]                   
[    0.381693] pci 0000:05:00.0: supports D1                                    
[    0.381694] pci 0000:05:00.0: supports D2                                    
[    0.381695] pci 0000:05:00.0: PME# supported from D1 D2 D3hot D3cold         
[    0.381727] pci 0000:05:00.0: PME# disabled                                  
[    0.381778] PCI: bridge 0000:00:1c.5 io port: [d000, dfff]                   
[    0.381780] PCI: bridge 0000:00:1c.5 32bit mmio: [f8000000, f9ffffff]        
[    0.381821] pci 0000:00:1e.0: transparent bridge                             
[    0.381850] PCI: bridge 0000:00:1e.0 io port: [8000, 8fff]                   
[    0.381871] bus 00 -> node 0                                                 
[    0.381875] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]              
[    0.382076] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]         
[    0.382148] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]         
[    0.382222] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]         
[    0.382292] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]         
[    0.392632] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)                                                                               
[    0.392632] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)                                                                               
[    0.392902] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)                                                                               
[    0.393301] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 *15)                                                                               
[    0.396151] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.                                                                  
[    0.397501] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)                                                                               
[    0.397901] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 *14 15)                                                                               
[    0.398300] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)                                                                               
[    0.398660] Linux Plug and Play Support v0.97 (c) Adam Belay                 
[    0.398660] pnp: PnP ACPI init                                               
[    0.398660] ACPI: bus type pnp registered                                    
[    0.400318] pnp: PnP ACPI: found 14 devices                                  
[    0.400318] ACPI: ACPI bus type pnp unregistered                             
[    0.400318] PnPBIOS: Disabled by ACPI PNP                                    
[    0.400318] PCI: Using ACPI for IRQ routing                                  
[    0.408033] NET: Registered protocol family 8                                
[    0.408065] NET: Registered protocol family 20                               
[    0.408108] NetLabel: Initializing                                           
[    0.408108] NetLabel:  domain hash size = 128                                
[    0.408108] NetLabel:  protocols = UNLABELED CIPSOv4                         
[    0.408138] NetLabel:  unlabeled traffic allowed by default                  
[    0.408169] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0                       
[    0.408312] hpet0: 4 64-bit timers, 14318180 Hz                              
[    0.409892] tracer: 772 pages allocated for 65536 entries of 48 bytes        
[    0.409921]    actual entries 65620                                          
[    0.409999] AppArmor: AppArmor Filesystem Enabled                            
[    0.410040] ACPI: RTC can wake from S4                                       
[    0.416042] system 00:01: ioport range 0x4d0-0x4d1 has been reserved         
[    0.416075] system 00:01: ioport range 0x290-0x29f has been reserved         
[    0.416108] system 00:01: ioport range 0x800-0x87f has been reserved         
[    0.416144] system 00:01: ioport range 0x290-0x294 has been reserved         
[    0.416173] system 00:01: ioport range 0x880-0x88f has been reserved         
[    0.416207] system 00:0a: ioport range 0x400-0x4bf could not be reserved     
[    0.416238] system 00:0b: iomem range 0xf0000000-0xf3ffffff could not be reserved                                                                            
[    0.416272] system 00:0c: iomem range 0xd2200-0xd3fff has been reserved      
[    0.416301] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved  
[    0.416331] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved  
[    0.416360] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved  
[    0.416389] system 00:0c: iomem range 0xcfee0000-0xcfefffff could not be reserved                                                                            
[    0.416421] system 00:0c: iomem range 0x0-0x9ffff could not be reserved      
[    0.416450] system 00:0c: iomem range 0x100000-0xcfedffff could not be reserved                                                                              
[    0.416483] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved                                                                            
[    0.416515] system 00:0c: iomem range 0xfed10000-0xfed1dfff could not be reserved                                                                            
[    0.416547] system 00:0c: iomem range 0xfed20000-0xfed8ffff could not be reserved                                                                            
[    0.416580] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved                                                                            
[    0.416612] system 00:0c: iomem range 0xffb00000-0xffb7ffff could not be reserved                                                                            
[    0.416644] system 00:0c: iomem range 0xfff00000-0xffffffff could not be reserved                                                                            
[    0.416676] system 00:0c: iomem range 0xe0000-0xeffff has been reserved      
[    0.451527] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01              
[    0.451557] pci 0000:00:01.0:   IO window: 0xa000-0xafff                     
[    0.451586] pci 0000:00:01.0:   MEM window: 0xf6000000-0xf7ffffff            
[    0.451615] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff                                                                           
[    0.451649] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02              
[    0.451678] pci 0000:00:06.0:   IO window: 0xb000-0xbfff                     
[    0.451707] pci 0000:00:06.0:   MEM window: 0xf4000000-0xf5ffffff            
[    0.451736] pci 0000:00:06.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff                                                                           
[    0.451770] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03              
[    0.451799] pci 0000:00:1c.0:   IO window: 0x9000-0x9fff                     
[    0.451829] pci 0000:00:1c.0:   MEM window: disabled                         
[    0.451858] pci 0000:00:1c.0:   PREFETCH window: disabled                    
[    0.451889] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04              
[    0.451918] pci 0000:00:1c.3:   IO window: 0xc000-0xcfff                     
[    0.451948] pci 0000:00:1c.3:   MEM window: 0xfa000000-0xfa0fffff            
[    0.451978] pci 0000:00:1c.3:   PREFETCH window: disabled                    
[    0.452009] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:05              
[    0.452044] pci 0000:00:1c.5:   IO window: 0xd000-0xdfff                     
[    0.452074] pci 0000:00:1c.5:   MEM window: 0xf8000000-0xf9ffffff            
[    0.452104] pci 0000:00:1c.5:   PREFETCH window: 0x000000fa200000-0x000000fa2fffff                                                                           
[    0.452139] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06              
[    0.452168] pci 0000:00:1e.0:   IO window: 0x8000-0x8fff                     
[    0.452198] pci 0000:00:1e.0:   MEM window: disabled                         
[    0.452227] pci 0000:00:1e.0:   PREFETCH window: disabled                    
[    0.452262] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16     
[    0.452292] pci 0000:00:01.0: setting latency timer to 64                    
[    0.452295] pci 0000:00:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16     
[    0.452325] pci 0000:00:06.0: setting latency timer to 64                    
[    0.452330] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16     
[    0.452360] pci 0000:00:1c.0: setting latency timer to 64                    
[    0.452365] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19     
[    0.452395] pci 0000:00:1c.3: setting latency timer to 64                    
[    0.452400] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17     
[    0.452431] pci 0000:00:1c.5: setting latency timer to 64                    
[    0.452435] pci 0000:00:1e.0: setting latency timer to 64                    
[    0.452437] bus: 00 index 0 io port: [0, ffff]                               
[    0.452465] bus: 00 index 1 mmio: [0, ffffffff]                              
[    0.452493] bus: 01 index 0 io port: [a000, afff]                            
[    0.452521] bus: 01 index 1 mmio: [f6000000, f7ffffff]                       
[    0.452549] bus: 01 index 2 mmio: [d0000000, dfffffff]                       
[    0.452577] bus: 01 index 3 mmio: [0, 0]                                     
[    0.452604] bus: 02 index 0 io port: [b000, bfff]                            
[    0.452632] bus: 02 index 1 mmio: [f4000000, f5ffffff]                       
[    0.452660] bus: 02 index 2 mmio: [e0000000, efffffff]                       
[    0.452688] bus: 02 index 3 mmio: [0, 0]                                     
[    0.452716] bus: 03 index 0 io port: [9000, 9fff]                            
[    0.452743] bus: 03 index 1 mmio: [0, 0]                                     
[    0.452771] bus: 03 index 2 mmio: [0, 0]                                     
[    0.452798] bus: 03 index 3 mmio: [0, 0]                                     
[    0.452826] bus: 04 index 0 io port: [c000, cfff]                            
[    0.452853] bus: 04 index 1 mmio: [fa000000, fa0fffff]                       
[    0.452881] bus: 04 index 2 mmio: [0, 0]                                     
[    0.452909] bus: 04 index 3 mmio: [0, 0]                                     
[    0.452936] bus: 05 index 0 io port: [d000, dfff]                            
[    0.452964] bus: 05 index 1 mmio: [f8000000, f9ffffff]                       
[    0.452992] bus: 05 index 2 mmio: [fa200000, fa2fffff]                       
[    0.453020] bus: 05 index 3 mmio: [0, 0]                                     
[    0.453048] bus: 06 index 0 io port: [8000, 8fff]                            
[    0.453075] bus: 06 index 1 mmio: [0, 0]                                     
[    0.453103] bus: 06 index 2 mmio: [0, 0]                                     
[    0.453130] bus: 06 index 3 io port: [0, ffff]                               
[    0.453158] bus: 06 index 4 mmio: [0, ffffffff]                              
[    0.453190] NET: Registered protocol family 2                                
[    0.468072] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.468247] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)                                                                             
[    0.468467] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)      
[    0.468587] TCP: Hash tables configured (established 131072 bind 65536)      
[    0.468616] TCP reno registered                                              
[    0.472085] NET: Registered protocol family 1                                
[    0.472189] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1                                                                    
[    0.504028] Switched to high resolution mode on CPU 0                        
[    0.686647]  it is                                                           
[    0.917612] Freeing initrd memory: 8258k freed                               
[    0.918367] audit: initializing netlink socket (disabled)                    
[    0.918409] type=2000 audit(1227911600.916:1): initialized                   
[    0.922270] highmem bounce pool size: 64 pages                               
[    0.922300] HugeTLB registered 4 MB page size, pre-allocated 0 pages         
[    0.923733] VFS: Disk quotas dquot_6.5.1                                     
[    0.923811] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)       
[    0.923904] msgmni has been set to 1721                                      
[    0.924006] io scheduler noop registered                                     
[    0.924034] io scheduler anticipatory registered                             
[    0.924062] io scheduler deadline registered                                 
[    0.924095] io scheduler cfq registered (default)                            
[    0.924229] pci 0000:01:00.0: Boot video device                              
[    0.924306] pcieport-driver 0000:00:01.0: setting latency timer to 64        
[    0.924327] pcieport-driver 0000:00:01.0: found MSI capability               
[    0.924373] pci_express 0000:00:01.0:pcie00: allocate port service           
[    0.924401] pci_express 0000:00:01.0:pcie03: allocate port service           
[    0.924452] pcieport-driver 0000:00:06.0: setting latency timer to 64        
[    0.924472] pcieport-driver 0000:00:06.0: found MSI capability               
[    0.924518] pci_express 0000:00:06.0:pcie00: allocate port service           
[    0.924544] pci_express 0000:00:06.0:pcie03: allocate port service           
[    0.924595] pcieport-driver 0000:00:1c.0: setting latency timer to 64        
[    0.924620] pcieport-driver 0000:00:1c.0: found MSI capability               
[    0.924670] pci_express 0000:00:1c.0:pcie00: allocate port service           
[    0.924696] pci_express 0000:00:1c.0:pcie02: allocate port service           
[    0.924721] pci_express 0000:00:1c.0:pcie03: allocate port service           
[    0.924780] pcieport-driver 0000:00:1c.3: setting latency timer to 64        
[    0.924804] pcieport-driver 0000:00:1c.3: found MSI capability               
[    0.924855] pci_express 0000:00:1c.3:pcie00: allocate port service           
[    0.924881] pci_express 0000:00:1c.3:pcie02: allocate port service           
[    0.924905] pci_express 0000:00:1c.3:pcie03: allocate port service           
[    0.924964] pcieport-driver 0000:00:1c.5: setting latency timer to 64        
[    0.924988] pcieport-driver 0000:00:1c.5: found MSI capability               
[    0.925039] pci_express 0000:00:1c.5:pcie00: allocate port service           
[    0.925064] pci_express 0000:00:1c.5:pcie02: allocate port service           
[    0.925089] pci_express 0000:00:1c.5:pcie03: allocate port service           
[    0.925295] isapnp: Scanning for PnP cards...                                
[    1.278062] isapnp: No Plug & Play device found                              
[    1.298089] hpet_resources: 0xfed00000 is busy                               
[    1.298139] Serial: 8250/16550 driver4 ports, IRQ sharing enabled            
[    1.298260] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A             
[    1.298698] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                  
[    1.299757] brd: module loaded                                               
[    1.299822] input: Macintosh mouse button emulation as /devices/virtual/input/input0                                                                         
[    1.299922] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1           
[    1.299951] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp                                                   
[    1.302986] serio: i8042 KBD port at 0x60,0x64 irq 1                         
[    1.304609] mice: PS/2 mouse device common for all mice                      
[    1.304730] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0            
[    1.304777] rtc0: alarms up to one month, hpet irqs                          
[    1.304892] EISA: Probing bus 0 at eisa.0                                    
[    1.304938] Cannot allocate resource for EISA slot 8                         
[    1.304966] EISA: Detected 0 cards.                                          
[    1.304994] cpuidle: using governor ladder                                   
[    1.305022] cpuidle: using governor menu                                     
[    1.305364] TCP cubic registered                                             
[    1.305409] Using IPI No-Shortcut mode                                       
[    1.305544] registered taskstats version 1                                   
[    1.305657]   Magic number: 0:500:604                                        
[    1.305716] tty ptyd8: hash matches                                          
[    1.305748] tty ptyab: hash matches                                          
[    1.305827] rtc_cmos 00:04: setting system clock to 2008-11-28 22:33:22 UTC (1227911602)                                                                     
[    1.305860] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found             
[    1.305888] EDD information not available.                                   
[    1.306012] Freeing unused kernel memory: 424k freed                         
[    1.306062] Write protecting the kernel text: 2576k                          
[    1.306104] Write protecting the kernel read-only data: 936k                 
[    1.335960] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1                                                               
[  114.982735] fuse init (API version 7.9)                                      
[  114.996512] processor ACPI0007:00: registered as cooling_device0             
[  114.996542] ACPI: Processor [CPU0] (supports 8 throttling states)            
[  114.996726] ACPI: SSDT CFEE83C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)                                                                            
[  114.996956] processor ACPI0007:01: registered as cooling_device1             
[  114.996986] ACPI: Processor [CPU1] (supports 8 throttling states)            
[  115.102015] usbcore: registered new interface driver usbfs                   
[  115.102058] usbcore: registered new interface driver hub                     
[  115.102106] usbcore: registered new device driver usb                        
[  115.108152] USB Universal Host Controller Interface driver v3.0              
[  115.108209] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  115.108243] uhci_hcd 0000:00:1a.0: setting latency timer to 64               
[  115.108246] uhci_hcd 0000:00:1a.0: UHCI Host Controller                      
[  115.108296] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1                                                                             
[  115.108350] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e100                
[  115.108454] usb usb1: configuration #1 chosen from 1 choice                  
[  115.108505] hub 1-0:1.0: USB hub found                                       
[  115.108535] hub 1-0:1.0: 2 ports detected                                    
[  115.175513] No dock devices found.                                           
[  115.184308] SCSI subsystem initialized                                       
[  115.194296] libata version 3.00 loaded.                                      
[  115.316723] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[  115.316760] uhci_hcd 0000:00:1a.1: setting latency timer to 64               
[  115.316763] uhci_hcd 0000:00:1a.1: UHCI Host Controller                      
[  115.316805] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2                                                                             
[  115.316860] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e200                
[  115.316942] usb usb2: configuration #1 chosen from 1 choice                  
[  115.316986] hub 2-0:1.0: USB hub found                                       
[  115.317016] hub 2-0:1.0: 2 ports detected                                    
[  115.420164] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[  115.420199] uhci_hcd 0000:00:1a.2: setting latency timer to 64               
[  115.420202] uhci_hcd 0000:00:1a.2: UHCI Host Controller                      
[  115.420247] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3                                                                             
[  115.420301] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e000                
[  115.420381] usb usb3: configuration #1 chosen from 1 choice                  
[  115.420427] hub 3-0:1.0: USB hub found                                       
[  115.420458] hub 3-0:1.0: 2 ports detected                                    
[  115.428511] usb 1-2: new low speed USB device using uhci_hcd and address 2   
[  115.524170] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[  115.524206] ehci_hcd 0000:00:1a.7: setting latency timer to 64               
[  115.524209] ehci_hcd 0000:00:1a.7: EHCI Host Controller                      
[  115.524251] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4                                                                             
[  115.528191] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported    
[  115.528194] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfa104000                 
[  115.556009] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004                                                                            
[  115.556119] usb usb4: configuration #1 chosen from 1 choice                  
[  115.556162] hub 4-0:1.0: USB hub found                                       
[  115.556192] hub 4-0:1.0: 6 ports detected                                    
[  115.764136] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[  115.764168] uhci_hcd 0000:00:1d.0: setting latency timer to 64               
[  115.764170] uhci_hcd 0000:00:1d.0: UHCI Host Controller                      
[  115.764210] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5                                                                             
[  115.764262] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e300                
[  115.764338] usb usb5: configuration #1 chosen from 1 choice                  
[  115.764381] hub 5-0:1.0: USB hub found                                       
[  115.764410] hub 5-0:1.0: 2 ports detected                                    
[  115.868132] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  115.868164] uhci_hcd 0000:00:1d.1: setting latency timer to 64               
[  115.868166] uhci_hcd 0000:00:1d.1: UHCI Host Controller                      
[  115.868207] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6                                                                             
[  115.868260] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400                
[  115.868336] usb usb6: configuration #1 chosen from 1 choice                  
[  115.868380] hub 6-0:1.0: USB hub found                                       
[  115.868410] hub 6-0:1.0: 2 ports detected                                    
[  115.952007] usb 1-2: device not accepting address 2, error -71               
[  115.972132] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[  115.972164] uhci_hcd 0000:00:1d.2: setting latency timer to 64               
[  115.972166] uhci_hcd 0000:00:1d.2: UHCI Host Controller                      
[  115.972206] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7                                                                             
[  115.972255] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e500                
[  115.972333] usb usb7: configuration #1 chosen from 1 choice                  
[  115.972375] hub 7-0:1.0: USB hub found                                       
[  115.972405] hub 7-0:1.0: 2 ports detected                                    
[  116.008030] hub 1-0:1.0: unable to enumerate USB device on port 2            
[  116.076917] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[  116.076950] ehci_hcd 0000:00:1d.7: setting latency timer to 64               
[  116.076952] ehci_hcd 0000:00:1d.7: EHCI Host Controller                      
[  116.076995] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8                                                                             
[  116.080910] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported    
[  116.080913] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfa105000                 
[  116.096009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004                                                                            
[  116.096116] usb usb8: configuration #1 chosen from 1 choice                  
[  116.096159] hub 8-0:1.0: USB hub found                                       
[  116.096189] hub 8-0:1.0: 6 ports detected                                    
[  116.201266] ahci 0000:00:1f.2: version 3.0                                   
[  116.201274] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19    
[  116.201377] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode                                                                    
[  116.201411] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems                                                                   
[  116.201445] ahci 0000:00:1f.2: setting latency timer to 64                   
[  116.201775] scsi0 : ahci                                                     
[  116.201860] scsi1 : ahci                                                     
[  116.201924] scsi2 : ahci                                                     
[  116.201986] scsi3 : ahci                                                     
[  116.202047] scsi4 : ahci                                                     
[  116.202112] scsi5 : ahci                                                     
[  116.202213] ata1: SATA max UDMA/133 abar m2048@0xfa106000 port 0xfa106100 irq 218                                                                            
[  116.202247] ata2: SATA max UDMA/133 abar m2048@0xfa106000 port 0xfa106180 irq 218                                                                            
[  116.202279] ata3: SATA max UDMA/133 abar m2048@0xfa106000 port 0xfa106200 irq 218                                                                            
[  116.202312] ata4: SATA max UDMA/133 abar m2048@0xfa106000 port 0xfa106280 irq 218                                                                            
[  116.202344] ata5: SATA max UDMA/133 abar m2048@0xfa106000 port 0xfa106300 irq 218                                                                            
[  116.202377] ata6: SATA max UDMA/133 abar m2048@0xfa106000 port 0xfa106380 irq 218                                                                            
[  116.456008] usb 1-2: new low speed USB device using uhci_hcd and address 4   
[  116.632494] usb 1-2: configuration #1 chosen from 1 choice                   
[  116.643809] usbcore: registered new interface driver hiddev                  
[  116.659606] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2:1.0/input/input2                                         
[  116.659791] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.0-2                                                       
[  116.659921] usbcore: registered new interface driver usbhid                  
[  116.659950] usbhid: v2.6:USB HID core driver                                 
[  116.684012] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)           
**[  116.690350] ata1.00: HPA detected: current 976771055, native 976773168       **
[  116.690385] ata1.00: ATA-7: SAMSUNG HD502IJ, 1AA01112, max UDMA7             
[  116.690421] ata1.00: 976771055 sectors, multi 0: LBA48 NCQ (depth 31/32)     
[  116.696810] ata1.00: configured for UDMA/133                                 
[  117.196013] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)           
[  117.202350] ata2.00: ATA-7: SAMSUNG HD502IJ, 1AA01112, max UDMA7             
[  117.202383] ata2.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)     
[  117.208779] ata2.00: configured for UDMA/133                                 
[  117.544014] ata3: SATA link down (SStatus 0 SControl 300)                    
[  118.044013] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)           
[  118.045689] ata4.00: ATAPI: TSSTcorp CDDVDW SH-S203D, SB00, max UDMA/100, ATAPI AN                                                                           
[  118.046722] ata4.00: configured for UDMA/100                                 
[  118.380012] ata5: SATA link down (SStatus 0 SControl 300)                    
[  118.716012] ata6: SATA link down (SStatus 0 SControl 300)                    
[  118.732098] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD502IJ  1AA0 PQ: 0 ANSI: 5                                                                     
[  118.732539] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD502IJ  1AA0 PQ: 0 ANSI: 5                                                                     
[  118.733135] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203D  SB00 PQ: 0 ANSI: 5                                                                     
[  118.733977] ahci 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19    
[  118.748033] ahci 0000:04:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode                                                                     
[  118.748071] ahci 0000:04:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[  118.748107] ahci 0000:04:00.0: setting latency timer to 64                   
[  118.748189] scsi6 : ahci                                                     
[  118.748410] scsi7 : ahci                                                     
[  118.748486] ata7: SATA max UDMA/133 abar m8192@0xfa000000 port 0xfa000100 irq 19                                                                             
[  118.748519] ata8: SATA max UDMA/133 abar m8192@0xfa000000 port 0xfa000180 irq 19                                                                             
[  119.068023] ata7: SATA link down (SStatus 0 SControl 300)                    
[  119.404023] ata8: SATA link down (SStatus 0 SControl 300)                    
[  119.420034] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded                  
[  119.420076] r8169 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17   
[  119.420123] r8169 0000:05:00.0: setting latency timer to 64                  
[  119.420358] eth0: RTL8168b/8111b at 0xf883a000, 00:1d:7d:00:80:9d, XID 38000000 IRQ 217                                                                      
[  119.426122] pata_acpi 0000:04:00.1: enabling device (0000 -> 0001)           
[  119.426154] pata_acpi 0000:04:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16                                                                               
[  119.426206] pata_acpi 0000:04:00.1: setting latency timer to 64              
[  119.426216] pata_acpi 0000:04:00.1: PCI INT B disabled                       
[  119.428475] scsi 0:0:0:0: Attached scsi generic sg0 type 0                   
[  119.428525] scsi 1:0:0:0: Attached scsi generic sg1 type 0                   
[  119.428573] scsi 3:0:0:0: Attached scsi generic sg2 type 5                   
[  119.431188] pata_jmicron 0000:04:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16                                                                            
[  119.431241] pata_jmicron 0000:04:00.1: setting latency timer to 64           
[  119.431793] scsi8 : pata_jmicron                                             
[  119.432217] scsi9 : pata_jmicron                                             
[  119.432698] ata9: PATA max UDMA/100 cmd 0xc000 ctl 0xc100 bmdma 0xc400 irq 16
[  119.432728] ata10: PATA max UDMA/100 cmd 0xc200 ctl 0xc300 bmdma 0xc408 irq 16                                                                               
[  119.442212] Driver 'sd' needs updating - please use bus_type methods         
[  119.443230] sd 0:0:0:0: [sda] 976771055 512-byte hardware sectors (500107 MB)
[  119.443269] sd 0:0:0:0: [sda] Write Protect is off                           
[  119.443297] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                        
[  119.443315] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                          
[  119.443389] sd 0:0:0:0: [sda] 976771055 512-byte hardware sectors (500107 MB)
[  119.443427] sd 0:0:0:0: [sda] Write Protect is off                           
[  119.443455] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                        
[  119.443474] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                          
[  119.443508]  sda:<4>Driver 'sr' needs updating - please use bus_type methods 
[  119.452267]  sda1                                                            
[  119.452322] sda: p1 exceeds device capacity                                  
[  119.452409] sd 0:0:0:0: [sda] Attached SCSI disk                             
[  119.452481] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[  119.452520] sd 1:0:0:0: [sdb] Write Protect is off                           
[  119.452549] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00                        
[  119.452568] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                          
[  119.452635] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[  119.452674] sd 1:0:0:0: [sdb] Write Protect is off                           
[  119.452702] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00                        
[  119.452722] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                          
[  119.452756]  sdb: unknown partition table                                    
[  119.468500] sd 1:0:0:0: [sdb] Attached SCSI disk                             
[  119.471780] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray                                                                            
[  119.471817] Uniform CD-ROM driver Revision: 3.20                             
[  119.471902] sr 3:0:0:0: Attached scsi CD-ROM sr0                             
[  119.828132] attempt to access beyond end of device                           
[  119.828162] sda: rw=0, want=1654667016, limit=976771055                      
[  119.828190] Buffer I/O error on device sda1, logical block 206833120         
[  119.828219] attempt to access beyond end of device                           
[  119.828247] sda: rw=0, want=1654667016, limit=976771055                      
[  119.828276] Buffer I/O error on device sda1, logical block 206833120         
[  119.828309] attempt to access beyond end of device                           
[  119.828337] sda: rw=0, want=1654667248, limit=976771055                      
[  119.828365] Buffer I/O error on device sda1, logical block 206833149         
[  119.828394] attempt to access beyond end of device                           
[  119.828422] sda: rw=0, want=1654667248, limit=976771055                      
[  119.828450] Buffer I/O error on device sda1, logical block 206833149         
[  119.828507] attempt to access beyond end of device                           
[  119.828535] sda: rw=0, want=1654667256, limit=976771055                      
[  119.828564] Buffer I/O error on device sda1, logical block 206833150         
[  119.828595] attempt to access beyond end of device                           
[  119.828623] sda: rw=0, want=1654667256, limit=976771055                      
[  119.828651] Buffer I/O error on device sda1, logical block 206833150         
[  119.828690] attempt to access beyond end of device                           
[  119.828719] sda: rw=0, want=1654667256, limit=976771055                      
[  119.828747] Buffer I/O error on device sda1, logical block 206833150         
[  119.828778] attempt to access beyond end of device                           
[  119.828806] sda: rw=0, want=1654667256, limit=976771055                      
[  119.828834] Buffer I/O error on device sda1, logical block 206833150         
[  119.828866] attempt to access beyond end of device                           
[  119.828894] sda: rw=0, want=1654667256, limit=976771055                      
[  119.828922] Buffer I/O error on device sda1, logical block 206833150         
[  119.828953] attempt to access beyond end of device                           
[  119.828982] sda: rw=0, want=1654667256, limit=976771055                      
[  119.829010] Buffer I/O error on device sda1, logical block 206833150         
[  119.829041] attempt to access beyond end of device                           
[  119.829069] sda: rw=0, want=1654667256, limit=976771055                      
[  119.829101] attempt to access beyond end of device                           
[  119.829129] sda: rw=0, want=1654667200, limit=976771055                      
[  119.829160] attempt to access beyond end of device                           
[  119.829188] sda: rw=0, want=1654667248, limit=976771055                      
[  119.829219] attempt to access beyond end of device                           
[  119.829247] sda: rw=0, want=1654667256, limit=976771055                      
[  119.829278] attempt to access beyond end of device                           
[  119.829306] sda: rw=0, want=1654667256, limit=976771055                      
[  120.088405] attempt to access beyond end of device                           
[  120.088441] sda: rw=0, want=1654667016, limit=976771055                      
[  120.088474] attempt to access beyond end of device                           
[  120.088510] sda: rw=0, want=1654667016, limit=976771055                      
[  120.088543] attempt to access beyond end of device                           
[  120.088571] sda: rw=0, want=1654667248, limit=976771055                      
[  120.088600] attempt to access beyond end of device                           
[  120.088627] sda: rw=0, want=1654667248, limit=976771055                      
[  120.088676] attempt to access beyond end of device                           
[  120.088705] sda: rw=0, want=1654667256, limit=976771055                      
[  120.088734] attempt to access beyond end of device                           
[  120.088773] sda: rw=0, want=1654667256, limit=976771055                      
[  120.088805] attempt to access beyond end of device                           
[  120.088834] sda: rw=0, want=1654667256, limit=976771055                      
[  120.088867] attempt to access beyond end of device                           
[  120.088895] sda: rw=0, want=1654667256, limit=976771055                      
[  120.088925] attempt to access beyond end of device                           
[  120.088953] sda: rw=0, want=1654667256, limit=976771055                      
[  120.088984] attempt to access beyond end of device                           
[  120.089012] sda: rw=0, want=1654667256, limit=976771055                      
[  120.089042] attempt to access beyond end of device                           
[  120.089070] sda: rw=0, want=1654667256, limit=976771055                      
[  120.089102] attempt to access beyond end of device                           
[  120.089130] sda: rw=0, want=1654667200, limit=976771055                      
[  120.089161] attempt to access beyond end of device                           
[  120.089189] sda: rw=0, want=1654667248, limit=976771055                      
[  120.089220] attempt to access beyond end of device                           
[  120.089248] sda: rw=0, want=1654667256, limit=976771055                      
[  120.089279] attempt to access beyond end of device                           
[  120.089307] sda: rw=0, want=1654667256, limit=976771055                      
[  121.114892] attempt to access beyond end of device                           
[  121.114926] sda: rw=0, want=1654667016, limit=976771055                      
[  121.114958] attempt to access beyond end of device                           
[  121.114990] sda: rw=0, want=1654667016, limit=976771055                      
[  121.115029] attempt to access beyond end of device                           
[  121.115057] sda: rw=0, want=1654667248, limit=976771055                      
[  121.115085] attempt to access beyond end of device                           
[  121.115113] sda: rw=0, want=1654667248, limit=976771055                      
[  121.115162] attempt to access beyond end of device                           
[  121.115191] sda: rw=0, want=1654667256, limit=976771055                      
[  121.115220] attempt to access beyond end of device                           
[  121.115250] sda: rw=0, want=1654667256, limit=976771055                      
[  121.115281] attempt to access beyond end of device                           
[  121.115316] sda: rw=0, want=1654667256, limit=976771055                      
[  121.115348] attempt to access beyond end of device                           
[  121.115376] sda: rw=0, want=1654667256, limit=976771055                      
[  121.115406] attempt to access beyond end of device                           
[  121.115434] sda: rw=0, want=1654667256, limit=976771055                      
[  121.115465] attempt to access beyond end of device                           
[  121.115493] sda: rw=0, want=1654667256, limit=976771055                      
[  121.115524] attempt to access beyond end of device                           
[  121.115552] sda: rw=0, want=1654667256, limit=976771055                      
[  121.115584] attempt to access beyond end of device                           
[  121.115612] sda: rw=0, want=1654667200, limit=976771055                      
[  121.115642] attempt to access beyond end of device                           
[  121.115671] sda: rw=0, want=1654667248, limit=976771055                      
[  121.115701] attempt to access beyond end of device                           
[  121.115729] sda: rw=0, want=1654667256, limit=976771055                      
[  121.115760] attempt to access beyond end of device                           
[  121.115788] sda: rw=0, want=1654667256, limit=976771055                      
[  122.141179] attempt to access beyond end of device                           
[  122.141213] sda: rw=0, want=1654667016, limit=976771055                      
[  122.141246] attempt to access beyond end of device                           
[  122.141282] sda: rw=0, want=1654667016, limit=976771055                      
[  122.141314] attempt to access beyond end of device                           
[  122.141342] sda: rw=0, want=1654667248, limit=976771055                      
[  122.141371] attempt to access beyond end of device                           
[  122.141399] sda: rw=0, want=1654667248, limit=976771055                      
[  122.141448] attempt to access beyond end of device                           
[  122.141477] sda: rw=0, want=1654667256, limit=976771055                      
[  122.141506] attempt to access beyond end of device                           
[  122.141536] sda: rw=0, want=1654667256, limit=976771055                      
[  122.141567] attempt to access beyond end of device                           
[  122.141602] sda: rw=0, want=1654667256, limit=976771055                      
[  122.141633] attempt to access beyond end of device                           
[  122.141662] sda: rw=0, want=1654667256, limit=976771055                      
[  122.141692] attempt to access beyond end of device                           
[  122.141720] sda: rw=0, want=1654667256, limit=976771055                      
[  122.141751] attempt to access beyond end of device                           
[  122.141779] sda: rw=0, want=1654667256, limit=976771055                      
[  122.141810] attempt to access beyond end of device                           
[  122.141838] sda: rw=0, want=1654667256, limit=976771055                      
[  122.141870] attempt to access beyond end of device                           
[  122.141898] sda: rw=0, want=1654667200, limit=976771055                      
[  122.141929] attempt to access beyond end of device                           
[  122.141957] sda: rw=0, want=1654667248, limit=976771055                      
[  122.141987] attempt to access beyond end of device                           
[  122.142015] sda: rw=0, want=1654667256, limit=976771055                      
[  122.142046] attempt to access beyond end of device                           
[  122.142074] sda: rw=0, want=1654667256, limit=976771055                      
[  123.167278] attempt to access beyond end of device                           
[  123.167314] sda: rw=0, want=1654667016, limit=976771055                      
[  123.167347] attempt to access beyond end of device                           
[  123.167383] sda: rw=0, want=1654667016, limit=976771055                      
[  123.167416] attempt to access beyond end of device                           
[  123.167444] sda: rw=0, want=1654667248, limit=976771055                      
[  123.167473] attempt to access beyond end of device                           
[  123.167501] sda: rw=0, want=1654667248, limit=976771055                      
[  123.167550] attempt to access beyond end of device                           
[  123.167578] sda: rw=0, want=1654667256, limit=976771055                      
[  123.167608] attempt to access beyond end of device                           
[  123.167638] sda: rw=0, want=1654667256, limit=976771055                      
[  123.167669] attempt to access beyond end of device                           
[  123.167704] sda: rw=0, want=1654667256, limit=976771055                      
[  123.167735] attempt to access beyond end of device                           
[  123.167764] sda: rw=0, want=1654667256, limit=976771055                      
[  123.167794] attempt to access beyond end of device                           
[  123.167822] sda: rw=0, want=1654667256, limit=976771055                      
[  123.167853] attempt to access beyond end of device                           
[  123.167881] sda: rw=0, want=1654667256, limit=976771055                      
[  123.167911] attempt to access beyond end of device                           
[  123.167940] sda: rw=0, want=1654667256, limit=976771055                      
[  123.167972] attempt to access beyond end of device                           
[  123.168000] sda: rw=0, want=1654667200, limit=976771055                      
[  123.168031] attempt to access beyond end of device                           
[  123.169005] sda: rw=0, want=1654667248, limit=976771055                      
[  123.169037] attempt to access beyond end of device                           
[  123.169065] sda: rw=0, want=1654667256, limit=976771055                      
[  123.169096] attempt to access beyond end of device                           
[  123.169124] sda: rw=0, want=1654667256, limit=976771055                      
[  124.194459] attempt to access beyond end of device                           
[  124.194493] sda: rw=0, want=1654667016, limit=976771055                      
[  124.194526] attempt to access beyond end of device                           
[  124.194557] sda: rw=0, want=1654667016, limit=976771055                      
[  124.194596] attempt to access beyond end of device                           
[  124.194624] sda: rw=0, want=1654667248, limit=976771055                      
[  124.194653] attempt to access beyond end of device                           
[  124.194681] sda: rw=0, want=1654667248, limit=976771055                      
[  124.194730] attempt to access beyond end of device                           
[  124.194759] sda: rw=0, want=1654667256, limit=976771055                      
[  124.194788] attempt to access beyond end of device                           
[  124.194826] sda: rw=0, want=1654667256, limit=976771055                      
[  124.194859] attempt to access beyond end of device                           
[  124.194888] sda: rw=0, want=1654667256, limit=976771055                      
[  124.194920] attempt to access beyond end of device                           
[  124.194948] sda: rw=0, want=1654667256, limit=976771055                      
[  124.194979] attempt to access beyond end of device                           
[  124.195007] sda: rw=0, want=1654667256, limit=976771055                      
[  124.195038] attempt to access beyond end of device                           
[  124.195066] sda: rw=0, want=1654667256, limit=976771055                      
[  124.195097] attempt to access beyond end of device                           
[  124.195125] sda: rw=0, want=1654667256, limit=976771055                      
[  124.195157] attempt to access beyond end of device                           
[  124.195185] sda: rw=0, want=1654667200, limit=976771055                      
[  124.195216] attempt to access beyond end of device                           
[  124.195244] sda: rw=0, want=1654667248, limit=976771055                      
[  124.195275] attempt to access beyond end of device                           
[  124.195303] sda: rw=0, want=1654667256, limit=976771055                      
[  124.195334] attempt to access beyond end of device                           
[  124.195362] sda: rw=0, want=1654667256, limit=976771055                      
[  124.800940] ISO 9660 Extensions: Microsoft Joliet Level 3                    
[  124.825097] ISO 9660 Extensions: RRIP_1991A                                  
[  125.079418] aufs 20080922                                                    
[  125.083173] loop: module loaded                                              
[  125.323752] squashfs: version 3.3 (2007/10/31) Phillip Lougher               
[  147.736442] attempt to access beyond end of device                           
[  147.736482] sda: rw=0, want=1654667016, limit=976771055                      
[  147.736512] __ratelimit: 80 callbacks suppressed                             
[  147.736541] Buffer I/O error on device sda1, logical block 206833120         
[  147.736570] attempt to access beyond end of device                           
[  147.736598] sda: rw=0, want=1654667016, limit=976771055                      
[  147.736628] Buffer I/O error on device sda1, logical block 206833120         
[  147.736666] attempt to access beyond end of device                           
[  147.736696] sda: rw=0, want=1654667248, limit=976771055                      
[  147.736726] Buffer I/O error on device sda1, logical block 206833149         
[  147.736762] attempt to access beyond end of device                           
[  147.736793] sda: rw=0, want=1654667248, limit=976771055                      
[  147.736821] Buffer I/O error on device sda1, logical block 206833149         
[  147.736873] attempt to access beyond end of device                           
[  147.736902] sda: rw=0, want=1654667256, limit=976771055                      
[  147.736931] Buffer I/O error on device sda1, logical block 206833150         
[  147.736972] attempt to access beyond end of device                           
[  147.737000] sda: rw=0, want=1654667256, limit=976771055                      
[  147.737029] Buffer I/O error on device sda1, logical block 206833150         
[  147.737063] attempt to access beyond end of device                           
[  147.737092] sda: rw=0, want=1654667256, limit=976771055                      
[  147.737120] Buffer I/O error on device sda1, logical block 206833150         
[  147.737152] attempt to access beyond end of device                           
[  147.737180] sda: rw=0, want=1654667256, limit=976771055                      
[  147.737209] Buffer I/O error on device sda1, logical block 206833150         
[  147.737240] attempt to access beyond end of device                           
[  147.737268] sda: rw=0, want=1654667256, limit=976771055                      
[  147.737297] Buffer I/O error on device sda1, logical block 206833150         
[  147.737334] attempt to access beyond end of device                           
[  147.737362] sda: rw=0, want=1654667256, limit=976771055                      
[  147.737391] Buffer I/O error on device sda1, logical block 206833150         
[  147.737423] attempt to access beyond end of device                           
[  147.737451] sda: rw=0, want=1654667256, limit=976771055                      
[  147.737483] attempt to access beyond end of device                           
[  147.737512] sda: rw=0, want=1654667200, limit=976771055                      
[  147.737543] attempt to access beyond end of device                           
[  147.737571] sda: rw=0, want=1654667248, limit=976771055                      
[  147.737602] attempt to access beyond end of device                           
[  147.737630] sda: rw=0, want=1654667256, limit=976771055                      
[  147.737661] attempt to access beyond end of device                           
[  147.737691] sda: rw=0, want=1654667256, limit=976771055                      
[  158.804847] udevd version 124 started                                        
[  159.032593] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                  
[  159.062341] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4     
[  159.653608] iTCO_vendor_support: vendor-support=0                            
[  159.657342] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)    
[  159.657421] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware                                                                            
[  159.657461] iTCO_wdt: No card detected                                       
[  159.809709] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3                                                                        
[  159.820100] ACPI: Power Button (FF) [PWRF]                                   
[  159.820166] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4                                                               
[  159.848522] ACPI: Power Button (CM) [PWRB]                                   
[  159.998842] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22                                                                               
[  159.998894] HDA Intel 0000:00:1b.0: setting latency timer to 64              
[  160.031849] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...                                                                              
[  160.068296] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17                                                                               
[  160.068346] HDA Intel 0000:01:00.1: setting latency timer to 64              
[  160.074860] input: PC Speaker as /devices/platform/pcspkr/input/input5       
[  160.116249] HDA Intel 0000:02:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17                                                                               
[  160.116295] HDA Intel 0000:02:00.1: setting latency timer to 64              
[  160.279615] parport_pc 00:08: reported by Plug and Play ACPI                 
[  160.279685] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]              
[  160.555381] attempt to access beyond end of device                           
[  160.555413] sda: rw=0, want=1654667016, limit=976771055                      
[  160.555442] __ratelimit: 5 callbacks suppressed                              
[  160.555470] Buffer I/O error on device sda1, logical block 206833120         
[  160.555499] attempt to access beyond end of device                           
[  160.555527] sda: rw=0, want=1654667016, limit=976771055                      
[  160.555556] Buffer I/O error on device sda1, logical block 206833120         
[  160.555589] attempt to access beyond end of device                           
[  160.555618] sda: rw=0, want=1654667248, limit=976771055                      
[  160.555646] Buffer I/O error on device sda1, logical block 206833149         
[  160.555675] attempt to access beyond end of device                           
[  160.555703] sda: rw=0, want=1654667248, limit=976771055                      
[  160.555731] Buffer I/O error on device sda1, logical block 206833149         
[  160.555784] attempt to access beyond end of device                           
[  160.555813] sda: rw=0, want=1654667256, limit=976771055                      
[  160.555842] Buffer I/O error on device sda1, logical block 206833150         
[  160.555895] attempt to access beyond end of device                           
[  160.555924] sda: rw=0, want=1654667256, limit=976771055                      
[  160.555953] Buffer I/O error on device sda1, logical block 206833150         
[  160.555987] attempt to access beyond end of device                           
[  160.556015] sda: rw=0, want=1654667256, limit=976771055                      
[  160.556044] Buffer I/O error on device sda1, logical block 206833150         
[  160.556075] attempt to access beyond end of device                           
[  160.556103] sda: rw=0, want=1654667256, limit=976771055                      
[  160.556131] Buffer I/O error on device sda1, logical block 206833150         
[  160.556162] attempt to access beyond end of device                           
[  160.556191] sda: rw=0, want=1654667256, limit=976771055                      
[  160.556219] Buffer I/O error on device sda1, logical block 206833150         
[  160.556250] attempt to access beyond end of device                           
[  160.556278] sda: rw=0, want=1654667256, limit=976771055                      
[  160.556306] Buffer I/O error on device sda1, logical block 206833150         
[  160.556337] attempt to access beyond end of device                           
[  160.556365] sda: rw=0, want=1654667256, limit=976771055                      
[  160.556397] attempt to access beyond end of device                           
[  160.556426] sda: rw=0, want=1654667200, limit=976771055                      
[  160.556457] attempt to access beyond end of device                           
[  160.556485] sda: rw=0, want=1654667248, limit=976771055                      
[  160.556520] attempt to access beyond end of device                           
[  160.556549] sda: rw=0, want=1654667256, limit=976771055                      
[  160.556579] attempt to access beyond end of device                           
[  160.556607] sda: rw=0, want=1654667256, limit=976771055                      
[  162.562883] ip_tables: (C) 2000-2006 Netfilter Core Team                     
[  164.022998] ACPI: WMI: Mapper loaded                                         
[  165.804017] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)                                                                         
[  165.857000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)         
[  165.857004] apm: disabled - APM is not SMP safe.                             
[  165.942371] lp0: using parport0 (interrupt-driven).                          
[  165.985194] ppdev: user-space parallel port driver                           
[  171.413669] attempt to access beyond end of device                           
[  171.413676] sda: rw=0, want=1654667016, limit=976771055                      
[  171.413679] __ratelimit: 5 callbacks suppressed                              
[  171.413682] Buffer I/O error on device sda1, logical block 206833120         
[  171.416022] attempt to access beyond end of device                           
[  171.416027] sda: rw=0, want=1654667016, limit=976771055                      
[  171.416030] Buffer I/O error on device sda1, logical block 206833120         
[  171.417821] attempt to access beyond end of device                           
[  171.417826] sda: rw=0, want=1654667248, limit=976771055                      
[  171.417829] Buffer I/O error on device sda1, logical block 206833149         
[  171.419599] attempt to access beyond end of device                           
[  171.419604] sda: rw=0, want=1654667248, limit=976771055                      
[  171.419607] Buffer I/O error on device sda1, logical block 206833149         
[  171.421423] attempt to access beyond end of device                           
[  171.421429] sda: rw=0, want=1654667256, limit=976771055                      
[  171.421431] Buffer I/O error on device sda1, logical block 206833150         
[  171.423217] attempt to access beyond end of device                           
[  171.423222] sda: rw=0, want=1654667256, limit=976771055                      
[  171.423224] Buffer I/O error on device sda1, logical block 206833150         
[  171.425010] attempt to access beyond end of device                           
[  171.425015] sda: rw=0, want=1654667256, limit=976771055                      
[  171.425018] Buffer I/O error on device sda1, logical block 206833150         
[  171.426792] attempt to access beyond end of device                           
[  171.426797] sda: rw=0, want=1654667256, limit=976771055                      
[  171.426800] Buffer I/O error on device sda1, logical block 206833150         
[  171.428574] attempt to access beyond end of device                           
[  171.428579] sda: rw=0, want=1654667256, limit=976771055                      
[  171.428582] Buffer I/O error on device sda1, logical block 206833150         
[  171.430347] attempt to access beyond end of device                           
[  171.430352] sda: rw=0, want=1654667256, limit=976771055                      
[  171.430355] Buffer I/O error on device sda1, logical block 206833150         
[  171.432129] attempt to access beyond end of device                           
[  171.432134] sda: rw=0, want=1654667256, limit=976771055                      
[  171.433236] attempt to access beyond end of device                           
[  171.433242] sda: rw=0, want=1654667200, limit=976771055                      
[  171.434345] attempt to access beyond end of device                           
[  171.434350] sda: rw=0, want=1654667248, limit=976771055                      
[  171.435447] attempt to access beyond end of device                           
[  171.435452] sda: rw=0, want=1654667256, limit=976771055                      
[  171.436549] attempt to access beyond end of device                           
[  171.436554] sda: rw=0, want=1654667256, limit=976771055                      
[  172.185083] Bluetooth: Core ver 2.13                                         
[  172.185918] NET: Registered protocol family 31                               
[  172.185921] Bluetooth: HCI device and connection manager initialized         
[  172.185924] Bluetooth: HCI socket layer initialized                          
[  172.231503] Bluetooth: L2CAP ver 2.11                                        
[  172.231508] Bluetooth: L2CAP socket layer initialized                        
[  172.307412] Bluetooth: SCO (Voice Link) ver 0.6                              
[  172.307417] Bluetooth: SCO socket layer initialized                          
[  172.695591] Bluetooth: BNEP (Ethernet Emulation) ver 1.3                     
[  172.695597] Bluetooth: BNEP filters: protocol multicast                      
[  172.709354] Bluetooth: RFCOMM socket layer initialized                       
[  172.709364] Bluetooth: RFCOMM TTY layer initialized                          
[  172.709366] Bluetooth: RFCOMM ver 1.10                                       
[  172.928440] Bridge firewalling registered                                    
[  172.928549] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.     
[  177.670414] r8169: eth0: link up                                             
[  177.670423] r8169: eth0: link up                                             
[  178.981785] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16     
[  179.122519] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining                                                                   
[  181.077315] NET: Registered protocol family 17                               
[  356.984463] device-mapper: uevent: version 1.0.3                             
[  356.984824] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com                                                                 
[  357.058379] attempt to access beyond end of device                           
[  357.058387] sda: rw=0, want=1654667016, limit=976771055                      
[  357.058389] __ratelimit: 5 callbacks suppressed                              
[  357.058393] Buffer I/O error on device sda1, logical block 206833120         
[  357.058398] attempt to access beyond end of device                           
[  357.058400] sda: rw=0, want=1654667016, limit=976771055                      
[  357.058403] Buffer I/O error on device sda1, logical block 206833120
[  357.058412] attempt to access beyond end of device
[  357.058415] sda: rw=0, want=1654667248, limit=976771055
[  357.058417] Buffer I/O error on device sda1, logical block 206833149
[  357.058420] attempt to access beyond end of device
[  357.058422] sda: rw=0, want=1654667248, limit=976771055
[  357.058425] Buffer I/O error on device sda1, logical block 206833149
[  357.058463] attempt to access beyond end of device
[  357.058466] sda: rw=0, want=1654667256, limit=976771055
[  357.058468] Buffer I/O error on device sda1, logical block 206833150
[  357.058472] attempt to access beyond end of device
[  357.058474] sda: rw=0, want=1654667256, limit=976771055
[  357.058476] Buffer I/O error on device sda1, logical block 206833150
[  357.058483] attempt to access beyond end of device
[  357.058485] sda: rw=0, want=1654667256, limit=976771055
[  357.058487] Buffer I/O error on device sda1, logical block 206833150
[  357.058495] attempt to access beyond end of device
[  357.058497] sda: rw=0, want=1654667256, limit=976771055
[  357.058499] Buffer I/O error on device sda1, logical block 206833150
[  357.058505] attempt to access beyond end of device
[  357.058508] sda: rw=0, want=1654667256, limit=976771055
[  357.058510] Buffer I/O error on device sda1, logical block 206833150
[  357.058516] attempt to access beyond end of device
[  357.058518] sda: rw=0, want=1654667256, limit=976771055
[  357.058521] Buffer I/O error on device sda1, logical block 206833150
[  357.058540] attempt to access beyond end of device
[  357.058542] sda: rw=0, want=1654667256, limit=976771055
[  357.058550] attempt to access beyond end of device
[  357.058553] sda: rw=0, want=1654667200, limit=976771055
[  357.058559] attempt to access beyond end of device
[  357.058561] sda: rw=0, want=1654667248, limit=976771055
[  357.058567] attempt to access beyond end of device
[  357.058569] sda: rw=0, want=1654667256, limit=976771055
[  357.058576] attempt to access beyond end of device
[  357.058578] sda: rw=0, want=1654667256, limit=976771055

```
And the dmraid -tay -vvvv -dddd output:
```
ubuntu@ubuntu:~$ sudo dmraid -tay -vvvv -dddd
WARN: locking /var/lock/dmraid/.lock         
NOTICE: /dev/sdb: asr     discovering        
NOTICE: /dev/sdb: ddf1    discovering        
NOTICE: /dev/sdb: hpt37x  discovering        
NOTICE: /dev/sdb: hpt45x  discovering        
NOTICE: /dev/sdb: isw     discovering        
NOTICE: /dev/sdb: isw metadata discovered    
NOTICE: /dev/sdb: jmicron discovering        
NOTICE: /dev/sdb: lsi     discovering        
NOTICE: /dev/sdb: nvidia  discovering        
NOTICE: /dev/sdb: pdc     discovering        
NOTICE: /dev/sdb: sil     discovering        
NOTICE: /dev/sdb: via     discovering        
NOTICE: /dev/sda: asr     discovering        
NOTICE: /dev/sda: ddf1    discovering        
NOTICE: /dev/sda: hpt37x  discovering        
NOTICE: /dev/sda: hpt45x  discovering        
NOTICE: /dev/sda: isw     discovering        
NOTICE: /dev/sda: isw metadata discovered    
NOTICE: /dev/sda: jmicron discovering        
NOTICE: /dev/sda: lsi     discovering        
NOTICE: /dev/sda: nvidia  discovering        
NOTICE: /dev/sda: pdc     discovering        
NOTICE: /dev/sda: sil     discovering        
NOTICE: /dev/sda: via     discovering        
DEBUG: _find_set: searching isw_gajjjcjci    
DEBUG: _find_set: not found isw_gajjjcjci    
DEBUG: _find_set: searching isw_gajjjcjci_Volume0
DEBUG: _find_set: searching isw_gajjjcjci_Volume0
DEBUG: _find_set: not found isw_gajjjcjci_Volume0
DEBUG: _find_set: not found isw_gajjjcjci_Volume0
NOTICE: added /dev/sdb to RAID set "isw_gajjjcjci"
DEBUG: _find_set: searching isw_gajjjcjci         
DEBUG: _find_set: found isw_gajjjcjci             
DEBUG: _find_set: searching isw_gajjjcjci_Volume0 
DEBUG: _find_set: searching isw_gajjjcjci_Volume0 
DEBUG: _find_set: found isw_gajjjcjci_Volume0     
DEBUG: _find_set: found isw_gajjjcjci_Volume0     
NOTICE: added /dev/sda to RAID set "isw_gajjjcjci"
DEBUG: checking isw device "/dev/sda"             
DEBUG: checking isw device "/dev/sdb"             
DEBUG: set status of set "isw_gajjjcjci_Volume0" to 16
DEBUG: set status of set "isw_gajjjcjci" to 16        
isw_gajjjcjci_Volume0: 0 1953532416 striped 2 256 /dev/sda 0 /dev/sdb 0
INFO: Activating GROUP RAID set "isw_gajjjcjci"                        
NOTICE: discovering partitions on "isw_gajjjcjci_Volume0"
NOTICE: /dev/mapper/isw_gajjjcjci_Volume0: dos     discovering
NOTICE: /dev/mapper/isw_gajjjcjci_Volume0: dos metadata discovered
DEBUG: _find_set: searching isw_gajjjcjci_Volume01
DEBUG: _find_set: not found isw_gajjjcjci_Volume01
DEBUG: _find_set: searching isw_gajjjcjci_Volume05
DEBUG: _find_set: not found isw_gajjjcjci_Volume05
DEBUG: _find_set: searching isw_gajjjcjci_Volume06
DEBUG: _find_set: not found isw_gajjjcjci_Volume06
NOTICE: created partitioned RAID set(s) for /dev/mapper/isw_gajjjcjci_Volume0
isw_gajjjcjci_Volume01: 0 1654665208 linear /dev/mapper/isw_gajjjcjci_Volume0 2048
INFO: Activating partition RAID set "isw_gajjjcjci_Volume01"
isw_gajjjcjci_Volume05: 0 286615602 linear /dev/mapper/isw_gajjjcjci_Volume0 1654678998
INFO: Activating partition RAID set "isw_gajjjcjci_Volume05"
isw_gajjjcjci_Volume06: 0 12225402 linear /dev/mapper/isw_gajjjcjci_Volume0 1941294663
INFO: Activating partition RAID set "isw_gajjjcjci_Volume06"
WARN: unlocking /var/lock/dmraid/.lock
DEBUG: freeing devices of RAID set "isw_gajjjcjci_Volume0"
DEBUG: freeing device "isw_gajjjcjci_Volume0", path "/dev/sda"
DEBUG: freeing device "isw_gajjjcjci_Volume0", path "/dev/sdb"
DEBUG: freeing devices of RAID set "isw_gajjjcjci"
DEBUG: freeing device "isw_gajjjcjci", path "/dev/sda"
DEBUG: freeing device "isw_gajjjcjci", path "/dev/sdb"
DEBUG: freeing devices of RAID set "isw_gajjjcjci_Volume01"
DEBUG: freeing device "isw_gajjjcjci_Volume01", path "/dev/mapper/isw_gajjjcjci_Volume0"
DEBUG: freeing devices of RAID set "isw_gajjjcjci_Volume05"
DEBUG: freeing device "isw_gajjjcjci_Volume05", path "/dev/mapper/isw_gajjjcjci_Volume0"
DEBUG: freeing devices of RAID set "isw_gajjjcjci_Volume06"
DEBUG: freeing device "isw_gajjjcjci_Volume06", path "/dev/mapper/isw_gajjjcjci_Volume0"

```

---

### Post by psusi on 2008-11-28
See [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).  The installer on the livecd crashes when it gets to the end and tries to install grub, so you have to do it yourself.  You also have to install dmraid on the hard disk, and in your case, you will need to change the ignore_hpa option in /etc/modprobe.d/options before rebooting.  If you just finished installing the hard disk is mounted in /target so prefix that to the above file name.

Alternatively, use the alternate cd and once you reboot into the hard drive for the first time you will still need to do the boot time override to get the system to boot, which you can then make permanent by editing /etc/modprbe.d/options.

---

### Post by Swooper86 on 2008-11-28
Gah, it had to be something simple. I forgot to uncheck Grub. Let's try this one more time... :)

---

### Post by Swooper86 on 2008-11-28
This is going well. The installer finished this time, but when I run the command "sudo chroot /target" I get the response:
```
ubuntu@ubuntu:~$ sudo chroot /target
chroot: cannot run command 'bin/bash': No such file or directory
```
Does this mean what the long version of the Fakeraid-Howto reports as 'After install, the "/target" mount point was "busy"'?

Edit: Never mind, got past this on my own. ALMOST. DONE. NOW. -_-

---

### Post by Swooper86 on 2008-11-28
Ok, I managed with some difficulty in a couple of places to follow the fakeraidhowto guide through to the end. I rebooted, the grub screen appeared normally. I selected Kubuntu, get the icon and the loading bar and then the initramfs prompt. I enter the now quite familiar 'echo options libata...' line, and then 'exit'. Instead of Kubuntu booting up now, I get this:
```
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT /dev/mapper/isw_gajjjcjci_Volume05 does not exist. Dropping to a shell!
```
and puts me back into initramfs. I must have messed up something in the grub configuration, but I don't know what. Help? :-?

Edit: Rebooting gives:
```
GRUB loading, please wait...
Error 18
```

---

### Post by psusi on 2008-11-29
The first one is because you didn't get dmraid installed on the hard drive.  Not sure why it would change when you reboot again.

Boot the livecd again and mount the raid array ( after installing dmraid ), then chroot into it and install dmraid ( to the hard disk ):

```

sudo apt-get install dmraid
sudo mount /dev/mapper/isw_gajjjcjci_Volume05 /mnt
sudo chroot /mnt
apt-get install dmraid

```

---

### Post by Swooper86 on 2008-11-29
Right when I was about to give up for the night and catch some sleep :p

I'll give it a try now, stick with me.

---

### Post by Swooper86 on 2008-11-29
Dmraid was already installed on the hard drive. I seem to have not run 'apt-get update' on it though. I'm not sure it matters.

Edit: Since I'm not sure I did this bit correctly, I'll paste in the end part of the /boot/grub/menu.lst file:
```
## ## End Default Options ##

title           Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.27-7-generic root=/dev/mapper/isw_gajjjcjci_V$
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.27-7-generic root=/dev/mapper/isw_gajjjcjci_V$
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin

title           Windows Vista Home Premium 32bit
root            (hd0,0)
chainloader     +1
### END DEBIAN AUTOMAGIC KERNELS LIST
```
Should all the linux partitions have (hd0,4) and only the Windows one (hd0,0)?

Edit2: Current situation:
On cold boot, GRUB loads normally
If I choose Vista, it boots normally too
If I choose Kubuntu, it looks like it's going to boot (loading screen appears) but then the screen goes black as if there's no signal. If I reboot from there I get GRUB Error 18.

---

### Post by Swooper86 on 2008-12-01
*shameless bump*

Still not booting. Anyone have an idea? :(

---

