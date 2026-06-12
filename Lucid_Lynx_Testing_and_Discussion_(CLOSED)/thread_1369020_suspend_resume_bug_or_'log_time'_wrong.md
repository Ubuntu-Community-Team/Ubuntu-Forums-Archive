---
title: "suspend resume bug or 'log time' wrong?"
date: 2009-12-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by GeorgeVita on 2009-12-31
Hi! Triggered from: > **sarthorks said:**
> ...When i suspend my laptop (either by shutting the lid, or using power button and then the suspend option), and say keep it on suspend for a few minutes, and then wake the system, my kernel logfile shows a little different story...

I tested the same on my LL a1+updates (kernel 2.6.32-9-generic #13) with the same results (resume done 15:13):

>>> Preparing system to sleep at 'resume' time!

```
Dec 31 15:08:27 LL23dec kernel: [   23.005659] type=1505 audit(1262264907.747:10):  operation="profile_load" pid=1098 name="/usr/bin/evince-previewer"
Dec 31 15:08:27 LL23dec kernel: [   23.032179] type=1505 audit(1262264907.771:11):  operation="profile_load" pid=1098 name="/usr/bin/evince-thumbnailer"
Dec 31 15:08:27 LL23dec kernel: [   23.122392] Skipping EDID probe due to cached edid
Dec 31 15:08:27 LL23dec kernel: [   23.161150] Skipping EDID probe due to cached edid
Dec 31 15:08:28 LL23dec kernel: [   23.542728] ppdev: user-space parallel port driver
Dec 31 15:08:29 LL23dec kernel: [   24.909253] Skipping EDID probe due to cached edid
Dec 31 15:08:29 LL23dec kernel: [   24.950085] Skipping EDID probe due to cached edid
Dec 31 15:08:29 LL23dec kernel: [   24.989327] Skipping EDID probe due to cached edid
Dec 31 15:08:36 LL23dec kernel: [   32.252050] wlan0: no IPv6 routers present
Dec 31 15:10:02 LL23dec kernel: [  117.270553] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 112
Dec 31 15:10:05 LL23dec kernel: [  120.810029] Skipping EDID probe due to cached edid
Dec 31 15:10:05 LL23dec kernel: [  120.854406] Skipping EDID probe due to cached edid
Dec 31 15:10:05 LL23dec kernel: [  120.909815] Skipping EDID probe due to cached edid
Dec 31 15:10:06 LL23dec kernel: [  122.249213] Skipping EDID probe due to cached edid
Dec 31 15:10:08 LL23dec kernel: [  123.493227] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
Dec 31 15:13:23 LL23dec kernel: [  168.412457] PM: Syncing filesystems ... done.
Dec 31 15:13:23 LL23dec kernel: [  168.448080] PM: Preparing system for mem sleep
Dec 31 15:13:23 LL23dec kernel: [  168.448094] Freezing user space processes ... (elapsed 0.00 seconds) done.
Dec 31 15:13:23 LL23dec kernel: [  168.449751] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Dec 31 15:13:23 LL23dec kernel: [  168.450018] PM: Entering mem sleep
Dec 31 15:13:23 LL23dec kernel: [  168.450042] Suspending console(s) (use no_console_suspend to debug)
Dec 31 15:13:23 LL23dec kernel: [  168.451489] btusb_intr_complete: hci0 urb f318c400 failed to resubmit (1)
Dec 31 15:13:23 LL23dec kernel: [  168.452473] btusb_bulk_complete: hci0 urb f318c100 failed to resubmit (1)
Dec 31 15:13:23 LL23dec kernel: [  168.453473] btusb_bulk_complete: hci0 urb f318c180 failed to resubmit (1)
Dec 31 15:13:23 LL23dec kernel: [  168.500091] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Dec 31 15:13:23 LL23dec kernel: [  168.500538] sd 0:0:0:0: [sda] Stopping disk
Dec 31 15:13:23 LL23dec kernel: [  169.343115] ACPI handle has no context!
Dec 31 15:13:23 LL23dec kernel: [  169.343208] rt2860 0000:01:00.0: PCI INT A disabled
Dec 31 15:13:23 LL23dec kernel: [  169.343218] ACPI handle has no context!
Dec 31 15:13:23 LL23dec kernel: [  169.356222] ACPI handle has no context!
Dec 31 15:13:23 LL23dec kernel: [  169.356241] ATL1E 0000:03:00.0: PCI INT A disabled
Dec 31 15:13:23 LL23dec kernel: [  169.356255] ACPI handle has no context!
Dec 31 15:13:23 LL23dec kernel: [  169.372312] ata_piix 0000:00:1f.2: PCI INT B disabled
Dec 31 15:13:23 LL23dec kernel: [  169.388096] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Dec 31 15:13:23 LL23dec kernel: [  169.388119] uhci_hcd 0000:00:1d.3: PCI INT D disabled
Dec 31 15:13:23 LL23dec kernel: [  169.388138] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Dec 31 15:13:23 LL23dec kernel: [  169.388158] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Dec 31 15:13:23 LL23dec kernel: [  169.388177] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Dec 31 15:13:23 LL23dec kernel: [  169.388234] HDA Intel 0000:00:1b.0: PCI INT A disabled
Dec 31 15:13:23 LL23dec kernel: [  169.424725] i915 0000:00:02.0: PCI INT A disabled
Dec 31 15:13:23 LL23dec kernel: [  169.440188] PM: suspend devices took 0.992 seconds
Dec 31 15:13:23 LL23dec kernel: [  169.456301] ACPI: Preparing to enter system sleep state S3
Dec 31 15:13:23 LL23dec kernel: [  169.485230] Disabling non-boot CPUs ...
Dec 31 15:13:23 LL23dec kernel: [  169.588034] CPU 1 is now offline
Dec 31 15:13:23 LL23dec kernel: [  169.588040] SMP alternatives: switching to UP code
Dec 31 15:13:23 LL23dec kernel: [  169.593511] CPU0 attaching NULL sched-domain.
Dec 31 15:13:23 LL23dec kernel: [  169.593519] CPU1 attaching NULL sched-domain.
Dec 31 15:13:23 LL23dec kernel: [  169.593533] CPU0 attaching NULL sched-domain.
Dec 31 15:13:23 LL23dec kernel: [  169.594157] CPU1 is down
Dec 31 15:13:23 LL23dec kernel: [  169.594179] Back to C!
Dec 31 15:13:23 LL23dec kernel: [  169.594179] CPU0: Thermal LVT vector (0xfa) already installed
Dec 31 15:13:23 LL23dec kernel: [  169.594179] Enabling non-boot CPUs ...
Dec 31 15:13:23 LL23dec kernel: [  169.594179] SMP alternatives: switching to SMP code
Dec 31 15:13:23 LL23dec kernel: [  169.599607] Booting processor 1 APIC 0x1 ip 0x6000
Dec 31 15:13:23 LL23dec kernel: [  169.593243] Initializing CPU#1
Dec 31 15:13:23 LL23dec kernel: [  169.593243] Calibrating delay using timer specific routine.. 3191.99 BogoMIPS (lpj=6383996)
Dec 31 15:13:23 LL23dec kernel: [  169.593243] CPU: L1 I cache: 32K, L1 D cache: 24K
Dec 31 15:13:23 LL23dec kernel: [  169.593243] CPU: L2 cache: 512K
Dec 31 15:13:23 LL23dec kernel: [  169.593243] CPU: Physical Processor ID: 0
Dec 31 15:13:23 LL23dec kernel: [  169.593243] CPU: Processor Core ID: 0
Dec 31 15:13:23 LL23dec kernel: [  169.593243] CPU1: Thermal monitoring enabled (TM2)
Dec 31 15:13:23 LL23dec kernel: [  169.688156] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
Dec 31 15:13:23 LL23dec kernel: [  169.688269] CPU0 attaching NULL sched-domain.
Dec 31 15:13:23 LL23dec kernel: [  169.700040] CPU0 attaching sched-domain:
Dec 31 15:13:23 LL23dec kernel: [  169.700049]  domain 0: span 0-1 level SIBLING
Dec 31 15:13:23 LL23dec kernel: [  169.700056]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
Dec 31 15:13:23 LL23dec kernel: [  169.700071]   domain 1: span 0-1 level MC
Dec 31 15:13:23 LL23dec kernel: [  169.700077]    groups: 0-1 (cpu_power = 1178)
Dec 31 15:13:23 LL23dec kernel: [  169.700089] CPU1 attaching sched-domain:
Dec 31 15:13:23 LL23dec kernel: [  169.700095]  domain 0: span 0-1 level SIBLING
Dec 31 15:13:23 LL23dec kernel: [  169.700101]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
Dec 31 15:13:23 LL23dec kernel: [  169.700115]   domain 1: span 0-1 level MC
Dec 31 15:13:23 LL23dec kernel: [  169.700121]    groups: 0-1 (cpu_power = 1178)
Dec 31 15:13:23 LL23dec kernel: [  169.704040] CPU1 is up
Dec 31 15:13:23 LL23dec kernel: [  169.704226] ACPI: Waking up from system sleep state S3
Dec 31 15:13:23 LL23dec kernel: [  169.772519] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
Dec 31 15:13:23 LL23dec kernel: [  169.772580] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x1fff1, writing 0x80318021)
Dec 31 15:13:23 LL23dec kernel: [  169.772593] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0xfff0, writing 0x80108000)
Dec 31 15:13:23 LL23dec kernel: [  169.772606] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0xf0, writing 0x1010)
Dec 31 15:13:23 LL23dec kernel: [  169.772627] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100104, writing 0x100507)
Dec 31 15:13:23 LL23dec kernel: [  169.772708] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x1fff1, writing 0x80518041)
Dec 31 15:13:23 LL23dec kernel: [  169.772733] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
Dec 31 15:13:23 LL23dec kernel: [  169.772815] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0xf0, writing 0x2020)
Dec 31 15:13:23 LL23dec kernel: [  169.772837] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100106, writing 0x100507)
Dec 31 15:13:23 LL23dec kernel: [  169.772917] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Dec 31 15:13:23 LL23dec kernel: [  169.772966] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Dec 31 15:13:23 LL23dec kernel: [  169.773018] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Dec 31 15:13:23 LL23dec kernel: [  169.773067] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Dec 31 15:13:23 LL23dec kernel: [  169.773125] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
Dec 31 15:13:23 LL23dec kernel: [  169.773411] rt2860 0000:01:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
Dec 31 15:13:23 LL23dec kernel: [  169.773448] rt2860 0000:01:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xfbef0000)
Dec 31 15:13:23 LL23dec kernel: [  169.773461] rt2860 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
Dec 31 15:13:23 LL23dec kernel: [  169.773477] rt2860 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Dec 31 15:13:23 LL23dec kernel: [  169.944356] PM: Device PNP0C0D:00 failed to resume: error 1
Dec 31 15:13:23 LL23dec kernel: [  169.953494] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 31 15:13:23 LL23dec kernel: [  169.953504] i915 0000:00:02.0: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.074205] [drm] LVDS-8: set mode 1024x600 e
Dec 31 15:13:23 LL23dec kernel: [  170.114197] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 31 15:13:23 LL23dec kernel: [  170.114209] HDA Intel 0000:00:1b.0: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.114248] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 31 15:13:23 LL23dec kernel: [  170.114259] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.114289] usb usb2: root hub lost power or was reset
Dec 31 15:13:23 LL23dec kernel: [  170.114315] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 31 15:13:23 LL23dec kernel: [  170.114326] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.114354] usb usb3: root hub lost power or was reset
Dec 31 15:13:23 LL23dec kernel: [  170.114378] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 31 15:13:23 LL23dec kernel: [  170.114388] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.114416] usb usb4: root hub lost power or was reset
Dec 31 15:13:23 LL23dec kernel: [  170.114440] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Dec 31 15:13:23 LL23dec kernel: [  170.114450] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.114477] usb usb5: root hub lost power or was reset
Dec 31 15:13:23 LL23dec kernel: [  170.114522] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 31 15:13:23 LL23dec kernel: [  170.114533] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.114568] pci 0000:00:1e.0: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.114584] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 31 15:13:23 LL23dec kernel: [  170.114593] ata_piix 0000:00:1f.2: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.117094] ATL1E 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 31 15:13:23 LL23dec kernel: [  170.117108] ATL1E 0000:03:00.0: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.125101] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Dec 31 15:13:23 LL23dec kernel: [  170.504474] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
Dec 31 15:13:23 LL23dec kernel: [  170.504484] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
Dec 31 15:13:23 LL23dec kernel: [  170.504869] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
Dec 31 15:13:23 LL23dec kernel: [  170.528978] ata1.00: configured for UDMA/133
Dec 31 15:13:23 LL23dec kernel: [  170.552942] ata1.00: configured for UDMA/133
Dec 31 15:13:23 LL23dec kernel: [  170.552955] ata1: EH complete
Dec 31 15:13:23 LL23dec kernel: [  170.630679] sd 0:0:0:0: [sda] Starting disk
Dec 31 15:13:23 LL23dec kernel: [  170.792084] usb 1-5: reset high speed USB device using ehci_hcd and address 3
Dec 31 15:13:23 LL23dec kernel: [  171.036082] usb 1-8: reset high speed USB device using ehci_hcd and address 5
Dec 31 15:13:23 LL23dec kernel: [  171.332082] usb 5-1: reset full speed USB device using uhci_hcd and address 2
Dec 31 15:13:23 LL23dec kernel: [  172.051138] btusb 5-1:1.0: no reset_resume for driver btusb?
Dec 31 15:13:23 LL23dec kernel: [  172.051149] btusb 5-1:1.1: no reset_resume for driver btusb?
Dec 31 15:13:23 LL23dec kernel: [  172.300850] PM: resume devices took 2.528 seconds
Dec 31 15:13:23 LL23dec kernel: [  172.300914] PM: Finishing wakeup.
Dec 31 15:13:23 LL23dec kernel: [  172.300918] Restarting tasks ... done.
Dec 31 15:13:23 LL23dec kernel: [  172.709855] ATL1E 0000:03:00.0: irq 27 for MSI/MSI-X
Dec 31 15:13:23 LL23dec kernel: [  172.738816] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 31 15:13:23 LL23dec kernel: [  172.754136] RX DESC f2761000  size = 2048
Dec 31 15:13:23 LL23dec kernel: [  172.754587] <-- RTMPAllocTxRxRingMemory, Status=0
Dec 31 15:13:23 LL23dec kernel: [  172.758287] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
Dec 31 15:13:23 LL23dec kernel: [  172.758298] 1. Phy Mode = 0
Dec 31 15:13:23 LL23dec kernel: [  172.758303] 2. Phy Mode = 0
Dec 31 15:13:23 LL23dec kernel: [  172.785156] 3. Phy Mode = 0
Dec 31 15:13:23 LL23dec kernel: [  172.807911] MCS Set = 00 00 00 00 00
``` 
Can anybody test it more? Is it a suspend bug or just the log is updated later from a buffer? System seems to resume normally but I did not checked power conservation.

Thanks in advance,
George

---

