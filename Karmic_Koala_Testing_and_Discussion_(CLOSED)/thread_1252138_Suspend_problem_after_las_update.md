---
title: "Suspend problem after las update"
date: 2009-08-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by neferty on 2009-08-28
I have suspend problems since the last update(s) in the last few days:

My laptop (Sony Vaio VGN-SRXXX) won't resume after going into suspension mode. The screen appears frozen, even the mouse doesn't appear to move.
Switching to tty1 doesn't work either. Have to brute-restart every time.

Has anybody had similar problem??

---

### Post by bapoumba on 2009-08-28
Suspend works okay here.

---

### Post by raronson on 2009-08-28
I've had similar issues historically on my Macbook, but after updates from the other day, I haven't been frozen up or sluggish after a resume--to my pleasant surprise.  I usually anticipate rebooting every 2nd or 3rd time I open the lid.  Not sure what fixed it, or if it's going to last, but I'm appreciating it for now.

---

### Post by neferty on 2009-08-29
Hmm.. fact is that the problem is still there and the laptop freezes everytime i resume after suspension. :(

---

### Post by taavikko on 2009-08-29
> **neferty said:**
> Hmm.. fact is that the problem is still there and the laptop freezes everytime i resume after suspension. :(

I know the next page is a bit confusing, but please read it carefully
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

---

### Post by warreno on 2009-08-29
> **neferty said:**
> Hmm.. fact is that the problem is still there and the laptop freezes everytime i resume after suspension. :(

I've had sporadic suspend/resume problems on my Acer netbook as well. If you've got an SD card plugged into your machine, try unmounting (and possibly removing) it before you suspend. That seems to have fixed it for me.

I was able to make the suspend failure 100% consistent, by the way, by setting the filesystem on the SD card to ext3. Leaving it inserted and mounted, then suspending the netbook, *always* led to the problem you're describing here.

---

### Post by camper365 on 2009-08-31
Since I started running Karmic, I have never been able to suspend on a Thinkpad T43.
However, it hasn't bothered me too much until now.

I think this has to do with the deprecation of HAL and that means a lot of hardware problems are going to exist.

---

### Post by jmmL on 2009-08-31
I've had suspend problems on my laptop ever since upgrading to karmic. After resuming I see 100% usage on one core by ksoftirqd/0. It doesn't make the laptop unusable (I have another core that gets by), but it does raise the temperature dramatically and also severely reduces the battery life.

Here's the first two lines from top:
```
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
    4 root      15  -5     0    0    0 R   100  0.0   0:19.84 ksoftirqd/0
```

---

### Post by neferty on 2009-09-03
I don't think it's a kernel problem in my case since I switched to the kernel that used to work (31-6) and the screen still crashes after suspension. Might be related to the latest intel graphic driver update...

---

### Post by neferty on 2009-09-03
> **taavikko said:**
> I know the next page is a bit confusing, but please read it carefully
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)


Taavikko, I managed to follow the instructions and got this dmesg (extract of the relevant part):
```

[    1.150925] Using IPI No-Shortcut mode
[    1.151155] PM: Resume from disk failed.
[    1.151169] registered taskstats version 1
[    1.151312]   Magic number: 0:291:379
[    1.151315]   hash matches /build/buildd/linux-2.6.31/drivers/base/power/main.c:419
[    1.151396] rtc_cmos 00:06: setting system clock to 2064-01-03 12:22:59 UTC (2966588579)
[    1.151400] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.151402] EDD information not available.
[    1.170181] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.420963] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.421538] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    1.421545] ata1.00: ATA-8: FUJITSU MHY2250BH, 0000000B, max UDMA/100
[    1.421549] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.422284] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    1.422315] ata1.00: configured for UDMA/100
[    1.436230] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHY2250B 0000 PQ: 0 ANSI: 5
[    1.436565] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.436621] sd 0:0:0:0: [sda] Write Protect is off
[    1.436625] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.436633] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.436671] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.436819]  sda: sda1 sda2 sda3 sda4
[    1.466760] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.476613] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.504026] Clocksource tsc unstable (delta = -218476071 ns)
[    1.611637] usb 1-2: configuration #1 chosen from 1 choice
[    2.128076] usb 7-1: new full speed USB device using uhci_hcd and address 2
[    2.160070] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.160716] ata2.00: ATAPI: Optiarc  DVD RW AD-7910S, 1.70, max UDMA/100
[    2.161827] ata2.00: configured for UDMA/100
[    2.177647] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7910S  1.70 PQ: 0 ANSI: 5
[    2.187284] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.187288] Uniform CD-ROM driver Revision: 3.20
[    2.187492] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.187659] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.187756] Freeing unused kernel memory: 536k freed
[    2.188108] Write protecting the kernel text: 4536k
[    2.188175] Write protecting the kernel read-only data: 1824k
[    2.287027] Linux agpgart interface v0.103
[    2.290216] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    2.291428] agpgart-intel 0000:00:00.0: detected 131068K stolen memory
[    2.294334] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    2.319193] usb 7-1: configuration #1 chosen from 1 choice
[    2.319330] [drm] Initialized drm 1.1.0 20060810
[    2.332305] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.332311] i915 0000:00:02.0: setting latency timer to 64
[    2.335220]   alloc irq_desc for 29 on node -1
[    2.335224]   alloc kstat_irqs on node -1
[    2.335233] i915 0000:00:02.0: irq 29 for MSI/MSI-X
[    2.340450] i2c-adapter i2c-1: unable to read EDID block.
[    2.340454] i915 0000:00:02.0: LVDS-1: no EDID data
[    2.340682] [drm:intel_dp_i2c_init] *ERROR* i2c_init DPDDC-D
[    2.364436] i2c-adapter i2c-1: unable to read EDID block.
[    2.364439] i915 0000:00:02.0: LVDS-1: no EDID data
[    2.373082] [drm] fb0: inteldrmfb frame buffer device
[    2.380558] acpi device:18: registered as cooling_device2
[    2.380945] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:16/input/input4
[    2.381010] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.381067] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.692367] [drm] LVDS-8: set mode 1280x800 f
[    3.216280] Console: switching to colour frame buffer device 160x50
[    3.432698] sky2 driver version 1.23
[    3.432810] sky2 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.432863] sky2 0000:01:00.0: setting latency timer to 64
[    3.432943] sky2 0000:01:00.0: Yukon-2 FE+ chip revision 0
[    3.433459]   alloc irq_desc for 30 on node -1
[    3.433462]   alloc kstat_irqs on node -1
[    3.433540] sky2 0000:01:00.0: irq 30 for MSI/MSI-X
[    3.434580] sky2 eth0: addr 00:1a:80:4b:47:d2
[    3.486799] ohci1394 0000:06:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.542543] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[d5500000-d55007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.816518] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460302bedc0c]
[   12.010722] PM: Starting manual resume from disk
[   12.010726] PM: Resume from partition 252:0
[   12.010728] PM: Checking hibernation image.
[   12.011005] PM: Resume from disk failed.
[   12.014836] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
[   12.014841] EXT4-fs (sda2): write access will be enabled during recovery
[   12.052740] EXT4-fs (sda2): barriers enabled
[   14.070472] kjournald2 starting: pid 1211, dev sda2:8, commit interval 5 seconds
[   14.070502] EXT4-fs (sda2): delayed allocation enabled
[   14.070507] EXT4-fs: file extents enabled
[   14.070607] EXT4-fs: mballoc enabled
[   14.070624] EXT4-fs (sda2): orphan cleanup on readonly fs
[   14.070632] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 1179659
[   14.070664] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 1179658
[   14.070675] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 1179657
[   14.070686] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 1179655
[   14.070751] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 1179653
[   14.070761] EXT4-fs (sda2): 5 orphan inodes deleted
[   14.070765] EXT4-fs (sda2): recovery complete
[   14.477236] EXT4-fs (sda2): mounted filesystem with ordered data mode

``` 

However, apart of the "PM: Resume from disk failed." message I cannot find any data that would be helpful to determine the source of this error...

---

### Post by jithin1987 on 2009-09-03
Same problem here in kubuntu. Already reported a bug

[https://bugs.launchpad.net/bugs/422669](https://bugs.launchpad.net/bugs/422669)

---

### Post by neferty on 2009-09-04
An interesting thing. If I switch to TTY1 and run a manual
```
sudo pm-suspend
```
I am able to reinitiate in TTY1 after suspension (even though it spits a few errors). However if I switch back to gdm (ctrl+alt+f7) evertthing gets frozen.

On the other hand. If I suspend/proceed through TTY1 as described above and then restart the gdm with
```
sudo /etc/init.d/gdm stop; sudo /etc/init.d/gdm start;
``` it works OK. But you have to re-login afterwards and everything you had open in your lasst session is gone (clearly, not what suspension is meant to be :P).

So, the problem lies somewhere in gdm... right?

---

### Post by neferty on 2009-09-05
hmm. turning the compiz off fixed the problem. No graphics, but at least I can suspend again

---

### Post by Bakon Jarser on 2009-10-25
> **warreno said:**
> I've had sporadic suspend/resume problems on my Acer netbook as well. If you've got an SD card plugged into your machine, try unmounting (and possibly removing) it before you suspend. That seems to have fixed it for me.

I was able to make the suspend failure 100% consistent, by the way, by setting the filesystem on the SD card to ext3. Leaving it inserted and mounted, then suspending the netbook, *always* led to the problem you're describing here.

I can confirm this on my Acer Aspire 6920.  Unmounting the sd card fixed my suspend problems.  Is there a  bug report filed for this?

EDIT:  Yes there is a bug report.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/449626](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/449626)

---

