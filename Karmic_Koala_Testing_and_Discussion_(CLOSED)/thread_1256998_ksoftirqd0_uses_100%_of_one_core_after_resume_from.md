---
title: "ksoftirqd/0 uses 100% of one core after resume from suspend"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jmmL on 2009-09-03
I've started a new suspend thread to deal with what seems to be a different problem. I can sucessfully resume from suspend, however, when I do I see a process called ksoftirqd/0 using 100% CPU in top.
```
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
    4 root      15  -5     0    0    0 R   100  0.0   0:19.84 ksoftirqd/0
```
It does affect perfomance, but the laptop is still usable because it is only hogging CPU time on one core. Suspend/resume has worked fine since intrepid on this laptop. I have a Packard Bell MB88-P-003. I've followed the debugging advice for suspend/resume; here is my dmesg output:
```

[ 6205.025057] wlan0: deauthenticating by local choice (reason=3)
[ 6205.115522] wlan0: disassociating by local choice (reason=3)
[ 6205.140139] sky2 eth0: disabling interface
[ 6208.129619] PM: Syncing filesystems ... done.
[ 6208.134304] PM: Preparing system for mem sleep
[ 6208.134309] Freezing user space processes ... (elapsed 0.02 seconds) done.
[ 6208.157061] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 6208.157106] PM: Entering mem sleep
[ 6208.157119] Suspending console(s) (use no_console_suspend to debug)
[ 6208.228088] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 6208.228169] sd 0:0:0:0: [sda] Stopping disk
[ 6211.141117] ACPI handle has no context!
[ 6211.141196] lirc_ite8709 00:02: disabled
[ 6211.142263] ACPI handle has no context!
[ 6211.142269] sdhci-pci 0000:09:01.1: PME# disabled
[ 6211.142277] sdhci-pci 0000:09:01.1: PCI INT B disabled
[ 6211.142285] ACPI handle has no context!
[ 6211.161169] ACPI handle has no context!
[ 6211.176239] sky2 0000:08:00.0: PME# disabled
[ 6211.208295] ahci 0000:06:00.0: PCI INT A disabled
[ 6211.376353] ata_piix 0000:00:1f.1: PCI INT A disabled
[ 6211.376368] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 6211.376377] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 6211.376386] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 6211.376394] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 6211.480269] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 6211.496117] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[ 6211.496129] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[ 6211.496141] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[ 6211.496364] PM: suspend devices took 3.340 seconds
[ 6211.496460] ricoh-mmc: Suspending.
[ 6211.496470] ricoh-mmc: Controller is now re-enabled.
[ 6211.496766] ehci_hcd 0000:00:1d.7: PME# disabled
[ 6211.512461] ehci_hcd 0000:00:1a.7: PME# disabled
[ 6211.528388] ACPI: Preparing to enter system sleep state S3
[ 6211.616444] Disabling non-boot CPUs ...
[ 6211.720020] CPU 1 is now offline
[ 6211.720024] SMP alternatives: switching to UP code
[ 6211.727265] CPU0 attaching NULL sched-domain.
[ 6211.727268] CPU1 attaching NULL sched-domain.
[ 6211.727275] CPU0 attaching NULL sched-domain.
[ 6211.727451] CPU1 is down
[ 6211.727500] Extended CMOS year: 2000
[ 6211.727500] Back to C!
[ 6211.727500] Extended CMOS year: 2000
[ 6211.727500] Enabling non-boot CPUs ...
[ 6211.727500] SMP alternatives: switching to SMP code
[ 6211.739125] Booting processor 1 APIC 0x1 ip 0x6000
[ 6211.727118] Initializing CPU#1
[ 6211.727118] Calibrating delay using timer specific routine.. 3325.08 BogoMIPS (lpj=6650161)
[ 6211.727118] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 6211.727118] CPU: L2 cache: 2048K
[ 6211.727118] CPU: Physical Processor ID: 0
[ 6211.727118] CPU: Processor Core ID: 1
[ 6211.828753] CPU1: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
[ 6211.828842] CPU0 attaching NULL sched-domain.
[ 6211.829023] Switched to high resolution mode on CPU 1
[ 6211.844028] CPU0 attaching sched-domain:
[ 6211.844033]  domain 0: span 0-1 level MC
[ 6211.844038]   groups: 0 1
[ 6211.844046] CPU1 attaching sched-domain:
[ 6211.844050]  domain 0: span 0-1 level MC
[ 6211.844054]   groups: 1 0
[ 6211.845025] CPU1 is up
[ 6211.845028] ACPI: Waking up from system sleep state S3
[ 6211.853915] pcieport-driver 0000:00:01.0: restoring config space at offset 0x6 (was 0x0, writing 0x10100)
[ 6211.853922] pcieport-driver 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[ 6211.853927] pcieport-driver 0000:00:01.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[ 6211.854064] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 6211.854189] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 6211.854322] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[ 6211.854344] ehci_hcd 0000:00:1a.7: PME# disabled
[ 6211.854472] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6211.854480] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100102)
[ 6211.854605] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x40100, writing 0x4010b)
[ 6211.854623] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x200000f0, writing 0x600000f0)
[ 6211.854635] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6211.854643] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 6211.854786] pcieport-driver 0000:00:1c.1: restoring config space at offset 0xf (was 0x40200, writing 0x4020b)
[ 6211.854801] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0xf1f1f001)
[ 6211.854807] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xf3f0f200)
[ 6211.854813] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x7 (was 0x0, writing 0x3030)
[ 6211.854825] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6211.854833] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 6211.854976] pcieport-driver 0000:00:1c.2: restoring config space at offset 0xf (was 0x40300, writing 0x40305)
[ 6211.854991] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 6211.854997] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x8 (was 0x0, writing 0xf420f420)
[ 6211.855004] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x7 (was 0x20000000, writing 0x4040)
[ 6211.855015] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6211.855024] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 6211.855167] pcieport-driver 0000:00:1c.3: restoring config space at offset 0xf (was 0x40400, writing 0x40405)
[ 6211.855182] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 6211.855188] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
[ 6211.855194] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x7 (was 0x0, writing 0x200000f0)
[ 6211.855206] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6211.855214] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 6211.855357] pcieport-driver 0000:00:1c.5: restoring config space at offset 0xf (was 0x40200, writing 0x4020b)
[ 6211.855372] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 6211.855378] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x8 (was 0x0, writing 0xf400f400)
[ 6211.855385] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x7 (was 0x20000000, writing 0x5050)
[ 6211.855396] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6211.855404] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 6211.855558] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 6211.855681] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 6211.855804] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 6211.855938] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[ 6211.855959] ehci_hcd 0000:00:1d.7: PME# disabled
[ 6211.856083] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 6211.856089] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xf430f430)
[ 6211.856095] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x228000f0)
[ 6211.856110] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100004, writing 0x100107)
[ 6211.856252] pci 0000:00:1f.0: restoring config space at offset 0x1 (was 0x2100007, writing 0x2100107)
[ 6211.856359] ata_piix 0000:00:1f.1: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
[ 6211.856495] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x205)
[ 6211.856524] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 6211.856668] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x0, writing 0x80000000)
[ 6211.856823] nvidia 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 6211.856839] nvidia 0000:01:00.0: restoring config space at offset 0x9 (was 0x1, writing 0x2001)
[ 6211.856848] nvidia 0000:01:00.0: restoring config space at offset 0x7 (was 0x4, writing 0xcc000004)
[ 6211.856857] nvidia 0000:01:00.0: restoring config space at offset 0x5 (was 0xc, writing 0xd000000c)
[ 6211.856863] nvidia 0000:01:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xce000000)
[ 6211.856873] nvidia 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 6211.857141] iwlagn 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 6211.857185] iwlagn 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf4100004)
[ 6211.857198] iwlagn 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6211.857215] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x40100106)
[ 6211.857604] ahci 0000:06:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[ 6211.857625] ahci 0000:06:00.0: restoring config space at offset 0x9 (was 0x0, writing 0xf4200000)
[ 6211.857633] ahci 0000:06:00.0: restoring config space at offset 0x8 (was 0x1, writing 0x4001)
[ 6211.857641] ahci 0000:06:00.0: restoring config space at offset 0x7 (was 0x1, writing 0x4011)
[ 6211.857649] ahci 0000:06:00.0: restoring config space at offset 0x6 (was 0x1, writing 0x4019)
[ 6211.857657] ahci 0000:06:00.0: restoring config space at offset 0x5 (was 0x1, writing 0x4015)
[ 6211.857665] ahci 0000:06:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x4021)
[ 6211.857673] ahci 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6211.857683] ahci 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 6211.858016] sky2 0000:08:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 6211.858043] sky2 0000:08:00.0: restoring config space at offset 0x6 (was 0x1, writing 0x5001)
[ 6211.858053] sky2 0000:08:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf4000004)
[ 6211.858061] sky2 0000:08:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6211.858071] sky2 0000:08:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 6211.858330] ohci1394 0000:09:01.0: restoring config space at offset 0x4 (was 0x0, writing 0xf4300000)
[ 6211.858337] ohci1394 0000:09:01.0: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[ 6211.858345] ohci1394 0000:09:01.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 6211.858478] sdhci-pci 0000:09:01.1: restoring config space at offset 0x4 (was 0x0, writing 0xf4300800)
[ 6211.858485] sdhci-pci 0000:09:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[ 6211.858493] sdhci-pci 0000:09:01.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 6211.858626] ricoh-mmc 0000:09:01.2: restoring config space at offset 0x4 (was 0x0, writing 0xf4300c00)
[ 6211.858636] ricoh-mmc 0000:09:01.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 6211.858650] ricoh-mmc: Resuming.
[ 6211.858661] ricoh-mmc: Controller is now disabled.
[ 6218.835859] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 6218.835868] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 6218.835897] usb usb3: root hub lost power or was reset
[ 6218.836039] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 6218.836049] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 6218.836079] usb usb4: root hub lost power or was reset
[ 6218.836187] ehci_hcd 0000:00:1a.7: PME# disabled
[ 6218.836192] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 6218.836200] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 6218.836205] usb usb1: root hub lost power or was reset
[ 6218.840113] ehci_hcd 0000:00:1a.7: debug port 1
[ 6218.840121] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[ 6218.840217] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 6218.840225] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 6218.929691] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 6218.929699] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 6218.929727] usb usb5: root hub lost power or was reset
[ 6218.929833] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 6218.929840] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 6218.929868] usb usb6: root hub lost power or was reset
[ 6218.929985] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 6218.929993] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 6218.930020] usb usb7: root hub lost power or was reset
[ 6218.930127] ehci_hcd 0000:00:1d.7: PME# disabled
[ 6218.930133] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 6218.930140] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 6218.930146] usb usb2: root hub lost power or was reset
[ 6218.934044] ehci_hcd 0000:00:1d.7: debug port 1
[ 6218.934052] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[ 6218.934150] pci 0000:00:1e.0: setting latency timer to 64
[ 6218.934333] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 6218.934339] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 6218.935730] ahci 0000:00:1f.2: setting latency timer to 64
[ 6219.101272] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[ 6219.101276] ata5.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[ 6219.117367] ata5.00: configured for UDMA/33
[ 6219.253184] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 6219.253282] ata3: SATA link down (SStatus 0 SControl 300)
[ 6219.254217] ata1.00: _GTF unexpected object type 0x1
[ 6219.255508] ata1.00: _GTF unexpected object type 0x1
[ 6219.255635] ata1.00: configured for UDMA/133
[ 6219.265154] ata2: SATA link down (SStatus 0 SControl 300)
[ 6219.883383] ahci 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 6219.883393] ahci 0000:06:00.0: setting latency timer to 64
[ 6219.897358] sky2 0000:08:00.0: PME# disabled
[ 6219.955041] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f4300000-f43007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[ 6219.961128] sdhci-pci 0000:09:01.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 6219.962319] pci 0000:09:01.3: PME# disabled
[ 6219.963075] lirc_ite8709 00:02: activated
[ 6220.217055] ata4: SATA link down (SStatus 0 SControl 300)
[ 6220.471507] sd 0:0:0:0: [sda] Starting disk
[ 6220.601034] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[ 6220.861034] usb 2-4: reset high speed USB device using ehci_hcd and address 2
[ 6221.273361] usb 2-4.4: reset full speed USB device using ehci_hcd and address 3
[ 6221.376859] snd-usb-audio 2-4.4:1.0: no reset_resume for driver snd-usb-audio?
[ 6221.376862] snd-usb-audio 2-4.4:1.1: no reset_resume for driver snd-usb-audio?
[ 6221.397726] PM: resume devices took 9.496 seconds
[ 6221.397729] ------------[ cut here ]------------
[ 6221.397736] WARNING: at /build/buildd/linux-2.6.31/kernel/power/suspend_test.c:52 suspend_test_finish+0x80/0x90()
[ 6221.397739] Hardware name: EasyNote MB85
[ 6221.397741] Component: resume devices
[ 6221.397743] Modules linked in: snd_usb_audio snd_usb_lib usbhid snd_hwdep binfmt_misc ppdev lp parport snd_hda_codec_conexant snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi arc4 ecb snd_rawmidi snd_seq_midi_event snd_seq iwlagn joydev snd_timer iwlcore snd_seq_device mac80211 snd uvcvideo soundcore sdhci_pci videodev sdhci ricoh_mmc psmouse snd_page_alloc cfg80211 nvidia(P) v4l1_compat led_class lirc_ite8709 serio_raw lirc_dev ohci1394 ieee1394 sky2 dm_raid45 xor fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit video output intel_agp agpgart
[ 6221.397795] Pid: 5077, comm: pm-suspend Tainted: P           2.6.31-9-generic #29-Ubuntu
[ 6221.397798] Call Trace:
[ 6221.397804]  [<c014082d>] warn_slowpath_common+0x6d/0xa0
[ 6221.397809]  [<c0170520>] ? suspend_test_finish+0x80/0x90
[ 6221.397812]  [<c0170520>] ? suspend_test_finish+0x80/0x90
[ 6221.397816]  [<c01408a6>] warn_slowpath_fmt+0x26/0x30
[ 6221.397820]  [<c0170520>] suspend_test_finish+0x80/0x90
[ 6221.397824]  [<c017030f>] suspend_devices_and_enter+0x9f/0xd0
[ 6221.397828]  [<c05661fe>] ? printk+0x18/0x1a
[ 6221.397832]  [<c01703f9>] enter_state+0xb9/0xf0
[ 6221.397835]  [<c016faed>] state_store+0x6d/0xb0
[ 6221.397839]  [<c016fa80>] ? state_store+0x0/0xb0
[ 6221.397844]  [<c030cf10>] kobj_attr_store+0x20/0x30
[ 6221.397848]  [<c02347c0>] sysfs_write_file+0x90/0x100
[ 6221.397853]  [<c01e29ea>] vfs_write+0x9a/0x190
[ 6221.397857]  [<c0234730>] ? sysfs_write_file+0x0/0x100
[ 6221.397861]  [<c056ab2b>] ? do_page_fault+0x19b/0x380
[ 6221.397864]  [<c01e34ad>] sys_write+0x3d/0x70
[ 6221.397868]  [<c010334c>] syscall_call+0x7/0xb
[ 6221.397871] ---[ end trace 9585edae54992e18 ]---
[ 6221.397919] PM: Finishing wakeup.
[ 6221.397921] Restarting tasks ... done.
[ 6223.173995] Registered led device: iwl-phy0::radio
[ 6223.174020] Registered led device: iwl-phy0::assoc
[ 6223.174044] Registered led device: iwl-phy0::RX
[ 6223.174066] Registered led device: iwl-phy0::TX
[ 6223.210992] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6223.214687] sky2 eth0: enabling interface
[ 6223.214927] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6235.413216] wlan0: authenticate with AP 00:0f:b5:bc:b5:92
[ 6235.414777] wlan0: authenticated
[ 6235.414780] wlan0: associate with AP 00:0f:b5:bc:b5:92
[ 6235.416767] wlan0: RX AssocResp from 00:0f:b5:bc:b5:92 (capab=0x471 status=0 aid=1)
[ 6235.416770] wlan0: associated
[ 6235.436579] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

---

