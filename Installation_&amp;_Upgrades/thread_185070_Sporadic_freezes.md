---
title: "Sporadic freezes"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by jonibo on 2006-05-31
Since upgrading to Dapper, I get sporadic freezes on my Fujitsu Siemens Amilo D laptop.  When the laptop is cold (meaning it has been off for a couple of hours), then it freezes at startup, after the GDM login screen, but before GNOME has finished coming up... somtimes before the splashscreen, sometimes halfway through updating the desktop/panel.  A second boot usually succeeds.

Other than that, the freezes are seemingly random... the machine may run for hours and suddenly freeze, or it may freeze up three or times in a period of half an hour.

This may be hardware related, although booting into Breezy does not provoke the problem.

I noticed the sony_acpi and pcc_acpi drivers are loaded by default, although I do not see the need for them on this laptop.  Unloading them SEEMS to alleviate the problem... but the problem is so sporadic that it may just be an allusion at this point.

So... any tips?
Why are the sony_acpi and pcc_acpi drivers loaded by default?  I tried blacklisting them by adding "blacklist sony_acpi" to /etc/modprobe.d/blacklist, but this did not prevent them from loading.  I had to add "install sony_acpi /bin/true".  Is this normal?
Has anybody else had similar problems?  ...with perhaps the same laptop model?

---

### Post by an.echte.trilingue on 2006-05-31
In my admittedly limited experience, these things are usually caused by a failing video driver.  Are you sure yours is set up properly?

---

### Post by jonibo on 2006-06-01
It's an ATI Mobility Radeon 9000 graphics chip... I also get artefacts on widgets as mentioned in other posts -- this is apparently related to ATI+cairo, although I have no proof of such myself other than what I've read in other posts.

---

### Post by PsycoEwok on 2006-06-01
I've had a very similair problem, except mine has occured on ANY distributions of Linux that I've ever tried (Ubuntu, Gentoo, and Redhat so far). It just simply freezes up after a random period of time. Sometimes it's run for an entire night, sometimes it freezes before it even finishes loading the desktop.

This also makes installing it a nightmare. I've noticed that if the installation is running off of the cd, then everything works fine, but as soon as it copies everything over to the hard drive and tries to continue the installation from there (after rebooting), it's very likely that it will lock up while installing, which is extremely frustrating.

I just downloaded Ubuntu (AMD64) 6.06, hoping that maybe my problem had been fixed in the new release. However, it appears now that the problem is even WORSE than before. It loads from the cd just fine, and I can double-click the "Install" icon to begin. But as soon as I select English for my language and try to continue, it completely freezes, and has done so consistently for 3 different attempts so far. This has made installation impossible for me.

I would GREATLY appreciate any help in this thread. Here are some of my system specs, if you must know:
CPU: AMD Athlon 64 2800+
Motherboard: [Chaintech VNF3-250]("http://www.chaintechusa.com/tw/eng/product_spec.asp?PISNo=276")
Memory: 1GB DDR
Sound Card: Sound Blaster X-Fi XtremeMusic
Video Card: ATI Radeon 9500 Pro (AGP)

---

### Post by PsycoEwok on 2006-06-01
Also, here is a thread I made back in December regarding this same problem in Breezy: [http://www.ubuntuforums.org/showthread.php?t=109991](http://www.ubuntuforums.org/showthread.php?t=109991) It's a little more detailed. And I 'did' try letting the memtest run overnight, it still produced no errors.

---

### Post by Beomagi on 2006-06-01
[quote="PsycoEwok"]
I've had a very similair problem, except mine has occured on ANY distributions of Linux that I've ever tried (Ubuntu, Gentoo, and Redhat so far). It just simply freezes up after a random period of time. Sometimes it's run for an entire night, sometimes it freezes before it even finishes loading the desktop.

This also makes installing it a nightmare. I've noticed that if the installation is running off of the cd, then everything works fine, but as soon as it copies everything over to the hard drive and tries to continue the installation from there (after rebooting), it's very likely that it will lock up while installing, which is extremely frustrating.

I just downloaded Ubuntu (AMD64) 6.06, hoping that maybe my problem had been fixed in the new release. However, it appears now that the problem is even WORSE than before. It loads from the cd just fine, and I can double-click the "Install" icon to begin. But as soon as I select English for my language and try to continue, it completely freezes, and has done so consistently for 3 different attempts so far. This has made installation impossible for me.

I would GREATLY appreciate any help in this thread. Here are some of my system specs, if you must know:
CPU: AMD Athlon 64 2800+
Motherboard: Chaintech VNF3-250
Memory: 1GB DDR
Sound Card: Sound Blaster X-Fi XtremeMusic
Video Card: ATI Radeon 9500 Pro (AGP)
[/quote]

I have similar specs and problems.
same mobo, a 3400+ Athlon 64, 2GB ddr, and a 6800gt.
mobo uses nforce 3 chipset, AC97, realtek lan, 
I have also tried disabling the onboard sound - i get a squelch after the normal ubuntu startup chime - but that didn't help.

The installer (desktop gui) for me freezes at the partitioner at 7%

I've tried 4 or 5 installs and doublechecked md5 sums. Funny thing is this happens with suse 10.1 as well. 
I have 2 drives - a pata 160GB samsung, and a sata 250GB WD.

---

### Post by az on 2006-06-01
If you are using wireless, check to see what driver you are using.  For some cards that required ndiswrapper in breezy, Dapper now has native linux drivers that can conflict and cause lockups if you unknowingly try to use both at the same time.

So you would enable ndiswrapper out of habit without realising that a linux kernel module is grabbing the device first.

---

### Post by irish1916 on 2006-06-02
I have the same problems.I have a AMD 3500,nvidia 7800gt, 2gigs of ram,maxtor 200 gig sata,seagate 80 gig pata.Every install freezes after login.I have tried ver. 5.10 and dapper + suse 10.1 +fedora core always same thing lock up after every login.Thanks for any help

---

### Post by JoWilly on 2006-06-03
This happened to me recently.

This behavior is often (but not always) due to a bad agp implementation. In this case, disabling the agp modules so that they don't load fixes the problem.

---

### Post by irish1916 on 2006-06-03
Bad AGP implementation?Do you mean on my mobo?Is there a tutorial online that you could recomend for the modules.And how reload them after to resolve the problem.
              Thank You

---

### Post by PsycoEwok on 2006-06-06
Sorry to bump the topic, but I'd just like to report that I have FIXED my freeze up problem. I'm not sure where I read it, but there was another user on this forum that claimed he had the same problem, and that he fixed it by disabling the "Cool 'n Quiet" feature in his BIOS.

I tried this and I have been running for over 2 days now without any freezes, except for when Ubuntu tries to render some of its screensavers, which I think might be a different problem from the one I just fixed.

So a BIG thank you to these forums! Now maybe I can actually get acquainted with Linux.

---

### Post by jonibo on 2006-06-07
I'll give this another bump...
I'm not convinced my problems are hardware related.  I've run memtest through numerous passes and it has never found a single error.  I can run Breezy without problems... the problem is Dapper related.
I switched from the ati driver to the fglrx driver with the same results.
My hardware is, as mentioned, a Fujitsu-Siemens Amilo D laptop... Pentium 4 processor -- no Cool'n'Quiet!

---

### Post by meesterblack on 2006-06-08
Just have to add my two cents.

I am also an AMD64 user and have been experiencing the same kind of problems. Once thing in common I have noticed is that there are *a lot* of AMD64 folks reporting this issue.  Makes me wonder.

When I did a fresh install of dapper, I couldn't get the 32-bit or the 64-bit install to ever finish -- system would hang somewhere in the middle of copying files.  FINALLY, after trying several times and doing all the partitioning and formatting of filesystems by hand ahead of using the installer, I got the 32-bit version to install.

Once booting off the hard disk, I thought I was good to go.  NOT !!  "Sporadic freezing" at random times with no one thing in common.  I experimented and even ran 'top' in an xterm window to see if there was some sort of CPU spike.  Nothing.  I ran memtest86.  Memory is fine.  I downloaded and installed nvidia binary drivers and updated xorg.conf, also commented out 'dri' as I saw someone else report this could be in assue.  Still no dice.

Then I went to grub.conf and added a kernel boot option -- 'noacpi'.  I remembered that a long time ago when I loaded CentOS (Redhat), I had issues with the install cd and acpi.  I think this may have helped *some*, but I still see ACPI modules get loaded on startup.  Perhaps the boot option I used is incorrect.

I ran several hours last night without a hangup.  The last time it froze, I was about ready to give up and go to bed. Then I decided to try one last experiment and run recently installed dvd::rip to encode a movie.  I let it run all night.

Wouldn't you expect -- the computer ran all night long and encoded the movie fine.  As soon as I sit down in front of it and work with the computer for about twenty minutes -- FREEZE.

I do not have this freezing problem on my other standard x86 Ubuntu Dapper installs.  No problems at all.  Isolated to this AMD64 machine, and it seems like widespread to me.

Let's try to crack this one for everyone.  This seems to be a big issue for a lot of folks.

Any ideas?

Thanks

-m-

---

### Post by kevlarman on 2006-06-08
I don't know if this could be a different problem, but I have pretty much the same issue... on a pentium 3, which makes me doubt that it is isolated to amd64's

---

### Post by jonibo on 2006-06-09
Well, I've found a solution on my computer... I switched from package linux-686 to linux-386.  The sporadic freezes have disappeared.
There's some issue with the 686 version of the kernel and my hardware, but I have never been able to isolate it.  Perhaps this is worth trying for the rest of you running 32-bit Ubuntu with similar problems...???

---

### Post by dogen2 on 2006-06-09
I have the same problem with my Toshiba Satellite A45-S151 laptop. If I turn off ACPI in the boot options, everything runs fine. But once I turn ACPI back on, it freezes every 12 to 18 hours. I'm going to try switching to the 386 kernel and see if that helps.

---

### Post by Papa Shango on 2006-06-09
[QUOTE=jonibo]I'll give this another bump...
I'm not convinced my problems are hardware related.  I've run memtest through numerous passes and it has never found a single error.  I can run Breezy without problems... the problem is Dapper related.
I switched from the ati driver to the fglrx driver with the same results.
My hardware is, as mentioned, a Fujitsu-Siemens Amilo D laptop... Pentium 4 processor -- no Cool'n'Quiet![/QUOTE]

  I am having this exact same problem on my laptop and it is also exclusive to Dapper.  It seems my computer will freeze completely at random.  Sometimes it is during boot, sometimes within minutes of loading the desktop and still other times it will run for hours without problem.

  Earlier in this thread someone mentioned that they believed it was a problem specific to the Mobile Radeon 9000.  I am using a Mobile Radeon 9000, however it worked perfectly fine for me in Breezy.

---

### Post by chrsjav on 2006-06-09
I have the same problem on an ATI mobility radion 9100 IGP, Pentium 4-HT on the 686 kernel.  I also didn't have this issue on breezy.  I'm reverting back to the 386 kernel now to see if that fixes it...

---

### Post by izimobil on 2006-06-10
I have the same freeze problems: my laptop freeze 1 to 4 times a day and nothing in the log files :(
I have a Radeon Mobility 9200, maybe it's the cause of the problem...

Maybe one of us should fill a bug report ? cause it's really annoying.

FWIW, here are some infos on my machine:

**Os: **Ubuntu 6.06 LTS (default install)
**Laptop: **[Sony VAIO PCG-K115Z]("http://www.vaio-link.com/common/specs.asp?L=fr&H=yes&ID=1517")

**dmesg:**
```
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[4294667.296000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000d4000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[4294667.296000]  BIOS-e820: 000000001ff70000 - 000000001ff7f000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001ff7f000 - 000000001ff80000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[4294667.296000]  BIOS-e820: 000000002ff80000 - 0000000030000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 511MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 130928
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 126832 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI present.
[4294667.296000] ATI board detected. Disabling timer routing over 8254.
[4294667.296000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6fc0
[4294667.296000] ACPI: RSDT (v001 SONY   K7       0x06040000  LTP 0x00000000) @ 0x1ff7a3e2
[4294667.296000] ACPI: FADT (v001 SONY   K7       0x06040000 PTL  0x000f4240) @ 0x1ff7ef64
[4294667.296000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1ff7efd8
[4294667.296000] ACPI: SSDT (v001  INTEL  EISTRef 0x00002000 INTL 0x20030224) @ 0x1ff7a412
[4294667.296000] ACPI: DSDT (v001  SONY  K7       0x06040000 MSFT 0x0100000e) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x8008
[4294667.296000] Allocating PCI resources starting at 40000000 (gap: 30000000:cff80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda2 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01401000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 3057.569 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.868000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294670.869000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.883000] Memory: 508084k/523712k available (1976k kernel code, 15024k reserved, 606k data, 288k init, 0k highmem)
[4294670.883000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.943000] Calibrating delay using timer specific routine.. 6116.51 BogoMIPS (lpj=3058258)
[4294670.943000] Security Framework v1.0.0 initialized
[4294670.943000] SELinux:  Disabled at boot.
[4294670.943000] Mount-cache hash table entries: 512
[4294670.943000] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[4294670.943000] CPU: After vendor identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[4294670.943000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294670.943000] CPU: L2 cache: 512K
[4294670.943000] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00000080 00004400 00000000 00000000
[4294670.943000] mtrr: v2.0 (20020519)
[4294670.943000] CPU: Intel Mobile Intel(R) Pentium(R) 4     CPU 3.06GHz stepping 09
[4294670.943000] Enabling fast FPU save and restore... done.
[4294670.943000] Enabling unmasked SIMD FPU exception support... done.
[4294670.943000] Checking 'hlt' instruction... OK.
[4294670.947000] checking if image is initramfs... it is
[4294671.425000] Freeing initrd memory: 6837k freed
[4294671.440000] ACPI: Looking for DSDT ... not found!
[4294671.441000] ACPI: setting ELCR to 0200 (from 0c00)
[4294671.468000] NET: Registered protocol family 16
[4294671.468000] EISA bus registered
[4294671.468000] ACPI: bus type pci registered
[4294671.468000] PCI: PCI BIOS revision 2.10 entry at 0xfd890, last bus=1
[4294671.468000] PCI: Using configuration type 1
[4294671.468000] ACPI: Subsystem revision 20051216
[4294671.470000] ACPI: Interpreter enabled
[4294671.470000] ACPI: Using PIC for interrupt routing
[4294671.470000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.470000] PCI: Probing PCI hardware (bus 00)
[4294671.472000] PCI quirk: region 8000-803f claimed by ali7101 ACPI
[4294671.472000] PCI quirk: region 8040-805f claimed by ali7101 SMB
[4294671.473000] Boot video device is 0000:01:05.0
[4294671.473000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.474000] ACPI: PCI Interrupt Link [LNK0] (IRQs 4) *0, disabled.
[4294671.475000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3) *11
[4294671.475000] ACPI: PCI Interrupt Link [LNK2] (IRQs 10) *11
[4294671.475000] ACPI: PCI Interrupt Link [LNK3] (IRQs 11) *0, disabled.
[4294671.475000] ACPI: PCI Interrupt Link [LNK4] (IRQs 6) *10
[4294671.475000] ACPI: PCI Interrupt Link [LNK5] (IRQs *11)
[4294671.476000] ACPI: PCI Interrupt Link [LNK6] (IRQs 9) *0, disabled.
[4294671.476000] ACPI: PCI Interrupt Link [LNK7] (IRQs 9) *11
[4294671.476000] ACPI: PCI Interrupt Link [LNK8] (IRQs 3 4 5 7 10 *11)
[4294671.477000] ACPI: Embedded Controller [EC0] (gpe 24) interrupt mode.
[4294671.478000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PPB_._PRT]
[4294671.484000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.484000] pnp: PnP ACPI init
[4294671.488000] pnp: PnP ACPI: found 11 devices
[4294671.488000] PnPBIOS: Disabled by ACPI PNP
[4294671.488000] PCI: Using ACPI for IRQ routing
[4294671.488000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.491000] pnp: 00:04: ioport range 0x40b-0x40b has been reserved
[4294671.491000] pnp: 00:04: ioport range 0x480-0x48f has been reserved
[4294671.491000] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
[4294671.491000] pnp: 00:04: ioport range 0x4d6-0x4d6 has been reserved
[4294671.491000] pnp: 00:04: ioport range 0x8000-0x807f could not be reserved
[4294671.491000] PCI: Bridge: 0000:00:01.0
[4294671.491000]   IO window: a000-afff
[4294671.491000]   MEM window: e0300000-e03fffff
[4294671.491000]   PREFETCH window: f0000000-f7ffffff
[4294671.491000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[4294671.491000]   IO window: 00001400-000014ff
[4294671.491000]   IO window: 00001800-000018ff
[4294671.491000]   PREFETCH window: 40000000-41ffffff
[4294671.491000]   MEM window: 42000000-43ffffff
[4294671.491000] **** SET: Misaligned resource pointer: de9a36c2 Type 07 Len 0
[4294671.491000] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 4
[4294671.491000] PCI: setting IRQ 4 as level-triggered
[4294671.491000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK0] -> GSI 4 (level, low) -> IRQ 4
[4294671.491000] Simple Boot Flag at 0x35 set to 0x1
[4294671.492000] audit: initializing netlink socket (disabled)
[4294671.492000] audit(1149937417.491:1): initialized
[4294671.492000] VFS: Disk quotas dquot_6.5.1
[4294671.492000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.492000] Initializing Cryptographic API
[4294671.492000] io scheduler noop registered
[4294671.492000] io scheduler anticipatory registered
[4294671.492000] io scheduler deadline registered
[4294671.492000] io scheduler cfq registered
[4294671.492000] Activating ISA DMA hang workarounds.
[4294671.492000] isapnp: Scanning for PnP cards...
[4294671.849000] isapnp: No Plug & Play device found
[4294671.862000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294671.865000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.865000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.865000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.867000] PCI: Enabling device 0000:00:03.0 (0000 -> 0003)
[4294671.867000] **** SET: Misaligned resource pointer: df9712c2 Type 07 Len 0
[4294671.867000] ACPI: PCI Interrupt Link [LNK6] enabled at IRQ 9
[4294671.867000] PCI: setting IRQ 9 as level-triggered
[4294671.867000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNK6] -> GSI 9 (level, low) -> IRQ 9
[4294671.868000] 0000:00:03.0: ttyS9 at I/O 0x1028 (irq = 9) is a 8250
[4294671.868000] 0000:00:03.0: ttyS12 at I/O 0x1040 (irq = 9) is a 8250
[4294671.868000] 0000:00:03.0: ttyS14 at I/O 0x1050 (irq = 9) is a 8250
[4294671.869000] 0000:00:03.0: ttyS16 at I/O 0x1060 (irq = 9) is a 8250
[4294671.869000] 0000:00:03.0: ttyS18 at I/O 0x1070 (irq = 9) is a 8250
[4294671.871000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.871000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.871000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.871000] mice: PS/2 mouse device common for all mice
[4294671.872000] EISA: Probing bus 0 at eisa.0
[4294671.872000] Cannot allocate resource for EISA slot 1
[4294671.872000] Cannot allocate resource for EISA slot 8
[4294671.872000] EISA: Detected 0 cards.
[4294671.872000] NET: Registered protocol family 2
[4294671.881000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[4294671.881000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.881000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.881000] TCP: Hash tables configured (established 32768 bind 32768)
[4294671.881000] TCP reno registered
[4294671.881000] TCP bic registered
[4294671.881000] NET: Registered protocol family 1
[4294671.881000] NET: Registered protocol family 8
[4294671.881000] NET: Registered protocol family 20
[4294671.881000] Using IPI Shortcut mode
[4294671.881000] ACPI wakeup devices:
[4294671.881000] PCI0 SLT1 ENET MODM USB1 USB2 USB3
[4294671.881000] ACPI: (supports S0 S3 S4 S5)
[4294671.881000] Freeing unused kernel memory: 288k freed
[4294671.909000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.926000] vga16fb: initializing
[4294671.926000] vga16fb: mapped to 0xc00a0000
[4294672.031000] Console: switching to colour frame buffer device 80x30
[4294672.031000] fb0: VGA16 VGA frame buffer device
[4294673.097000] Capability LSM initialized
[4294673.253000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294673.253000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294673.255000] ACPI: Thermal Zone [TZ01] (65 C)
[4294673.809000] ALI15X3: IDE controller at PCI slot 0000:00:0f.0
[4294673.809000] ACPI: PCI Interrupt 0000:00:0f.0[A]: no GSI
[4294673.809000] ALI15X3: chipset revision 196
[4294673.809000] ALI15X3: not 100% native mode: will probe irqs later
[4294673.809000]     ide0: BM-DMA at 0x8080-0x8087, BIOS settings: hda:DMA, hdb:pio
[4294673.809000]     ide1: BM-DMA at 0x8088-0x808f, BIOS settings: hdc:DMA, hdd:pio
[4294673.809000] Probing IDE interface ide0...
[4294674.073000] hda: TOSHIBA MK6021GAS, ATA DISK drive
[4294674.685000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.750000] Probing IDE interface ide1...
[4294675.422000] hdc: MATSHITAUJ-820D, ATAPI CD/DVD-ROM drive
[4294675.728000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.738000] hda: max request size: 128KiB
[4294675.743000] hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
[4294675.746000] hda: cache flushes supported
[4294675.747000]  hda: hda1 hda2 hda3
[4294675.845000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294675.845000] Uniform CD-ROM driver Revision: 3.20
[4294676.194000] ieee1394: Initialized config rom entry `ip1394'
[4294676.196000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294676.196000] **** SET: Misaligned resource pointer: dfc6a702 Type 07 Len 0
[4294676.196000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
[4294676.196000] PCI: setting IRQ 10 as level-triggered
[4294676.196000] ACPI: PCI Interrupt 0000:00:0a.2[C] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[4294676.230000] usbcore: registered new driver usbfs
[4294676.231000] usbcore: registered new driver hub
[4294676.233000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294676.295000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[e000b000-e000b7ff]  Max Packet=[2048]
[4294676.295000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[4294676.295000] ohci_hcd 0000:00:0c.0: OHCI Host Controller
[4294676.295000] ohci_hcd 0000:00:0c.0: new USB bus registered, assigned bus number 1
[4294676.295000] ohci_hcd 0000:00:0c.0: irq 10, io mem 0xe0009000
[4294676.326000] hub 1-0:1.0: USB hub found
[4294676.326000] hub 1-0:1.0: 3 ports detected
[4294676.427000] **** SET: Misaligned resource pointer: deaaeec2 Type 07 Len 0
[4294676.427000] ACPI: PCI Interrupt Link [LNK4] enabled at IRQ 6
[4294676.427000] PCI: setting IRQ 6 as level-triggered
[4294676.427000] ACPI: PCI Interrupt 0000:00:0c.1[B] -> Link [LNK4] -> GSI 6 (level, low) -> IRQ 6
[4294676.427000] ohci_hcd 0000:00:0c.1: OHCI Host Controller
[4294676.427000] ohci_hcd 0000:00:0c.1: new USB bus registered, assigned bus number 2
[4294676.427000] ohci_hcd 0000:00:0c.1: irq 6, io mem 0xe000a000
[4294676.458000] hub 2-0:1.0: USB hub found
[4294676.458000] hub 2-0:1.0: 2 ports detected
[4294676.540000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[4294676.561000] **** SET: Misaligned resource pointer: deaaebc2 Type 07 Len 0
[4294676.561000] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 11
[4294676.561000] PCI: setting IRQ 11 as level-triggered
[4294676.561000] ACPI: PCI Interrupt 0000:00:0c.2[C] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[4294676.561000] ehci_hcd 0000:00:0c.2: EHCI Host Controller
[4294676.582000] ehci_hcd 0000:00:0c.2: new USB bus registered, assigned bus number 3
[4294676.582000] ehci_hcd 0000:00:0c.2: irq 11, io mem 0xe000b800
[4294676.582000] ehci_hcd 0000:00:0c.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294676.582000] hub 3-0:1.0: USB hub found
[4294676.582000] hub 3-0:1.0: 5 ports detected
[4294676.868000] Attempting manual resume
[4294676.917000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294676.917000] EXT3-fs: write access will be enabled during recovery.
[4294677.153000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[4294677.311000] usbcore: registered new driver hiddev
[4294677.323000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input1
[4294677.323000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0c.0-1
[4294677.323000] usbcore: registered new driver usbhid
[4294677.323000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294677.551000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301992c17]
[4294679.093000] EXT3-fs: recovery complete.
[4294679.093000] kjournald starting.  Commit interval 5 seconds
[4294679.103000] EXT3-fs: mounted filesystem with ordered data mode.
[4294692.423000] ts: Compaq touchscreen protocol output
[4294694.201000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294694.218000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294694.357000] ath_hal: module license 'Proprietary' taints kernel.
[4294694.357000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4294694.702000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK0] -> GSI 4 (level, low) -> IRQ 4
[4294694.702000] Yenta: CardBus bridge found at 0000:00:0a.0 [104d:8175]
[4294694.702000] Yenta: Enabling burst memory read transactions
[4294694.702000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294694.702000] Yenta: Routing CardBus interrupts to PCI
[4294694.702000] Yenta TI: socket 0000:00:0a.0, mfunc 0x000a1b22, devctl 0x64
[4294694.719000] wlan: 0.8.6.0 (EXPERIMENTAL)
[4294694.725000] ath_rate_sample: 1.2
[4294694.739000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4294694.739000] PCI: Enabling device 0000:00:09.0 (0000 -> 0002)
[4294694.739000] **** SET: Misaligned resource pointer: de774202 Type 07 Len 0
[4294694.739000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 11
[4294694.739000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNK3] -> GSI 11 (level, low) -> IRQ 11
[4294694.913000] Linux agpgart interface v0.101 (c) Dave Jones
[4294694.953000] agpgart: Detected Ati IGP345M chipset
[4294695.015000] agpgart: AGP aperture is 128M @ 0xe8000000
[4294695.015000] Yenta: ISA IRQ mask 0x00a8, PCI irq 4
[4294695.015000] Socket status: 30000006
[4294695.135000] parport: PnPBIOS parport detected.
[4294695.135000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294695.180000] Build date: May 29 2006
[4294695.180000] Debugging version (IEEE80211)
[4294695.180000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294695.180000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294695.180000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4294695.180000] ath0: mac 5.9 phy 4.3 radio 4.6
[4294695.180000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4294695.180000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4294695.180000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4294695.180000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4294695.180000] ath0: Use hw queue 8 for CAB traffic
[4294695.180000] ath0: Use hw queue 9 for beacons
[4294695.180000] Debugging version (ATH)
[4294695.180000] ath0: Atheros 5212: mem=0x44000000, irq=11
[4294695.216000] ali15x3_smbus 0000:00:06.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[4294695.216000] ali15x3_smbus 0000:00:06.0: ALI15X3 not detected, module not inserted.
[4294695.233000] Real Time Clock Driver v1.12
[4294695.743000] 8139too Fast Ethernet driver 0.9.27
[4294695.743000] **** SET: Misaligned resource pointer: d98978c2 Type 07 Len 0
[4294695.743000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 3
[4294695.743000] PCI: setting IRQ 3 as level-triggered
[4294695.743000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNK1] -> GSI 3 (level, low) -> IRQ 3
[4294695.744000] eth0: RealTek RTL8139 at 0xe0a58c00, 08:00:46:ce:e3:0c, IRQ 3
[4294695.744000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294695.798000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294695.809000] input: PC Speaker as /class/input/input2
[4294695.901000] cs: IO port probe 0x100-0x3af: clean.
[4294695.903000] cs: IO port probe 0x3e0-0x4ff: clean.
[4294695.904000] cs: IO port probe 0x820-0x8ff: clean.
[4294695.905000] cs: IO port probe 0xc00-0xcf7: clean.
[4294695.906000] cs: IO port probe 0xa00-0xaff: clean.
[4294695.956000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x256eb1, caps: 0xa04753/0x0
[4294696.005000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[4294696.462000] **** SET: Misaligned resource pointer: d9957f02 Type 07 Len 0
[4294696.463000] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 9
[4294696.463000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNK7] -> GSI 9 (level, low) -> IRQ 9
[4294696.819000] NET: Registered protocol family 17
[4294696.926000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294697.493000] AC'97 1 does not respond - RESET
[4294697.493000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[4294697.493000] ali mixer 1 creating error.
[4294697.904000] lp0: using parport0 (interrupt-driven).
[4294697.962000] SCSI subsystem initialized
[4294697.971000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294697.971000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[4294697.971000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294698.075000] Adding 1052248k swap on /dev/hda3.  Priority:-1 extents:1 across:1052248k
[4294698.320000] EXT3 FS on hda2, internal journal
[4294698.496000] NET: Registered protocol family 10
[4294698.496000] lo: Disabled Privacy Extensions
[4294698.496000] IPv6 over IPv4 tunneling driver
[4294698.514000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294698.514000] md: bitmap version 4.39
[4294699.447000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294700.324000] cdrom: open failed.
[4294700.900000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[4294700.961000] NTFS volume version 3.1.
[4294707.639000] ACPI: AC Adapter [ACAD] (on-line)
[4294707.798000] ACPI: Battery Slot [BAT1] (battery absent)
[4294707.859000] ACPI: Power Button (FF) [PWRF]
[4294707.859000] ACPI: Sleep Button (CM) [SBTN]
[4294707.859000] ACPI: Power Button (CM) [PBTN]
[4294707.859000] ACPI: Lid Switch [LID]
[4294707.951000] ibm_acpi: ec object not found
[4294707.971000] pcc_acpi: loading...
[4294707.994000] ACPI Sony Notebook Control Driver v0.2 successfully installed
[4294708.060000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294708.502000] eth0: no IPv6 routers present
[4294708.541000] ath0: no IPv6 routers present
[4294708.573000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[4294713.041000] [drm] Initialized drm 1.0.1 20051102
[4294713.059000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 4 (level, low) -> IRQ 4
[4294713.060000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[4294713.818000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294713.818000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[4294713.818000] agpgart: Putting AGP V2 device at 0000:01:05.0 into 1x mode
[4294713.903000] ppdev: user-space parallel port driver
[4294714.252000] [drm] Setting GART location based on new memory map
[4294714.252000] [drm] Loading R200 Microcode
[4294714.252000] [drm] writeback test succeeded in 1 usecs
[4294714.278000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294714.278000] apm: overridden by ACPI.
[4294717.790000] input: Sony Vaio Jogdial as /class/input/input4
[4294717.791000] input: Sony Vaio Keys as /class/input/input5
[4294717.935000] sonypi: Sony Programmable I/O Controller Driverv1.26.
[4294717.935000] sonypi: detected type2 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[4294717.935000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[4294717.935000] sonypi: device allocated minor is 61
[4294719.691000] Bluetooth: Core ver 2.8
[4294719.691000] NET: Registered protocol family 31
[4294719.691000] Bluetooth: HCI device and connection manager initialized
[4294719.691000] Bluetooth: HCI socket layer initialized
[4294719.866000] Bluetooth: L2CAP ver 2.8
[4294719.866000] Bluetooth: L2CAP socket layer initialized
[4294719.873000] Bluetooth: RFCOMM socket layer initialized
[4294719.873000] Bluetooth: RFCOMM TTY layer initialized
[4294719.873000] Bluetooth: RFCOMM ver 1.7
[4295035.770000] ath0: no IPv6 routers present
[4295132.981000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[4295135.634000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[4295146.170000] ath0: no IPv6 routers present
```

**xorg.conf:**
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbVariant"    "latin9"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. M9+ 5C61 [Radeon Mobility 9000 (AGP)]"
        Driver          "ati"
        BusID           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. M9+ 5C61 [Radeon Mobility 9000 (AGP)]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

---

### Post by wanton on 2006-06-10
There's definitely no consistency as I am having the same problem too. Only I am, on a desktop machine, AMD Athlon 2000+, nVidia geforce 5200, under Breezy....no problems at all, within minutes of getting Dapper to run the gui properly, it started..... I'd get 5 minutes, 12 minutes, over half an hour, completely at random, different programs running at time of freeze, incluluding synaptic (once...three other times synaptic ran fine enough to install some apps).

I am at a loss, and am really disappointed, Ubuntu has been my desktop of choice for over 12 months, (and I upgraded from hoary to breezy with no hassles) I do not want to have to go back to MS, from whence I am posting this :(

Oh, I did apt-get install nvidia-glx (naturally...until I reinstalled it, X didn't work at all under Dapper)

---

### Post by gradavies on 2006-06-11
I've been plagued with the system freezing sporadically since loading Dapper beta a month ago. There seemed to be no logic to the freeze starting. Recently it became worse with the system freezing at gdm login. Tried reinstalling, then even going back to Breezy but the same thing happened. I finally did a low level format of the entire hard disk and did a fresh install of Dapper - same thing still happened!

Then I saw the advice to disable cool n quiet on the BIOS. Did that several hours ago - what a difference! All working brilliantly. Weather has been hot here for the last few days - perhaps that explains it getting worse. Also seems to have solved the problem of Synaptic freezing after installing programmes and the graphic shutdown only working occasionally.

---

### Post by chrsjav on 2006-06-11
Reverting back to the 386 kernel did nothing for me... I think this thread encompasses two new bugs, since some people resolve it by disabling cool n quiet, and others (like me) have no fix.

---

### Post by wanton on 2006-06-11
I am sure you are right, I am running a desktop AMD based machine and it's winter here..... it's just more annoyance (well bigger since it stops usability) to add to all the apps that got removed from my system (all installed using synaptic/apt) or even parts of gnome, like the screensaver (which I now have reinstalled but it doesn't ever kick in) 

<SIGH> I could have had (and did have) this level of frustration with a certain other OS.

---

### Post by Maggot on 2006-06-12
Been running 6.06 on laptop since release with no issue. Installed on AMD 2000+ desktop with ATI 9800 Pro Vid card yesterday. 5 min after install it froze for no reason. Did a search here and tried a few suggestions which I thought worked but again, just froze up.

edit: My bad. Computer didn't freeze, IP Address changed and my updater didn't kick in.

So doing the ATI driver install seems to have fix it so far.

---

### Post by gadgetwizard1 on 2006-06-13
I too am having sporadic freezes. I am using a Sony C1MHP laptop. Now i know this is a little unusual as it's got a 1280x600 resolution screen but Ubuntu 5.04 worked perfectly on it. After i had added a couple of adjustments (sjog, spictrrl,  sonypi)  everything worked, sleep, jog dial etc.

So i was really dissapointed when upgrading to 6.06 to find that nothing worked. Sleep no longer works and the random freezes make it almost unusable. In addition to this the fan seems run constantly unlike when using 5.04.

This and other forums suggested disabling 'dri'. Tried that but no change. It was also suggested i try the 'vesa' driver. Tried that too but no change, and anyway i could not re-instate the correct resolution.. All this despite a fresh install of 6.06. I have compared the xorg.conf file from an re-install of 5.04 with 6.06 and can't see any difference. They both load 'ati' as the drivers for the graphics card.

I can't get over how dissapointed i am. I have installed Ubuntu 6.06 onto an IBM X21 and can't get over how fantastic it looks and feels. I really would have liked to have this on my little C1MHP.

So i have given up with 6.06 and re-installed 5.04 (for the second time). This has since been running and sleeping and just being brilliant for more than a week now.

Maybe someday there will be a permanent fix for this but until there is i'm sticking with 5.04 and recommending others to tread carefully. Just because 5.04 and 5.10 worked does not automatically mean the next version will too.

---

### Post by MarcDM on 2006-06-15
[QUOTE=gadgetwizard1]but until there is i'm sticking with 5.04 and recommending others to tread carefully. Just because 5.04 and 5.10 worked does not automatically mean the next version will too.[/QUOTE]
 off topic but, how about running Hoary or Breezy with Gnome and a few other apps from Dapper? How hard would that be?

But on to the freezing, It happens to me too.  Absolutely no pattern to when it will freeze. 

Also, Dapper has a bad habit of slowing down my mouse to process other things, Breezy never did that. 

For the record, I'm running on an Averatec 4155-EH1 with AMD Turion64 MT30 (1.6Ghz 64Bit), 512MB RAM and SiS onboard sound, lan and video. 

The modem doesn't work, and the wifi card was automatically detected and uses the rt2500 module.

I've modified xorg.conf to include a DisplaySize, so I can get 96dpi by default (in xfce). 

Gonna look up the cool 'n' quiet though. If it doesn't freeze again, I'll be back next month to say so.

---

### Post by Latch2112 on 2006-08-31
I've been using the latest for about a week.  Everything has been good until I went to copy 3 ~600 MB files to a share on my Windows box.  Nautilus copied the first file and froze solid during the second.  Hard reset was the only cure as everything was totally borked.  After that, it locked up again twice while trying to copy file2.  File3 copied without hanging the system, but I suspect that was just luck.  This system had been up & running Windows Server 2003 for the past several months as a torrent client and was solid as a rock, so I doubt very much that it's a hardware issue.  Plus, it never hung for a week while I did everything else in the world except copy files over the network to a Windows box.

---

