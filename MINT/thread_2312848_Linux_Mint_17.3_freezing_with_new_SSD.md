---
title: "Linux Mint 17.3 freezing with new SSD"
date: 2016-02-07
forum: MINT
---

### Post by rock.rockwellgmai on 2016-02-07
Installed fresh copy of Linux Mint 17.3  on new Samsung SSD 850 EVO. 
Mostly works but quite unstable, strange freezes. Resizing a Chrome window freezes things pretty reliably.
Saw lots of notes on AHCI and IDE modes but my BIOS does not have a setting like this.

Motherboard is ASUS M2N68/AM-SE2, 2 SATA ports that claim to be SATA2.
Board also has an PATA interface but this behavior persists even with no other stuff connected and IDE disables in BIOS
Latest available BIOS, 
Cool and Quiet is enabled.
 Athlon 64 x2 CPU 

Noticed this from dmesg... the configured for UDMA/133 seems messed up to me....
also no mention of AHCI in dmesg
--------------------------------------------------------------------------------------------------------------------------
[    1.992043] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.000203] ata1.00: supports DRM functions and may not be fully accessible
[    2.000206] ata1.00: ATA-9: Samsung SSD 850 EVO 250GB, EMT02B6Q, max UDMA/133
[    2.000208] ata1.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    2.008186] ata1.00: supports DRM functions and may not be fully accessible
[    2.008592] ata1.00: configured for UDMA/133
[    2.008760] scsi 0:0:0:0: Direct-Access     ATA      Samsung SSD 850  2B6Q PQ: 0 ANSI: 5
[    2.009079] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.009107] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.009189] sd 0:0:0:0: [sda] Write Protect is off
[    2.009191] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.009214] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.009955]  sda: sda1 sda2 < sda5 >
[    2.010431] sd 0:0:0:0: [sda] Attached SCSI disk

-----------------------------------------------------------------------------------------------
I see from forums that Samsung drives have been problematic but the notes I read said that Linux hasd been fixed and this
is latest Samsung v-nand tech so I expected it to work....should I give up on this drive/motherboard combo?
Suggestions welcome.

---

### Post by weatherman2 on 2016-02-07
Did you have a regular had drive running reliably before in this same motherboard?

If not, then I would try to troubleshoot other possible hardware problems besides the SSD.

---

### Post by howefield on 2016-02-07
Thread moved to the "*MINT*" sub forum.

---

### Post by Dennis N on 2016-02-07
I have the same SSD, and never had any problems. 

Here are similar lines here from systemd journal:

```
Feb 07 06:49:36 Zotac kernel: ata1.00: ATA-9: Samsung SSD 850 EVO 250GB, EMT01B6Q, max UDMA/133
Feb 07 06:49:36 Zotac kernel: ata1.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
Feb 07 06:49:36 Zotac kernel: ata1.00: supports DRM functions and may not be fully accessible
Feb 07 06:49:36 Zotac kernel: ata1.00: configured for UDMA/133

```

As to AHCI, there is this:

```
Feb 07 06:49:35 Zotac kernel: ahci 0000:00:1f.2: version 3.0
Feb 07 06:49:35 Zotac kernel: ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
Feb 07 06:49:35 Zotac kernel: ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x11 impl SATA mode
Feb 07 06:49:36 Zotac kernel: ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems sxs apst

```

---

### Post by rock.rockwellgmai on 2016-02-07
I had been running Lubutu 14.04 previously on a hard drive with no problems. 
I am pretty sure that the Chrome freezing issue has to do with video drivers, hardware acceleration on this particular hardware (Nvidia GEforce 7025)
With Linux Mint 17.3 Cinnamon desktop, and the Nouveau drivers , Chrome would freeze reliably, trying to resize its window.
With Cinnamon and the reccomended nvidia 304 drivers,  Cinnamon would crash as soon as mouse was moved and the failsafe desktop would come up.
With Linux Mint 17.3 Mate desktop, neither driver set showed any instability but the chrome issue was still there. When I googled that I found that others had seen it.
Starting Chrome with "-disable-gpu" switch seemed to eliminate the more solid freezing symptom.

Going back to Linux Mint 17.3 Cinnamon desktop /Nouveau drivers  now and see if all is well using the Chrome workaround.
I saw a PCIe 1x SATA controller that supports the SATA3 6gbs SSD drive for 30 bucks, think it would make much difference?
Should I be seeing ahci text in  the dmesg output?

---

