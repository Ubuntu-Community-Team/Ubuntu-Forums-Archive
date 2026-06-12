---
title: "Installation give Kernel Oops at first boot"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by aximab on 2010-11-21
Hi all,
i tried to install ubuntu 10-10 64 bits on my laptop hp pavillon dv6-3162sf  [then 10.04-64  bits, 10.10-32 bits and 10.04 32 bits  2 days spent on it ... ] .

For the very first boot i get : 

```
 4.581196] scsi 0:0:0:0: Direct-Access     ATA      ST9640320AS      0001 PQ: 0 ANSI: 5
[    4.581370] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.581588] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    4.581633] sd 0:0:0:0: [sda] Write Protect is off
[    4.581635] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.581654] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.581788]  sda:
[    4.583101] scsi 1:0:0:0: CD-ROM            hp       DVD RW AD-7586H  KH04 PQ: 0 ANSI: 5
[    4.596259] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.596262] Uniform CD-ROM driver Revision: 3.20
[    4.596359] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.596415] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.630587] usb 1-1.3: new full speed USB device using ehci_hcd and address 3
[    4.904380] [drm] fb mappable at 0xA0140000
[    4.904382] [drm] vram apper at 0xA0000000
[    4.904383] [drm] size 4325376
[    4.904384] [drm] fb depth is 24
[    4.904385] [drm]    pitch is 5632
[    4.904467] fb1: radeondrmfb frame buffer device
[    4.904468] drm: registered panic notifier
[    4.904471] Slow work thread pool: Starting up
[    4.904504] Slow work thread pool: Ready
[    4.904510] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor 1
[    4.906223]  sda1 sda2 < sda5 >
[    4.945430] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.992927] Console: switching to colour frame buffer device 170x48
[    4.996125] fb0: inteldrmfb frame buffer device
[    5.006142] acpi device:01: registered as cooling_device2
[    5.007138] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    5.007183] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    5.013419] acpi device:13: registered as cooling_device3
[    5.019881] acpi device:14: registered as cooling_device4
[    5.020161] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:10/LNXVIDEO:02/input/input5
[    5.020193] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[    5.020218] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    5.050432] usb 2-1.3: new full speed USB device using ehci_hcd and address 3
[    5.240995] usb 2-1.5: new high speed USB device using ehci_hcd and address 4
[    6.265797] Skipping EDID probe due to cached edid
[    6.371290] Btrfs loaded
[    6.376926] xor: automatically using best checksumming function: generic_sse
[    6.419608]    generic_sse:  7553.600 MB/sec
[    6.419612] xor: using function: generic_sse (7553.600 MB/sec)
[    6.422415] device-mapper: dm-raid45: initialized v0.2594b
[    6.619081] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    8.506476] ISO 9660 Extensions: Microsoft Joliet Level 3
[    8.539025] ISO 9660 Extensions: RRIP_1991A
[    8.699507] aufs 2-standalone.tree-35-rcN-20100705
[    8.777371] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   61.581848] Adding 11284476k swap on /dev/sda5.  Priority:-1 extents:1 across:11284476k 
[   62.118570] udev[1451]: starting version 163
[   63.543927] Corrupted low memory at ffff880000006598 (6598 phys) = 100000000000
[   63.543989] ------------[ cut here ]------------
[   63.544004] WARNING: at /build/buildd/linux-2.6.35/arch/x86/kernel/check.c:134 check_for_bios_corruption+0xe5/0xf0()
[   63.544013] Hardware name: HP Pavilion dv6 Notebook PC
[   63.544015] Memory corruption detected in low memory
[   63.544016] Modules linked in: squashfs aufs nls_cp437 isofs dm_raid45 xor btrfs zlib_deflate crc32c libcrc32c radeon i915 ttm drm_kms_helper ahci r8169 drm mii intel_agp libahci i2c_algo_bit video output
[   63.544036] Pid: 10, comm: events/1 Not tainted 2.6.35-22-generic #33-Ubuntu
[   63.544039] Call Trace:
[   63.544046]  [<ffffffff8106077f>] warn_slowpath_common+0x7f/0xc0
[   63.544050]  [<ffffffff81060876>] warn_slowpath_fmt+0x46/0x50
[   63.544053]  [<ffffffff810370d5>] check_for_bios_corruption+0xe5/0xf0
[   63.544056]  [<ffffffff810370e0>] ? check_corruption+0x0/0x40
[   63.544059]  [<ffffffff810370ee>] check_corruption+0xe/0x40
[   63.544064]  [<ffffffff8107a765>] run_workqueue+0xc5/0x1a0
[   63.544068]  [<ffffffff8107a8e3>] worker_thread+0xa3/0x110
[   63.544071]  [<ffffffff8107f610>] ? autoremove_wake_function+0x0/0x40
[   63.544075]  [<ffffffff8107a840>] ? worker_thread+0x0/0x110
[   63.544077]  [<ffffffff8107f0b6>] kthread+0x96/0xa0
[   63.544081]  [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
[   63.544084]  [<ffffffff8107f020>] ? kthread+0x0/0xa0
[   63.544088]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
[   63.544090] ---[ end trace 966fc90c46d957db ]---
[   67.700058] intel ips 0000:00:1f.6: No CPUID match found.
[   67.700071] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
[   67.700076] IP: [<ffffffffa00533c6>] ips_detect_cpu+0x76/0x1d0 [intel_ips]
[   67.700083] PGD 14d771067 PUD 14d777067 PMD 0 
[   67.700087] Oops: 0000 [#1] SMP 
[   67.700089] last sysfs file: /sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/vendor
[   67.700093] CPU 1 
[   67.700094] Modules linked in: intel_ips(+) serio_raw squashfs aufs nls_cp437 isofs dm_raid45 xor btrfs zlib_deflate crc32c libcrc32c radeon i915 ttm drm_kms_helper ahci r8169 drm mii intel_agp libahci i2c_algo_bit video output
[   67.700112] 
[   67.700115] Pid: 1503, comm: modprobe Tainted: G        W   2.6.35-22-generic #33-Ubuntu 144A/HP Pavilion dv6 Notebook PC
[   67.700118] RIP: 0010:[<ffffffffa00533c6>]  [<ffffffffa00533c6>] ips_detect_cpu+0x76/0x1d0 [intel_ips]
[   67.700123] RSP: 0018:ffff88014dd31c48  EFLAGS: 00010202
[   67.700125] RAX: 0000000000c800c8 RBX: 0000000000000000 RCX: 0000000000c800c8
[   67.700127] RDX: 0000000000000000 RSI: ffff88014dd31c64 RDI: 0000000000c800c8
[   67.700129] RBP: ffff88014dd31c88 R08: 0000000000000000 R09: 0000000000000000
[   67.700132] R10: 0000000000000000 R11: 0000000000000002 R12: 0000000000c800c8
[   67.700134] R13: ffff8801536afc00 R14: ffff8801516c4090 R15: 00000000fffffff4
[   67.700136] FS:  00007f0d915ad700(0000) GS:ffff880001e40000(0000) knlGS:0000000000000000
[   67.700139] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   67.700141] CR2: 0000000000000008 CR3: 00000001504e0000 CR4: 00000000000006e0
[   67.700143] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   67.700145] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   67.700148] Process modprobe (pid: 1503, threadinfo ffff88014dd30000, task ffff88014efac4a0)
[   67.700150] Stack:
[   67.700151]  ffff88014dd31c88 ffffffff81142fa4 ffff88014dd31d14 00000000516c4000
[   67.700154] <0> ffff8801516c4000 ffff8801536afc00 ffff8801516c4000 00000000fffffff4
[   67.700158] <0> ffff88014dd31cd8 ffffffffa0053fb1 ffff88014dd31cb8 ffff880152bce910
[   67.700163] Call Trace:

``` Here this is the log of the live-cd wich i used to install ubuntu. The live-cd is able to boot but the Oops is the same than mine. 

The big issue is that this kernel is the only one i get so i can not switch to a another one. 

Can someone just tell me what should i do to get a functional linux distribution on this  laptop ? can i dowload a previous version of ubuntu ? or something ... 
I must say that i have tried to install debian from a live-cd and it gave me another kernel panic ! 
lspci : 

[PHP]00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
[/PHP]model name    : Intel(R) Pentium(R) CPU        P6100  @ 2.00GHz


PS : As a non native writer i want to apologize.

---

### Post by mörgæs on 2010-11-21
The log shows 'Memory corruption detected in low memory'. 

Have you tried to run memtest from the live CD? Might take many hours to complete.

---

### Post by dino99 on 2010-11-21
dont miss the intel-microcode and microcode.ctl packages (might be installed into synaptic)

---

### Post by aximab on 2010-11-21
First i got a way to install a ubuntu which work almost properly. I used the oem installation... there still the bug but it does'nt crash anymore.

I tried to run memtest serveral times but it always crashed and reboot  and i can't even see 
"uncoverable error" it just crashed....

Sounds pretty bad ....

---

### Post by aximab on 2010-11-21
Okay Memtest achieved and found no errors in the memory (the crash was frome me moving the usb mice). 
This might be related to this well known bug :[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/648631](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/648631)
don't you think ?
If you think it's the case can i safely try to black list the module ?
should i compile a new Kernel without this bug ? 
I don't know if it is related but i have no sound and alsamixer give me back 
cannot open mixer: Aucun fichier ou dossier de ce type  
(no such file or directory)

---

### Post by mörgæs on 2010-11-22
I can't answer this, but before going so far: Have you tried installing using the alternate installer?

---

### Post by aximab on 2010-11-23
OK i finally have the answer : my Oops was because of a bug in the Kernel. the intel_ips one [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/648631](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/648631).

I downloaded the new release and no more Oops.
Thanks

---

