---
title: "Can't format second SATA hardrive"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by flabbergasted on 2010-12-05
I have tried to install a second hard drive in an HP Pavillion m7557c. It has a serial ATA Maxtor 6L300S0 which according to the specs located at [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00711192&tmp_track_link=ot_faqs/top_issues/en_us/c00711192/loc:3&lc=en&dlc=en&cc=us&product=3220013](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00711192&tmp_track_link=ot_faqs/top_issues/en_us/c00711192/loc:3&lc=en&dlc=en&cc=us&product=3220013) is a 7200 rpm hard drive. I believe this is a SATA rather than SATA II or III as this model was first released in June 14th, 2006. I purchased mine about August of that year. The second hard drive I purchased is a Western Digital WD 2001 FASS Caviar Black 2 TB/ 64MB / SATA - 300. 

I am using Ubuntu 10.04 LTS

> ~$ uname -a
Linux workhorse 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64 GNU/Linux

I have plugged the hard drive into one of the SATA channels and it is recognized by the BIOS and Ubuntu 10.04 is seeing it according to dmesg, but I am not able to format it and add it into the system. This is the dmesg entries regarding the ATA channels.

> [    1.122828] ata2.00: ATAPI: LITE-ON DVDRW SHM-165H6S, HP10, max UDMA/66
[    1.122855] ata2.01: ATAPI: TSSTcorpDVD-ROM TS-H352C, HP02, max UDMA/33
[    1.122877] ata2: nv_mode_filter: 0x1f39f&0x739f->0x739f, BIOS=0x7000 (0xc0c0) ACPI=0x701f (60:60:0x1f)
[    1.122881] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c0) ACPI=0x701f (60:60:0x1f)
[    1.136935] usb 1-3: configuration #1 chosen from 1 choice
[    1.137273] hub 1-3:1.0: USB hub found
[    1.137717] hub 1-3:1.0: 2 ports detected
[    1.162780] ata2.00: configured for UDMA/33~$ uname -a
Linux workhorse 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64 GNU/Linux
[    1.202773] ata2.01: configured for UDMA/33
[    1.204308] scsi 1:0:0:0: CD-ROM            LITE-ON  DVDRW SHM-165H6S HP10 PQ: 0 ANSI: 5
[    1.208353] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.208356] Uniform CD-ROM driver Revision: 3.20
[    1.208457] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.208516] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    1.209169] scsi 1:0:1:0: CD-ROM            TSSTcorp DVD-ROM TS-H352C HP02 PQ: 0 ANSI: 5
[    1.211083] sr1: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[    1.211164] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.211258] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    1.361693] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    1.361698]   alloc irq_desc for 19 on node 0
[    1.361700]   alloc kstat_irqs on node 0
[    1.361714] ohci1394 0000:03:05.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    1.380769] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:17:31:c5:bf:15
[    1.380772] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    1.381296] sata_nv 0000:00:0e.0: version 3.5
[    1.381310] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.381313] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.381372] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.381493] scsi2 : sata_nv
[    1.381753] scsi3 : sata_nv
[    1.381984] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf800 irq 23
[    1.381987] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf808 irq 23
[    1.382221] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    1.382223] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    1.382275] sata_nv 0000:00:0f.0: setting latency timer to 64
[    1.382392] scsi4 : sata_nv
[    1.382527] scsi5 : sata_nv
[    1.382747] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xf300 irq 22
[    1.382749] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xf308 irq 22
[    1.418181] Console: switching to colour frame buffer device 80x30
[    1.422089] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[1024]  IR/IT contexts=[8/8]
[    1.670025] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    1.710024] ata5: SATA link down (SStatus 0 SControl 310)
[    1.860034] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    1.880197] ata3.00: ATA-7: Maxtor 6L300S0, BACE1G10, max UDMA/100
[    1.880200] ata3.00: 586072368 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    1.900128] usb 2-2: configuration #1 chosen from 1 choice
[    1.930228] ata3.00: configured for UDMA/100
[    1.930381] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6L300S0   BACE PQ: 0 ANSI: 5
[    1.930387] ata3.00: Disabling SWNCQ mode (depth 1)
[    1.930555] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.930661] sd 2:0:0:0: [sda] 586072368 512-byte logical blocks: (300 GB/279 GiB)
[    1.930703] sd 2:0:0:0: [sda] Write Protect is off
[    1.930706] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.930729] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.930973]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.047580] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.242527] usb 2-4: new low speed USB device using ohci_hcd and address 3
[    2.410045] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    2.471143] usb 2-4: configuration #1 chosen from 1 choice
[    2.487957] usbcore: registered new interface driver hiddev
[    2.494360] input: BTC USB Multimedia Cordless Kit   as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0/input/input3
[    2.494452] generic-usb 0003:03F0:0B0C.0001: input,hidraw0: USB HID v1.00 Keyboard [BTC USB Multimedia Cordless Kit  ] on usb-0000:00:0b.0-4/input0
[    2.508958] input: BTC USB Multimedia Cordless Kit   as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.1/input/input4
[    2.509231] generic-usb 0003:03F0:0B0C.0002: input,hiddev96,hidraw1: USB HID v1.00 Mouse [BTC USB Multimedia Cordless Kit  ] on usb-0000:00:0b.0-4/input1
[    2.509264] usbcore: registered new interface driver usbhid
[    2.509266] usbhid: v2.6:USB HID core driver
[    2.740176] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000b715ba]
[    2.812520] usb 2-8: new full speed USB device using ohci_hcd and address 4
[    3.040122] usb 2-8: configuration #1 chosen from 1 choice
[    3.048795] Initializing USB Mass Storage driver...
[    3.048985] scsi6 : SCSI emulation for USB Mass Storage devices
[    3.049086] usb-storage: device found at 4
[    3.049089] usb-storage: waiting for device to settle before scanning
[    3.049096] usbcore: registered new interface driver usb-storage
[    3.049099] USB Mass Storage support registered.
[    3.122852] usb 1-3.2: new full speed USB device using ehci_hcd and address 6
[    3.232055] usb 1-3.2: configuration #1 chosen from 1 choice
[    7.420173] ata4.00: qc timeout (cmd 0xec)
[    7.420180] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[    8.042091] usb-storage: device scan complete
[    8.049069] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    8.056058] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    8.063056] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    8.070057] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    8.070579] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    8.070702] sd 6:0:0:1: Attached scsi generic sg4 type 0
[    8.070820] sd 6:0:0:2: Attached scsi generic sg5 type 0
[    8.070950] sd 6:0:0:3: Attached scsi generic sg6 type 0
[    8.114057] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    8.125052] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    8.147051] sd 6:0:0:3: [sde] Attached SCSI removable disk
[    8.158056] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[   12.960020] ata4: link is slow to respond, please be patient (ready=0)
[   17.460021] ata4: SRST failed (errno=-16)
[   22.990018] ata4: link is slow to respond, please be patient (ready=0)
[   27.490018] ata4: SRST failed (errno=-16)
[   33.020048] ata4: link is slow to respond, please be patient (ready=0)
[   62.540032] ata4: SRST failed (errno=-16)
[   67.590018] ata4: SRST failed (errno=-16)
[   67.590021] ata4: reset failed, giving up
[   67.590033] ata4: hard resetting link
[   67.590035] ata4: nv: skipping hardreset on occupied port
[   73.120045] ata4: link is slow to respond, please be patient (ready=0)
[   77.620045] ata4: SRST failed (errno=-16)
[   77.620048] ata4: hard resetting link
[   77.620050] ata4: nv: skipping hardreset on occupied port
[   83.150025] ata4: link is slow to respond, please be patient (ready=0)
[   87.650019] ata4: SRST failed (errno=-16)
[   87.650022] ata4: hard resetting link
[   87.650023] ata4: nv: skipping hardreset on occupied port
[   93.180019] ata4: link is slow to respond, please be patient (ready=0)
[  122.700018] ata4: SRST failed (errno=-16)
[  122.700023] ata4: hard resetting link
[  122.700025] ata4: nv: skipping hardreset on occupied port
[  127.750026] ata4: SRST failed (errno=-16)
[  127.750028] ata4: reset failed, giving up
[  127.750032] ata4: EH complete
[  128.080023] ata6: SATA link down (SStatus 0 SControl 310)

The hard drive is supposed to be able to auto negotiate the transfer speed, but this is apparently not happening. According to Western Digital's FAQ at [http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1337&p_created=1112379341&p_sid=JQVdhJgk&p_accessibility=0&p_redirect=&p_srch=1&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NjksNjkmcF9wcm9kcz0yMjcsMjc5JnBfY2F0cz0xMjMmcF9wdj0yLjI3OSZwX2N2PTEuMTIzJnBfcGFnZT0x&p_li=&p_topview=1](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1337&p_created=1112379341&p_sid=JQVdhJgk&p_accessibility=0&p_redirect=&p_srch=1&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NjksNjkmcF9wcm9kcz0yMjcsMjc5JnBfY2F0cz0xMjMmcF9wdj0yLjI3OSZwX2N2PTEuMTIzJnBfcGFnZT0x&p_li=&p_topview=1)

there are six chipsets used on the early SATA controllers that may not be able to auto negotiated transfer rates.

My questions are,

How do I find out what my chipsets are?

Is there a configuration in Ubuntu 10.04 that would enable Ubuntu to work out this issue with the hard drive other than those listed by the manufacturer?

One of the solutions is to put a jumper across pins 5 & 6 locking the transfer speed at 150 MBs when this hard drive is capable of up to 3 GBs. I could also purchase a 3rd party PCI Serial ATA controller which might also solve the problem. I want to make sure there is not another solution before I try one of these.

In case the info might be important, both of the hard drive are being listed as device 0 in bios. I am not able to change it. I am used to the IDE way which lists them as 0 then 1 and so on.

---

### Post by flabbergasted on 2010-12-08
Since nobody has any ideas about this issues, hopefully this information will help.

I booted to the ubuntu 10.10 live cd and dmesg now has more information.

>  ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    4.850354] ata2.00: ATA-8: WDC WD2001FASS-00W2B0, 05.01D05, max UDMA/133
[    4.850357] ata2.00: 3907029168 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    4.870198] ata2.00: model number mismatch 'WDC WD2001FASS-00W2B0' != 'C WD2001FASS-00W2B0                   &#65533;'
[    4.870201] ata2.00: revalidation failed (errno=-19)
[    4.870206] ata2.00: limiting speed to UDMA/133:PIO3


[   10.320038] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   10.340188] ata2.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   10.340191] ata2.00: revalidation failed (errno=-5)
[   10.340194] ata2.00: disabled


This does not make sense to me, but apparently ubuntu thinks the model numbers do not match. Is there possibly a boot param I could use to get this hard drive to be recognised by ubuntu to get it formatted?

Any hints are greatly appreciated.

---

### Post by oldfred on 2010-12-08
No idea.

But I would experiment with unplugging one or the other of your CD/DVD drives to see if that makes a difference. Are they SATA or PATA?

Can you boot from USB? If so I might unplug both and see it that makes a difference. 

Is BIOS up to date?

IF you unplug all the other drives does it work standalone? 

I have copied a bunch of comments on BIOS settings, do any seem to apply?
BIOS should be set for IDE compatibility mode
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility 
So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive."
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
Old BIOS, new drive 137GB max boot size

---

### Post by flabbergasted on 2010-12-08
oldfred,

The bios settings are very limited. It is the phoenix bios that came with the hp, but according to their site, any bios upgrades would come from the manufacturer. Phoenix, who merged with Award custom builds bios for computer manufactures, and looking at hp downloads page for my model, there are no bios upgrades available. I read some of those comments on another post before and it seems that some people have more options in their bios than I do. I will check again for some of the ideas you have including unplugging the two optical drives. They are not sata as far as I know, but I will confirm.

Thanks for the tips.

---

### Post by flabbergasted on 2010-12-08
Ubuntu boots up just fine on the first hard drive. It just doesn't see the second one so I can't format it using gparted. 

The optical drives are PATA.

I unplugged the first hard drive and booted to the ubuntu live cd. Starting gparted results in no devices detected. Is the problem maybe ubuntu is not yet capable of utilizing newer SATA hard drives of this size?

---

### Post by oldfred on 2010-12-08
We have seen 2GB drives used without major issues. Often gpt instead of MBR (msdos) works better if not a windows environment.

Did the drive have partitions? This has a fix if that is the case.

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by flabbergasted on 2010-12-09
It was supposed to be unformatted. I do not remember where I read about the hard drive before I chose it, but I did read that it would require formatting regardless of what operating system was being used.

I presume you meant 2TB in your previous post?

---

### Post by oldfred on 2010-12-10
Yes 2TB. Some have had grub boot issues with larger drives over 500GB and only one root partition. But many have had 1 or 2TB drives in either MBR or GPT (fewer) work without major issues related to drive size.

I also see you had a multi card reader attached. I would unplug every thing you can but the one new 2TB drive and one CD and see if that works.

Edit:

I also found this but the only solution seemed to be plug into a different port that used a different hardware driver.
[http://www.mail-archive.com/linux-ide@vger.kernel.org/msg11274.html](http://www.mail-archive.com/linux-ide@vger.kernel.org/msg11274.html)

---

### Post by flabbergasted on 2010-12-18
I haven't forgotten about my thread. I developed another issue I am trying to resolve that is preventing me from working on this one. Now I can't see anything on my monitor, not even bios. I'll get back to this when I can see what I am doing.

---

