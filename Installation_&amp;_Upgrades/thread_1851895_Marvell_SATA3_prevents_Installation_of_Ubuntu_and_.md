---
title: "Marvell SATA3 prevents Installation of Ubuntu and Access to Devices with LIVE CD"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by edenilno on 2011-09-29
Howdy :)

I'm a great fan of Ubuntu for several years now and never had any problems creating a dual boot machine. Windows for work and Ubuntu for living. I simply need both OS and cannot do without Windows :(

I've now gotten myself a new W7 machine with two physically separated hard drives (not a partitioned one (1) harddrive) in only one box - a combi that works flawlessly on my XP-machine.

XP-machine (AMD Athlon 7750)
Two hard drives - one XP - the other Ubuntu 11.04 -> no problems whatsoever

Windows 7 (AMD Phenom IIx4 840)
Two hard drives again - one Win 7

and for the life of me, I will not get Ubuntu installed!

If I give Ubuntu both drives, there's no problem, but when I - as required 

- install Win 7 first
- then start the Live CD
- the Live CD will start properly
-- offering no access to the hard drives
-- offering no access to plugged in thumb drives

The subsequent installation _looks_ as if carried out properly and gives the usual grub boot screen where I still can start my W7 correctly. 

But when I choose Ubuntu, I will get a messed up login screen where the left border is rather in the middle thus the login box rather at the right border of the screen, but the screen actively is continued ("rolled over") to the left side.

When I now log in _nothing_ (0, Zero, d*ck) happens - I cannot boot Ubuntu.

So I repeated the installation (after erasing and formatting partitions) with W7 + Linux Mint - same result.

Then I tried Live-CDs
- Ubuntu 11.04
- Linux Mint 11
- Knoppix
- Fedora ???

all starting properly but none of them granting me access to the windows hard drives - a feature I dearly need :confused:

The other day I read in a newsletter, that Win 8 is supposed to come up with a feature preventing a dual boot, so I ask: is this a look into the future already?

I sure hope you can help me with this

FYI: I'm a skilled reader ("power user") but I am absolutely no Geek and have no interest in technology whatsoever. So please be kind and simple.

---

### Post by vinterkind on 2011-09-29
per default windows installs itself onto the first disk in the system, whatever you chose.
even if you've chosen to install it onto the second drive it installs its boot loader on the first one.
windows has to be first, you must know. #-o

could you take out the windows drive, install ubuntu and then afterwards put the windows drive back
in again ? 

-does- the installation merely start or does it install the system ?
how come, that you've started your win7 outta grub ?

---

### Post by edenilno on 2011-09-29
Thanks for your reply :)

> could you take out the windows drive, install ubuntu and then afterwards put the windows drive back
 in again ?

One could do that, I cannot :o (no-nill-zero technical skills)


> -does- the installation merely start or does it install the system ?

The procedure runs equally long and through all the screens of the "normal" installation, but the result is as described. So, something happens, but what?

> how come, that you've started your win7 outta grub ?


Not sure, what you mean here: when the installation routine finishes, I get the usual GRUB menu, with all the usual entries, and I simply can start W7 by choosing the option.

Thank you very much for your time :)

---

### Post by vinterkind on 2011-09-29
> **edenilno said:**
> Thanks for your reply :)



One could do that, I cannot :o (no-nill-zero technical skills)




The procedure runs equally long and through all the screens of the "normal" installation, but the result is as described. So, something happens, but what?




Not sure, what you mean here: when the installation routine finishes, I get the usual GRUB menu, with all the usual entries, and I simply can start W7 by choosing the option.

Thank you very much for your time :)

ok. I havn't read properly ;)
So you've installed Ubuntu already. GRUB is there so Ubuntu is.

So what's the problem ? Let's dig in.

> But when I choose Ubuntu, I will get a messed up login screen where the  left border is rather in the middle thus the login box rather at the  right border of the screen, but the screen actively is continued  ("rolled over") to the left side.

Which graphics adaptor do you have ?
So you can change terminals with e.g. <CTRL><F2> ?

> all starting properly but none of them granting me access to the windows hard drives - a feature I dearly need 

What do you mean, no access ? no access at all or simply no access to the files on your windows hard drives ?

> The other day I read in a newsletter, that Win 8 is supposed to come up  with a feature preventing a dual boot, so I ask: is this a look into the  future already?

I've read that too. But they can't do that. They would need access to some Hardware.
It may be interesting though, how fast they would crack it ... :-)

---

### Post by edenilno on 2011-09-29
> Which graphics adaptor do you have ?

My new machine:
AMD Phenom II x4 840
8 GB RAM
AMD Radeon HD 6500 Series - the installation CD reads "AMD Sapphire"

> What do you mean, no access ? no access at all or simply no access to the files on your windows hard drives ?

On my XP/Ubuntu machine I can - running Ubuntu - access all the drives connected to the machine:

[LIST=1]
[*]the two inbuilt hard drives
[*]any plugged in USB devices
[/LIST]

without any problem whatsoever and the boon of greater speed using Ubuntu :) and the feeling to be in a safer environment.

I need Windows for my job, and I need Win 7 for several reasons - but I won't do without Ubuntu.

But now having installed W7 on a new machine with those two separate hard drives I was aiming for the same configuration: the "Evil Empire" for my job - and Ubuntu for my life.

But the "installation" of Ubuntu won't start, and using any of the Live-CDs I get the same result:

- no access AT ALL to the inbuilt hard drives
- no access AT ALL to plugged in USB devices

The only device I can access with a Live-CD is the CD/DVD drive :o

And as for restricting access to devices by Windows: in my case it is working - maybe I should mail MS and sell them my new machine for research ;)

Again, thanks very much for your time, vinterkind :D

---

### Post by Quackers on 2011-09-29
2 questions.
Does your new computer use RAID?
Does your new computer use SATA3?

---

### Post by vinterkind on 2011-09-29
> But the "installation" of Ubuntu won't start, and using any of the Live-CDs I get the same result:

- no access AT ALL to the inbuilt hard drives
- no access AT ALL to plugged in USB devices

Could you, when you're within the live environment open a terminal and invoke

```
sudo fdisk -l
```

to see your hard disks ?

any hints in /var/log/syslog ? 
or could you post the outcome of the command dmesg ?

---

### Post by vinterkind on 2011-09-29
@quackers

that could be the answer ^^
it would've never come to my mind ...

---

### Post by edenilno on 2011-09-29
Hi :)

RAID - no
SATA3 - how would I find out :o Opening the device manager I get under 

Disk Drives
- ST31000524AS ATA Divice
- ST31000524AS ATA Divice

(as there are two hard drives ;) )

And here's the result of the sudo thing:

:: begin ::
omitting empty partition (5)
 
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0d817cc7
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              14      121602   976657409    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5              14      120557   968267654+   7  HPFS/NTFS
/dev/sda6          120558      121602     8386560   82  Linux swap / Solaris
omitting empty partition (5)
 
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0d817cdf
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13055   104863263+   7  HPFS/NTFS
/dev/sdb2           13056      121601   871895745    f  W95 Ext'd (LBA)
/dev/sdb5           13056      121601   871895713+   7  HPFS/NTFS
 
Disk /dev/sdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6180a8e8
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7296    58605088+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 

:: end ::

I will now try dmesg....



Thanks for your time :D

---

### Post by Quackers on 2011-09-29
Have a look in device manager and look for the SATA controller. Or open the box and see if the connection is SATA 3 or SATA 2. 

You say in post 1 that the installation seems to go fine but you also say that it gives you no access to your hard drives.
If that's the case where are you telling Ubuntu to install? And how?

---

### Post by vinterkind on 2011-09-29
ok.
It seems you've got windows on both disks ?

> /dev/sda1   *           1          13      102400    7 ** HPFS/NTFS**
/dev/sdb1               1       13055   104863263+   7  **HPFS/NTFS**but the second one is the "real" windows drive.
what data does sda contain ?

---

### Post by Quackers on 2011-09-29
A screenshot of the Windows Disk Management screen might help here.

---

### Post by edenilno on 2011-09-29
here's the output of the dmsg command

```
[    2.080298] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    2.080300] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.080375] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    2.080377] pnp 00:0c: [mem 0x000c0000-0x000cffff]
[    2.080378] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    2.080379] pnp 00:0c: [mem 0x00100000-0xc7ffffff]
[    2.080381] pnp 00:0c: [mem 0xfec00000-0xffffffff]
[    2.080384] pnp 00:0c: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    2.080386] pnp 00:0c: disabling [mem 0x000c0000-0x000cffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    2.080389] pnp 00:0c: disabling [mem 0x000e0000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    2.080391] pnp 00:0c: disabling [mem 0x00100000-0xc7ffffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    2.080426] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    2.080428] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    2.080499] pnp: PnP ACPI: found 13 devices
[    2.080500] ACPI: ACPI bus type pnp unregistered
[    2.086049] Switching to clocksource acpi_pm
[    2.595169] pci 0000:00:05.0: BAR 15: assigned [mem 0xc8000000-0xc80fffff pref]
[    2.595172] pci 0000:00:02.0: PCI bridge to [bus 02-02]
[    2.595175] pci 0000:00:02.0:   bridge window [io  0xc000-0xcfff]
[    2.595177] pci 0000:00:02.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    2.595180] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    2.595184] pci 0000:03:00.0: BAR 6: assigned [mem 0xc8000000-0xc800ffff pref]
[    2.595186] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    2.595188] pci 0000:00:05.0:   bridge window [io  0xd000-0xefff]
[    2.595191] pci 0000:00:05.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    2.595193] pci 0000:00:05.0:   bridge window [mem 0xc8000000-0xc80fffff pref]
[    2.595197] pci 0000:00:06.0: PCI bridge to [bus 04-04]
[    2.595199] pci 0000:00:06.0:   bridge window [io  disabled]
[    2.595202] pci 0000:00:06.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    2.595204] pci 0000:00:06.0:   bridge window [mem pref disabled]
[    2.595207] pci 0000:00:0a.0: PCI bridge to [bus 01-01]
[    2.595209] pci 0000:00:0a.0:   bridge window [io  0xb000-0xbfff]
[    2.595212] pci 0000:00:0a.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    2.595214] pci 0000:00:0a.0:   bridge window [mem 0xcff00000-0xcfffffff 64bit pref]
[    2.595218] pci 0000:00:14.4: PCI bridge to [bus 05-05]
[    2.595219] pci 0000:00:14.4:   bridge window [io  disabled]
[    2.595223] pci 0000:00:14.4:   bridge window [mem disabled]
[    2.595227] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    2.595246] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.595249] pci 0000:00:02.0: setting latency timer to 64
[    2.595256] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.595258] pci 0000:00:05.0: setting latency timer to 64
[    2.595262] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.595264] pci 0000:00:06.0: setting latency timer to 64
[    2.595268] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.595270] pci 0000:00:0a.0: setting latency timer to 64
[    2.595277] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.595279] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.595280] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.595282] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    2.595284] pci_bus 0000:00: resource 8 [mem 0xc8000000-0xdfffffff]
[    2.595285] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    2.595287] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    2.595289] pci_bus 0000:02: resource 1 [mem 0xfe900000-0xfe9fffff]
[    2.595291] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    2.595293] pci_bus 0000:03: resource 0 [io  0xd000-0xefff]
[    2.595294] pci_bus 0000:03: resource 1 [mem 0xfea00000-0xfeafffff]
[    2.595296] pci_bus 0000:03: resource 2 [mem 0xc8000000-0xc80fffff pref]
[    2.595298] pci_bus 0000:04: resource 1 [mem 0xfeb00000-0xfebfffff]
[    2.595300] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    2.595301] pci_bus 0000:01: resource 1 [mem 0xfe800000-0xfe8fffff]
[    2.595303] pci_bus 0000:01: resource 2 [mem 0xcff00000-0xcfffffff 64bit pref]
[    2.595305] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    2.595306] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    2.595308] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    2.595310] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
[    2.595311] pci_bus 0000:05: resource 8 [mem 0xc8000000-0xdfffffff]
[    2.595313] pci_bus 0000:05: resource 9 [mem 0xf0000000-0xfebfffff]
[    2.595346] NET: Registered protocol family 2
[    2.595540] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    2.596825] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    2.599416] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.599753] TCP: Hash tables configured (established 524288 bind 65536)
[    2.599755] TCP reno registered
[    2.599772] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    2.599835] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    2.599964] NET: Registered protocol family 1
[    2.599964] Switched to NOHz mode on CPU #0
[    2.604912] Switched to NOHz mode on CPU #1
[    2.647674] Switched to NOHz mode on CPU #2
[    2.647683] Switched to NOHz mode on CPU #3
[    2.660533] Freeing initrd memory: 13568k freed
[    2.780060] pci 0000:02:00.0: Boot video device
[    2.780147] PCI: CLS 64 bytes, default 64
[    2.784111] PCI-DMA: Disabling AGP.
[    2.784222] PCI-DMA: aperture base @ bc000000 size 65536 KB
[    2.784224] PCI-DMA: using GART IOMMU.
[    2.784226] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    2.789227] audit: initializing netlink socket (disabled)
[    2.789242] type=2000 audit(1317309412.779:1): initialized
[    2.798475] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.799828] VFS: Disk quotas dquot_6.5.2
[    2.799890] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.800441] fuse init (API version 7.16)
[    2.800510] msgmni has been set to 15998
[    2.800858] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.800955] io scheduler noop registered
[    2.800958] io scheduler deadline registered
[    2.801014] io scheduler cfq registered (default)
[    2.801204] pcieport 0000:00:02.0: setting latency timer to 64
[    2.801239] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    2.801440] pcieport 0000:00:05.0: setting latency timer to 64
[    2.801472] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    2.801667] pcieport 0000:00:06.0: setting latency timer to 64
[    2.801698] pcieport 0000:00:06.0: irq 42 for MSI/MSI-X
[    2.801893] pcieport 0000:00:0a.0: setting latency timer to 64
[    2.801924] pcieport 0000:00:0a.0: irq 43 for MSI/MSI-X
[    2.802039] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.802058] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.802156] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    2.802160] ACPI: Power Button [PWRB]
[    2.802188] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    2.802190] ACPI: Power Button [PWRF]
[    2.802294] ACPI: acpi_idle registered with cpuidle
[    2.803155] ERST: Table is not found!
[    2.803215] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.823850] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.000645] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.240875] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.250297] hpet_acpi_add: no address or irqs in _CRS
[    3.250308] Linux agpgart interface v0.103
[    3.250991] brd: module loaded
[    3.251305] loop: module loaded
[    3.251379] i2c-core: driver [adp5520] using legacy suspend method
[    3.251380] i2c-core: driver [adp5520] using legacy resume method
[    3.251599] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.251625] pata_acpi 0000:00:14.1: setting latency timer to 64
[    3.252032] Fixed MDIO Bus: probed
[    3.252052] PPP generic driver version 2.4.2
[    3.252097] tun: Universal TUN/TAP device driver, 1.6
[    3.252098] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.252158] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.252287] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.252333] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    3.252396] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    3.330067] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    3.330093] ehci_hcd 0000:00:12.2: debug port 1
[    3.330116] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe7ff000
[    3.350045] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    3.350166] hub 1-0:1.0: USB hub found
[    3.350169] hub 1-0:1.0: 6 ports detected
[    3.350399] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.350420] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.350478] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    3.350523] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    3.350542] ehci_hcd 0000:00:13.2: debug port 1
[    3.350565] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe7fa800
[    3.370042] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    3.370164] hub 2-0:1.0: USB hub found
[    3.370168] hub 2-0:1.0: 6 ports detected
[    3.370270] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.370413] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.370436] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    3.370496] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    3.370557] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe7fe000
[    3.434168] hub 3-0:1.0: USB hub found
[    3.434174] hub 3-0:1.0: 3 ports detected
[    3.434387] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.434412] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    3.434472] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    3.434528] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe7fd000
[    3.494169] hub 4-0:1.0: USB hub found
[    3.494175] hub 4-0:1.0: 3 ports detected
[    3.494390] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.494414] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.494485] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    3.494545] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe7fc000
[    3.554180] hub 5-0:1.0: USB hub found
[    3.554186] hub 5-0:1.0: 3 ports detected
[    3.554399] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.554421] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.554485] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    3.554539] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe7fb000
[    3.614181] hub 6-0:1.0: USB hub found
[    3.614187] hub 6-0:1.0: 3 ports detected
[    3.614403] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.614426] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    3.614491] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    3.614545] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe7f9000
[    3.674179] hub 7-0:1.0: USB hub found
[    3.674185] hub 7-0:1.0: 2 ports detected
[    3.674283] uhci_hcd: USB Universal Host Controller Interface driver
[    3.674372] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    3.677118] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.677127] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.677254] mousedev: PS/2 mouse device common for all mice
[    3.677335] rtc_cmos 00:02: RTC can wake from S4
[    3.730148] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    3.730172] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    3.730258] device-mapper: uevent: version 1.0.3
[    3.730309] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    3.730425] device-mapper: multipath: version 1.2.0 loaded
[    3.730428] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.730628] cpuidle: using governor ladder
[    3.730631] cpuidle: using governor menu
[    3.730812] TCP cubic registered
[    3.730891] NET: Registered protocol family 10
[    3.731227] NET: Registered protocol family 17
[    3.731241] Registering the dns_resolver key type
[    3.731296] powernow-k8: Found 1 AMD Phenom(tm) II X4 840 Processor (4 cpu cores) (version 2.20.00)
[    3.731324] powernow-k8:    0 : pstate 0 (3200 MHz)
[    3.731325] powernow-k8:    1 : pstate 1 (2500 MHz)
[    3.731326] powernow-k8:    2 : pstate 2 (1900 MHz)
[    3.731328] powernow-k8:    3 : pstate 3 (800 MHz)
[    3.731731] PM: Hibernation image not present or could not be loaded.
[    3.731739] registered taskstats version 1
[    3.731992]   Magic number: 11:508:286
[    3.731999] ppp ppp: hash matches
[    3.732094] rtc_cmos 00:02: setting system clock to 2011-09-29 15:16:54 UTC (1317309414)
[    3.732097] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.732098] EDD information not available.
[    3.733287] Freeing unused kernel memory: 956k freed
[    3.733493] Write protecting the kernel read-only data: 10240k
[    3.734097] Freeing unused kernel memory: 184k freed
[    3.737611] Freeing unused kernel memory: 1444k freed
[    3.760204] <30>udev[116]: starting version 167
[    3.780100] Refined TSC clocksource calibration: 3206.365 MHz.
[    3.780104] Switching to clocksource tsc
[    3.788204] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.788224] r8169 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.788262] r8169 0000:01:00.0: setting latency timer to 64
[    3.788304] r8169 0000:01:00.0: irq 44 for MSI/MSI-X
[    3.788626] r8169 0000:01:00.0: eth0: RTL8168d/8111d at 0xffffc90000c58000, 00:25:22:b1:ef:6e, XID 081000c0 IRQ 44
[    3.793574] ahci 0000:00:11.0: version 3.0
[    3.793598] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.793658] ahci 0000:00:11.0: irq 45 for MSI/MSI-X
[    3.793757] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    3.793760] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    3.795370] scsi0 : ahci
[    3.795510] scsi1 : ahci
[    3.795558] scsi2 : ahci
[    3.795603] scsi3 : ahci
[    3.795652] scsi4 : ahci
[    3.795698] scsi5 : ahci
[    3.795733] ata1: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff900 irq 45
[    3.795736] ata2: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff980 irq 45
[    3.795739] ata3: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa00 irq 45
[    3.795742] ata4: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa80 irq 45
[    3.795745] ata5: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffb00 irq 45
[    3.795748] ata6: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffb80 irq 45
[    3.796176] ahci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.796241] ahci 0000:03:00.0: irq 46 for MSI/MSI-X
[    3.796294] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    3.796297] ahci 0000:03:00.0: flags: 64bit ncq sntf led only pmp fbs pio slum part sxs 
[    3.796302] ahci 0000:03:00.0: setting latency timer to 64
[    3.805219] [drm] Initialized drm 1.1.0 20060810
[    3.805407] scsi6 : ahci
[    3.805478] scsi7 : pata_atiixp
[    3.805703] scsi9 : pata_atiixp
[    3.806149] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    3.806151] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    3.806868] scsi8 : ahci
[    3.806962] ata9: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaff900 irq 46
[    3.806966] ata10: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaff980 irq 46
[    3.850061] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    4.005931] usbcore: registered new interface driver uas
[    4.140091] ata3: SATA link down (SStatus 0 SControl 300)
[    4.150077] ata2: SATA link down (SStatus 0 SControl 300)
[    4.150118] ata6: SATA link down (SStatus 0 SControl 300)
[    4.150151] ata5: SATA link down (SStatus 0 SControl 300)
[    4.150179] ata4: SATA link down (SStatus 0 SControl 300)
[    4.330041] usb 4-2: new full speed USB device using ohci_hcd and address 2
[    4.340054] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.343896] ata1.00: ATAPI: HL-DT-ST DVDRAM GH22NS70, EX00, max UDMA/100
[    4.349032] ata1.00: configured for UDMA/100
[    4.350066] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 330)
[    4.350094] ata9: SATA link up 6.0 Gbps (SStatus 133 SControl 330)
[    4.351230] ata10.00: ATA-8: ST31000524AS, JC4B, max UDMA/133
[    4.351233] ata10.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.351246] ata9.00: ATA-8: ST31000524AS, JC4B, max UDMA/133
[    4.351248] ata9.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.352597] ata10.00: configured for UDMA/133
[    4.352622] ata9.00: configured for UDMA/133
[    4.354856] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS70  EX00 PQ: 0 ANSI: 5
[    4.359896] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.359899] cdrom: Uniform CD-ROM driver Revision: 3.20
[    4.360033] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.360104] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    4.360383] scsi 6:0:0:0: Direct-Access     ATA      ST31000524AS     JC4B PQ: 0 ANSI: 5
[    4.360551] sd 6:0:0:0: Attached scsi generic sg1 type 0
[    4.360564] sd 6:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    4.360666] sd 6:0:0:0: [sda] Write Protect is off
[    4.360669] sd 6:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.360692] sd 6:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.360790] scsi 8:0:0:0: Direct-Access     ATA      ST31000524AS     JC4B PQ: 0 ANSI: 5
[    4.360932] sd 8:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    4.360971] sd 8:0:0:0: Attached scsi generic sg2 type 0
[    4.360990] sd 8:0:0:0: [sdb] Write Protect is off
[    4.360993] sd 8:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.361031] sd 8:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.394917]  sdb: sdb1 sdb2 < sdb5 >
[    4.395322] sd 8:0:0:0: [sdb] Attached SCSI disk
[    4.432558]  sda: sda1 sda2 < sda5 sda6 >
[    4.433061] sd 6:0:0:0: [sda] Attached SCSI disk
[    4.439507] Initializing USB Mass Storage driver...
[    4.439628] usb-storage 2-1:1.0: Quirks match for vid 05e3 pid 0702: 520
[    4.439670] scsi10 : usb-storage 2-1:1.0
[    4.439773] usbcore: registered new interface driver usb-storage
[    4.439775] USB Mass Storage support registered.
[    4.458541] [drm] radeon defaulting to kernel modesetting.
[    4.458543] [drm] radeon kernel modesetting enabled.
[    4.458707] radeon 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.458712] radeon 0000:02:00.0: setting latency timer to 64
[    4.460404] [drm] initializing kernel modesetting (TURKS 0x1002:0x6759).
[    4.460443] [drm] register mmio base: 0xFE9E0000
[    4.460444] [drm] register mmio size: 131072
[    4.461142] ATOM BIOS: YODA
[    4.461179] radeon 0000:02:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    4.461181] radeon 0000:02:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[    4.461403] [drm] Detected VRAM RAM=1024M, BAR=256M
[    4.461407] [drm] RAM width 128bits DDR
[    4.461489] [TTM] Zone  kernel: Available graphics memory: 4096928 kiB.
[    4.461490] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[    4.461491] [TTM] Initializing pool allocator.
[    4.461512] [drm] radeon: 1024M of VRAM memory ready
[    4.461514] [drm] radeon: 512M of GTT memory ready.
[    4.461531] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    4.461532] [drm] Driver supports precise vblank timestamp query.
[    4.461574] radeon 0000:02:00.0: irq 47 for MSI/MSI-X
[    4.461579] radeon 0000:02:00.0: radeon: using MSI.
[    4.461625] [drm] radeon: irq initialized.
[    4.461627] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    4.462403] [drm] Loading TURKS Microcode
[    4.470211] radeon 0000:02:00.0: WB enabled
[    4.486545] [drm] ring test succeeded in 2 usecs
[    4.486619] [drm] radeon: ib pool ready.
[    4.486752] [drm] ib test succeeded in 0 usecs
[    4.486759] failed to evaluate ATIF got AE_BAD_PARAMETER
[    4.486990] [drm] Radeon Display Connectors
[    4.486991] [drm] Connector 0:
[    4.486992] [drm]   HDMI-A
[    4.486993] [drm]   HPD4
[    4.486995] [drm]   DDC: 0x6450 0x6450 0x6454 0x6454 0x6458 0x6458 0x645c 0x645c
[    4.486996] [drm]   Encoders:
[    4.486997] [drm]     DFP1: INTERNAL_UNIPHY2
[    4.486998] [drm] Connector 1:
[    4.486999] [drm]   DVI-D
[    4.487000] [drm]   HPD1
[    4.487001] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[    4.487003] [drm]   Encoders:
[    4.487004] [drm]     DFP2: INTERNAL_UNIPHY
[    4.487005] [drm] Connector 2:
[    4.487006] [drm]   VGA
[    4.487007] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    4.487008] [drm]   Encoders:
[    4.487009] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    4.550409] [drm] Internal thermal controller without fan control
[    4.551274] [drm] radeon: power management initialized
[    4.617556] [drm] fb mappable at 0xD0141000
[    4.617557] [drm] vram apper at 0xD0000000
[    4.617558] [drm] size 8294400
[    4.617559] [drm] fb depth is 24
[    4.617560] [drm]    pitch is 7680
[    4.630251] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input2
[    4.630333] generic-usb 0003:046D:C52B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:12.1-2/input0
[    4.634402] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.1/input/input3
[    4.634529] generic-usb 0003:046D:C52B.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:12.1-2/input1
[    4.643232] generic-usb 0003:046D:C52B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:12.1-2/input2
[    4.643247] usbcore: registered new interface driver usbhid
[    4.643248] usbhid: USB HID core driver
[    4.826066] Console: switching to colour frame buffer device 240x67
[    4.831168] fb0: radeondrmfb frame buffer device
[    4.831169] drm: registered panic notifier
[    4.831180] [drm] Initialized radeon 2.8.0 20080528 for 0000:02:00.0 on minor 0
[    4.860056] usb 4-3: new low speed USB device using ohci_hcd and address 3
[    5.120136] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input4
[    5.120218] generic-usb 0003:045E:00DD.0004: input,hidraw3: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:12.1-3/input0
[    5.133263] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input5
[    5.133339] generic-usb 0003:045E:00DD.0005: input,hidraw4: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:12.1-3/input1
[    5.430939] scsi 10:0:0:0: Direct-Access     HITACHI_ DK23FA-60        0811 PQ: 0 ANSI: 0
[    5.431402] sd 10:0:0:0: Attached scsi generic sg3 type 0
[    5.432932] sd 10:0:0:0: [sdc] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    5.434179] sd 10:0:0:0: [sdc] Test WP failed, assume Write Enabled
[    5.435428] sd 10:0:0:0: [sdc] Cache data unavailable
[    5.435432] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[    5.437678] sd 10:0:0:0: [sdc] Test WP failed, assume Write Enabled
[    5.438928] sd 10:0:0:0: [sdc] Cache data unavailable
[    5.438931] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[    5.832525]  sdc: sdc1
[    5.835019] sd 10:0:0:0: [sdc] Test WP failed, assume Write Enabled
[    5.836269] sd 10:0:0:0: [sdc] Cache data unavailable
[    5.836272] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[    5.836275] sd 10:0:0:0: [sdc] Attached SCSI disk
[    5.846773] Btrfs loaded
[    5.851497] xor: automatically using best checksumming function: generic_sse
[    5.900024]    generic_sse: 13138.400 MB/sec
[    5.900025] xor: using function: generic_sse (13138.400 MB/sec)
[    5.901719] device-mapper: dm-raid45: initialized v0.2594b
[    9.305235] ISO 9660 Extensions: Microsoft Joliet Level 3
[    9.371326] ISO 9660 Extensions: RRIP_1991A
[    9.539711] aufs 2.1-standalone.tree-38-rcN-20110207
[    9.617819] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   62.355876] Adding 8386556k swap on /dev/sda6.  Priority:-1 extents:1 across:8386556k 
[   63.737247] <30>udev[1403]: starting version 167
[   68.440067] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   68.440108] xhci_hcd 0000:04:00.0: setting latency timer to 64
[   68.440113] xhci_hcd 0000:04:00.0: xHCI Host Controller
[   68.440240] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 8
[   68.527230] MCE: In-kernel MCE decoding enabled.
[   68.595445] xhci_hcd 0000:04:00.0: irq 18, io mem 0xfebf0000
[   68.595465] xhci_hcd 0000:04:00.0: Failed to enable MSI-X
[   68.595523] xhci_hcd 0000:04:00.0: irq 48 for MSI/MSI-X
[   68.595588] usb usb8: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[   68.595695] xHCI xhci_add_endpoint called for root hub
[   68.595697] xHCI xhci_check_bandwidth called for root hub
[   68.595720] hub 8-0:1.0: USB hub found
[   68.595723] hub 8-0:1.0: 2 ports detected
[   68.637301] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io 0xb00-0xb0f]
[   68.637304] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   68.697139] EDAC MC: Ver: 2.1.0 Apr 11 2011
[   68.916445] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   68.916536] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   69.111996] EDAC amd64_edac: v3.3.0
[   69.112181] EDAC amd64: DRAM ECC disabled.
[   69.112203] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   69.112204]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   69.112205]  (Note that use of the override may cause unknown side effects.)
[   73.143697] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   73.820233] hda_codec: ALC892: BIOS auto-probing.
[   73.829161] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   73.840035] HDA Intel 0000:02:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   73.840101] HDA Intel 0000:02:00.1: irq 49 for MSI/MSI-X
[   73.840122] HDA Intel 0000:02:00.1: setting latency timer to 64
[   75.718841] r8169 0000:01:00.0: eth0: link down
[   75.718847] r8169 0000:01:00.0: eth0: link down
[   75.719502] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   77.783608] r8169 0000:01:00.0: eth0: link up
[   77.784235] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   84.630554] lp: driver loaded but no devices found
[   84.931431] ppdev: user-space parallel port driver
[   88.300039] eth0: no IPv6 routers present
[  116.886975] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[  148.757571] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
ubuntu@ubuntu:~$ 
 
 
 
 
```

Now back to the device manager...

Thanks, guys :D

---

### Post by vinterkind on 2011-09-29
he's getting your drives though 

> scsi 6:0:0:0: Direct-Access     ATA      ST31000524AS     JC4B PQ: 0 ANSI: 5
[    4.360551] sd 6:0:0:0: Attached scsi generic sg1 type 0
[    4.360564] sd 6:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    4.360666] sd 6:0:0:0: [sda] Write Protect is off
[    4.360669] sd 6:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.360692] sd 6:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.360790] scsi 8:0:0:0: Direct-Access     ATA      ST31000524AS     JC4B PQ: 0 ANSI: 5
[    4.360932] sd 8:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    4.360971] sd 8:0:0:0: Attached scsi generic sg2 type 0
[    4.360990] sd 8:0:0:0: [sdb] Write Protect is off
[    4.360993] sd 8:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.361031] sd 8:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.394917]  sdb: sdb1 sdb2 < sdb5 >
[    4.395322] sd 8:0:0:0: [sdb] Attached SCSI disk
[    4.432558]  sda: sda1 sda2 < sda5 sda6 >
[    4.433061] sd 6:0:0:0: [sda] Attached SCSI diskto **format** the mbr of your /dev/sda you could type

```
dd if=/dev/zero of=/dev/sda bs=512 count=1
```

but you would lose all data on sda, so you need to _check_ your data there.
better copy your mbr to an usb disk with

**dd if=/dev/sda of=/media/usb/mymbr.dat bs=512 count=1**

so if there would be any problems you've got a backup mbr.

The installation begins until partitioning ? which partition scheme would you / did you chose ?

---

### Post by edenilno on 2011-09-29
Here comes the screen shot - I do hope that's the right one.



As for the proceedings: I have really no problem entering cryptic commands asf but I ask you to consider the following.

I have bought the machine last Friday. Ever since I've been reinstalling, formatting, de-partitioning and whatever, starting from scratch, always and with no exception giving the same result: digested male bovine food.

I fear now, I will again commence an operation I do not understand, which might run out of my limited sight, and giving me  a completely messed up installation of whatever - if that hasn't happened already.

For instance, I do not understand, why the boot sector is on drive 0 while the data partition (base) is on drive 1. When installing W7 I explicitly selected drive 0 for installation, and now it seems, my drive C (SYS) is on drive 0 and my data partition (base) is on drive 1.

So my layman's explanation is quite simple: I messed up.

Is there a feasible way of eradicating all traces of previous installations and really really start anew?

---

### Post by edenilno on 2011-09-29
> The installation begins until partitioning ? which partition scheme would you / did you chose ?

Well, I always chose "install along side W7" or something to that effect. 

The installation of Ubuntu runs smoothly as I'm used to and as I did on my second machine - no problems with the graphics, but but but when I then start Ubuntu... see above...I never tried to install Fedora though, but also I'm not going to :o

When installing W7 I manually and explicitly chose drive 0 for the installtion...

Thanks for your time - this is much appreciated and I wish I could give something back - but I can only read...

---

### Post by vinterkind on 2011-09-29
That's really frustrating I know. 
I once wasted a whole day just for the englightenment that ms can't install on a second hard drive without
deleting my first partition on the first hard drive. 

Maybe you could deactivate one drive in BIOS ?
If it is just a data drive, you may copy the important files to the first disk and delete all partitions on 
the second hard drive via the microsoft disk manager ?

---

### Post by vinterkind on 2011-09-29
> The installation of Ubuntu runs smoothly as I'm used to and as I did on  my second machine - no problems with the graphics, but but but when I  then start Ubuntu... see above...I never tried to install Fedora though,  but also I'm not going to :eek:

as for fedora - I use it frequently, but there is something missing. I would say - ubuntu :-)
and another rh distribution - whoa - snail i gonna get you!

so if you boot the installed ubuntu version, could you change terminals then ? (see above)

and btw. I hope if we're through all this, you never should have the reason to meddle around with this formatting and reinstalling stuff ...

---

### Post by edenilno on 2011-09-29
There's nothing really important on that machine yet - just an installation of all my stuff for Windows. Reinstalling only this is a matter of hours and baby sitting the computer.

The second drive - the one I provided for Ubuntu - is empty and I would very much like to get Ubuntu on it, but do believe me:

I have repeated this procedure many times without getting any closer to an installation of Ubuntu. So I assume 

[LIST]
[*]there must be something left over - why should there always be the same mess
[*]one cannot install Ubuntu alongside W7 on two separate hard drives
[/LIST]

I would rather much have one last go at re-installing from scratch, if you could provide me with information on how to really erase and eradicate all previous traces. Partitioning and formatting with gPartEd or P a r a g o n obviously didn't do the job.

Thanks very much for your kind and understanding remarks - and your help indeed!

---

### Post by Blasphemist on 2011-09-29
I agree with where quakers is going. You have access to the drives, you just don't think so for some reason. You have ubuntu installed to the first hard drive, as well as grub. I think this is just getting confused by your statement of the wrong issue. The issue seems to be a video issue to me. Sure lets check everything but your description of what happens tells us you do have drive access but what you see isn't displayed right.

So just to be sure, lets have you install and run boot-repair using the live cd. We can get boot and config behind us and move on to video. Just click the create summary button, nothing else in boot-repair and pass us the link it refers to. We'll be able use the link to look at lots of details. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by edenilno on 2011-09-29
> **vinterkind said:**
> 
so if you boot the installed ubuntu version, could you change terminals then ? (see above)

I cannot boot the installed version, I can only boot the Live-CD - yeah, and I concur: I simply want to use the machine and forget about the rest. 

Ta :)

---

### Post by vinterkind on 2011-09-29
> I have repeated this procedure many times without getting any closer to an installation of Ubuntu. So I assume 

[LIST]
[*]there must be something left over - why should there always be the same mess
[*]one cannot install Ubuntu alongside W7 on two separate hard drives
[/LIST]


Ok. I've got the exact second case at home :-)
running w7pro on my first drive and ubuntu 10.04 on the second.
so it has to work ;-)

I'd think Its the first one then. I'll check on my drives at home. 
Good luck - and
so long

---

### Post by oldfred on 2011-09-29
I have to agree that after the install the issue is probably the video driver. But when you install to a second drive, if you do not disconnect Windows drive, you have to use manual install (Something Else in Natty) to get the combo box on the partitioning screen to give a choice on where to install the grub2 boot loader. You definitely want the boot loader on sdb and keep sda just for Windows.

One of many alternatives to install, Since you have large drive / can be larger but I would not go over 30GB if you have a separate /home or other data partitions where you store all your files:

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

Then once you get a good install in sdb you may need nomodeset on grub kernel line or other settings to get it to boot completely. Also change BIOS to boot from sdb drive.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Quackers on 2011-09-29
There appear to be odd aspects of your Win 7 installation. As per your output below, the second drive is definitely NOT empty, although it could be empty of data. It has partitions on it.
It's odd that Win 7 has installed on two drives using both primary partitions and logical partitions. Windows tends to prefer primary partitions.
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0d817cc7

Device Boot Start End Blocks Id System
/dev/sda1 * 1 13 102400 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary. 
/dev/sda2 14 121602 976657409 5 Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5 14 120557 968267654+ 7 HPFS/NTFS
/dev/sda6 120558 121602 8386560 82 Linux swap / Solaris
omitting empty partition (5)

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0d817cdf

Device Boot Start End Blocks Id System
/dev/sdb1 1 13055 104863263+ 7 HPFS/NTFS
/dev/sdb2 13056 121601 871895745 f W95 Ext'd (LBA)
/dev/sdb5 13056 121601 871895713+ 7 HPFS/NTFS
```
Do you know how that happened? Have you done any manual partitioning lately?

---

### Post by edenilno on 2011-09-29
I sort of give up now: I'm not familiar with most of the issues concerned here and I need to get back on solid ground.

So I will now use GPartEd to 

[LIST]
[*]delete the partitions
[*]create two new partitions on those two hard drives
[*]format them ntfs resp. ext4
[*]thereafter delete the partitions again thusly ("Orson Wells") hopefully erase all traces
[*]install W7
[*]pray a silent prayer ;)
[*]install ubuntu 10.10
[/LIST]

if that fails, I shall go out and get thoroughly wasted :D

@oldfred: The link to the installation procedure seems fruitful, so there might be another reason to go out tonight ;)

@quackers: Have I done any repartitioning lately? O yes, time and again when reinstalling; I will also try to disable drive 1 when installing W7 - if I am capable - remember: reader - no geek :D

Thanks for your support, I will sure be back in a while and report. If my typing then should be slower than now - you know the reason ):P

---

### Post by Quackers on 2011-09-29
It may be an idea to just unplug the second drive (when the pc is unplugged, of course! and the battery is out, if it's a laptop) and then just install W7. It will use the whole disc anyway by default and therefore over-write all previous partitions.
You will need to delete all partitions on the second drive, or format it using mbr type. Then plug that drive in and reboot. Windows should see the drive as empty then. 
You can then install Ubuntu on that drive by manually selecting that drive during installation - NOT using "install alongside" option.

---

### Post by edenilno on 2011-09-29
Quackers :)

Thanks for the advice, but there's only one technical device over which I have complete mastery: my conventional tooth brush :D

I know how to use things and honest to god I'm skilled with using the PC - but I have no understanding whatsoever of what cable to pull. So unfortunately - pulling is no option for me - to stupid!

I promise I'll report back - cu l8er :lolflag:

---

### Post by oldfred on 2011-09-29
I have seen where users installed Windows to sdb and it put the hidden 100MB boot/recovery on sda, since that was the boot drive. Perhaps that is what occurred?

---

### Post by Quackers on 2011-09-29
I understand edenilno :-)  Good luck.

oldfred, what baffles me is the use of both primary and logical partitions in a Win 7 installation. I haven't seen a default installation do that. Maybe it didn't and edenilno has changed that, whether by chance or design.

---

### Post by edenilno on 2011-09-29
I'm just digging in my BIOS setup and discover two entries:

STORAGE CONFIGURATION

Marvell SATA3_1 -> (on selecting the entry): SATA3_1 as first line
Marvell SATA3_2 -> (on selecting...): 5th IDE Slave

Is this of any importance or relevance?

---

### Post by Quackers on 2011-09-29
Yes. I don't know the current situation, but certainly not very long ago the Marvell SATA3 Controller was not supported by Ubuntu. If that were the case I would expect the installer to hang at the partitioning stage, though that isn't happening for you.
Have a google around and see what you can dig up about that, maybe.

---

### Post by edenilno on 2011-09-29
O well - I will run the practical test ;)

---

### Post by vinterkind on 2011-09-29
Hi,

> So I will now use GPartEd to 

[LIST]
[*]delete the partitions
[*]create two new partitions on those two hard drives
[*]format them ntfs resp. ext4
[*]thereafter delete the partitions again thusly ("Orson Wells") hopefully erase all traces
[*]install W7
[*]pray a silent prayer :wink:
[*]install ubuntu 10.10
[/LIST]
So why would you create two new partitions ? You don't need to do that.
As I could see from your layout, and you've said you've got Windows installed, just delete your
/dev/sda disk. You can install gparted via softwarecenter outta ubuntu live.

You've said you've done so much as installing, repartitioning and so on. 
So simply delete all the partitions on /dev/sda. Then try to install ubuntu on that drive.
If you're using gparted you could select /dev/sdb and /dev/sda. 
you're /dev/sdb seems to be windows. 
keep /dev/sda1, just to be sure not to delete the windows boot loader partition.

---

### Post by edenilno on 2011-09-29
vinterkind,

I'm an old timer - yet around when computers learned to wa&#314;k. So I have this habit of partitioning:

WINDOWS:
c: <- Windows System 
D: <- all the data

UBUNTU:

does whatever it needs to do on the second hard drive...

I'm just about installing now and discovered, that GParted offers me as SDBA1 the hard drive that will be drive 1 during the Windows installation ???

Never mind, we'll see :D

---

### Post by oldfred on 2011-09-29
Before you install Windows be sure to set BIOS to boot sda. Then it should install to sda and install its boot loader to sda.  If you have a NTFS partition with the boot flag, so windows sees it as the active partition it should install to that.

---

### Post by vinterkind on 2011-09-29
> I'm an old timer - yet around when computers learned to wa&#314;k. So I have this habit of partitioning:

hey. don't be so formal. Can't believe I'm so much younger.

So I've started in times no windows was around ... :guitar: ... and the old Z80 was hi-performance!

> I'm just about installing now and discovered, that GParted offers me as  SDBA1 the hard drive that will be drive 1 during the Windows  installation ???

yepp I guess so.

one hint - if you'll label your disks you'll always differenciate them. 
good luck!

---

### Post by edenilno on 2011-09-29
> **vinterkind said:**
> hey. don't be so formal. Can't believe I'm so much younger.

So I've started in times no windows was around ... :guitar: ... and the old Z80 was hi-performance!


yep - I was around when you could by the most modern caclulator with basic math functions and some trigonometry plus "memory" for 5 (f-i-v-e) values!

And doing homework was much easier with it.

Currently I have some sort of progress. The windows installation went as always good, but now when installing U11.04 (10.10 doesn't support that Marvell thing) I could immediately access my windows drive :)

So, let's hope for the best :D

Ede (short for Eduard)

---

### Post by edenilno on 2011-09-29
Well - not all wishes come true :(

But there's some improvement now. I have followed the instructions [here]("http://members.iinet.net.au/~herman546/p24.html") (link provided by oldfred) to the point (where applicable).

Booting Ubuntu still yields the same result - a devided messed up log-in screen with the login box, after logging in I can hear the music, but that's it - nothing more, nothing doing...

So I use (again) the Live-CD. This time when starting, I can easily access all the devices connected to the box - null problemo - but the box simply won't boot with Linux. Confounded! ("Nero Wolfe")

What I still do not get into my head is why the display is working properly with the Live-CD and nothing doing when trying to boot from the hard disk :o

Alas, I have to concede now this is beyond my limited capabilities. It has been awfully time consuming resulting in some experience, the experience being, the next time I fork out some dough and have things installed :)

For my peace of mind I simply assume now it is the controller though accessing all the devices connected seems to contradict that assumption.

I thank all of you for your continued support - I now shall proceed as announced :D

Cheers,
Ede

---

### Post by oldfred on 2011-09-29
That is back to video issues. Did you try the nomodeset I posted above?

---

### Post by edenilno on 2011-09-29
oldfred :)

Na, that's passed me now. I have tried and installed almost every day since last Friday - I'm through with it.

I will do whatever is necessary - but it needs to further results - not frustration and disappointment. Adding the chance of incompatible hardware and my absolute lack of interest in technology...

I'm not one giving up easily - but this one I lost! 

But one of the modsquad should change the title of this thread, as it is definitely misleading - it's got nothing to do with Windows 7.

Thanks again :D

---

### Post by oldfred on 2011-09-29
Since I am here what title would you like.

---

### Post by vinterkind on 2011-09-29
> I'm not one giving up easily - but this one I lost! ok then. But I've installed all alongside this threadposting now.
appended some pics.

1. I've installed windows on a 20G drive
2. Diskmanagement Windows (10G drive (2nd) is empty)
3. I've installed Ubuntu 11.04 on the 10G drive (NOT alongside Windows)
4. since I've chosen other heres the partition scheme.

have fun,
so long and good night :-) :-({|=

---

### Post by edenilno on 2011-09-30
First of all: thanks for all the support and help!

about the title:

I'm not really sure whether this thread will ever be helpful to others so I suggest, you might even delete it?

I've just come back from my dealer (PC-dealer, yes?!) and he confirmed: this controller will not work with Ubuntu yet. So the title might be something like:

Marvell SATA3_1 - not supported - aggro galore!

How could a reader profit from this threat?

[LIST=1]
[*]There is an active and supporting community where you will get help - even instant help. So do not hesitate to consult the forums here!

[*]Even as a non-geek you will get information in a way that is easy to understand and follow.

[*]When buying a computer, do ask if the hardware supports Ubuntu
[*]Ubuntu does not support all the hardware available
[/LIST]

I am very grateful for your help and support, and I will not give up. Maybe in a few months time, Ubuntu will support my hardware and then, yes, then I shall buy one more harddisk and - have the technician install Ubuntu on that drive!

Until then I will have two machines: One with Ubuntu 11.04 and another with Win7 - I will survive, won't I?

Cheers,
Ede

---

### Post by oldfred on 2011-09-30
Replaced Windows with Marvell SATA3 since that is your issue.

Some of this is older, so I do not know if it works in your case. 

[http://en.wikipedia.org/wiki/List_of_Marvell_Technology_Group_chipsets](http://en.wikipedia.org/wiki/List_of_Marvell_Technology_Group_chipsets)
> [B]Workaround for linux and Marvell's chips that are not in the pata_marvell driver : [[4]]("http://en.wikipedia.org/wiki/List_of_Marvell_Technology_Group_chipsets#cite_note-3") [[5]]("http://en.wikipedia.org/wiki/List_of_Marvell_Technology_Group_chipsets#cite_note-4")
[/B]
 
[LIST]
[*]Ensure the [BIOS]("http://en.wikipedia.org/wiki/BIOS")  is set to AHCI. Please go to Advanced > Drive configuration >  Configure SATA as. (In later Intel(R) desktop boards you can enter the  BIOS setup program by repeatedly pressing the key during the boot  process)
[*]Use the boot parameter: all-generic-ide
[*]use the boot parameter: pci=nommconf
[/LIST]


**Re: Sata 3 drives not detected during install**
[http://ubuntuforums.org/showthread.php?t=1456238](http://ubuntuforums.org/showthread.php?t=1456238)

---

