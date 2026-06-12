---
title: "how to install INTEX TV tuner card"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by ukmad on 2010-01-31
How do i install a intex TV tuner card 
I am very new to ubuntu and only know to use a little of it. 
I have a intex tv tuner card with FM. 
how do i add this as my hardware 
i wa earlier using windows XP and i also have drivers for XP and inter video Win DVR application for viewing TV on XP.

But on ubuntu how do i see TV and how do i install the card.
please help.

---

### Post by oupamster on 2010-01-31
no idea but have a look at this;

[http://ubuntuforums.org/showthread.php?t=626780](http://ubuntuforums.org/showthread.php?t=626780)

it might help.

---

### Post by ukmad on 2010-02-18
01:01.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)
	Subsystem: Philips Semiconductors Device [1131:0000]
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at f0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [40] Power Management version 1
	Kernel driver in use: saa7134
	Kernel modules: saa7134

---

### Post by Jose Catre-Vandis on 2010-02-18
Output from **dmesg** in terminal please

---

### Post by ukmad on 2010-02-18
DMSEG ----
[    1.048235] ata2.00: configured for UDMA/33
[    1.072208] ata1.00: HPA unlocked: 976771055 -> 976773168, native 976773168
[    1.072215] ata1.00: ATA-8: ST3500418AS, CC38, max UDMA/133
[    1.072218] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.088440] ata1.00: configured for UDMA/133
[    1.088589] scsi 0:0:0:0: Direct-Access     ATA      ST3500418AS      CC38 PQ: 0 ANSI: 5
[    1.088755] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.088807] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.088879] sd 0:0:0:0: [sda] Write Protect is off
[    1.088883] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.088918] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.089101]  sda:
[    1.092905] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10A  JL02 PQ: 0 ANSI: 5
[    1.105379] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.105384] Uniform CD-ROM driver Revision: 3.20
[    1.105496] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.105553] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.108777]  sda1 sda2 < sda5 >
[    1.135060] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.135084] Freeing unused kernel memory: 540k freed
[    1.135676] Write protecting the kernel text: 4568k
[    1.135734] Write protecting the kernel read-only data: 1836k
[    1.364653] Linux agpgart interface v0.103
[    1.371198] agpgart-intel 0000:00:00.0: Intel 915G Chipset
[    1.371713] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.409210] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.409276] 8139cp 0000:01:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.449632] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.449819] 8139too Fast Ethernet driver 0.9.28
[    1.449896]   alloc irq_desc for 21 on node -1
[    1.449904]   alloc kstat_irqs on node -1
[    1.449917] 8139too 0000:01:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.451914] eth0: RealTek RTL8139 at 0xa000, 00:14:85:e2:49:89, IRQ 21
[    1.455835] Floppy drive(s): fd0 is 1.44M
[    1.472801] FDC 0 is a post-1991 82077
[    1.504687] [drm] Initialized drm 1.1.0 20060810
[    1.519126] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.519137] i915 0000:00:02.0: setting latency timer to 64
[    1.635548] [drm] fb0: inteldrmfb frame buffer device
[    1.635561] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.698235] render error detected, EIR: 0x00000010
[    1.698240] page table error
[    1.698242]   PGTBL_ER: 0x00000010
[    1.698247] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[    1.698256] render error detected, EIR: 0x00000010
[    1.698258] page table error
[    1.698260]   PGTBL_ER: 0x00000010
[    1.704459] [drm] DAC-6: set mode 1024x768 15
[    1.727483] Console: switching to colour frame buffer device 128x48
[    2.093250] PM: Starting manual resume from disk
[    2.093256] PM: Resume from partition 8:5
[    2.093258] PM: Checking hibernation image.
[    2.093476] PM: Resume from disk failed.
[    2.129606] EXT4-fs (sda1): barriers enabled
[    2.147313] kjournald2 starting: pid 371, dev sda1:8, commit interval 5 seconds
[    2.147329] EXT4-fs (sda1): delayed allocation enabled
[    2.147334] EXT4-fs: file extents enabled
[    2.216392] EXT4-fs: mballoc enabled
[    2.216413] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.687094] type=1505 audit(1266478632.287:2): operation="profile_load" pid=394 name=/usr/share/gdm/guest-session/Xsession
[    2.690772] type=1505 audit(1266478632.291:3): operation="profile_load" pid=395 name=/sbin/dhclient3
[    2.691496] type=1505 audit(1266478632.291:4): operation="profile_load" pid=395 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    2.691892] type=1505 audit(1266478632.291:5): operation="profile_load" pid=395 name=/usr/lib/connman/scripts/dhclient-script
[    2.714279] type=1505 audit(1266478632.315:6): operation="profile_load" pid=396 name=/usr/bin/evince
[    2.725665] type=1505 audit(1266478632.327:7): operation="profile_load" pid=396 name=/usr/bin/evince-previewer
[    2.732400] type=1505 audit(1266478632.335:8): operation="profile_load" pid=396 name=/usr/bin/evince-thumbnailer
[    2.756372] type=1505 audit(1266478632.359:9): operation="profile_load" pid=398 name=/usr/lib/cups/backend/cups-pdf
[    2.757216] type=1505 audit(1266478632.359:10): operation="profile_load" pid=398 name=/usr/sbin/cupsd
[    3.652655] Adding 4498160k swap on /dev/sda5.  Priority:-1 extents:1 across:4498160k 
[    3.780807] udev: starting version 147
[    3.861990] EXT4-fs (sda1): internal journal on sda1:8
[    7.256329] __ratelimit: 9 callbacks suppressed
[    7.256337] type=1505 audit(1266478636.859:14): operation="profile_replace" pid=817 name=/usr/share/gdm/guest-session/Xsession
[    7.258878] type=1505 audit(1266478636.859:15): operation="profile_replace" pid=818 name=/sbin/dhclient3
[    7.259708] type=1505 audit(1266478636.859:16): operation="profile_replace" pid=818 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.260136] type=1505 audit(1266478636.863:17): operation="profile_replace" pid=818 name=/usr/lib/connman/scripts/dhclient-script
[    7.266418] type=1505 audit(1266478636.867:18): operation="profile_replace" pid=819 name=/usr/bin/evince
[    7.277867] type=1505 audit(1266478636.879:19): operation="profile_replace" pid=819 name=/usr/bin/evince-previewer
[    7.284764] type=1505 audit(1266478636.887:20): operation="profile_replace" pid=819 name=/usr/bin/evince-thumbnailer
[    7.295344] type=1505 audit(1266478636.895:21): operation="profile_replace" pid=821 name=/usr/lib/cups/backend/cups-pdf
[    7.296218] type=1505 audit(1266478636.899:22): operation="profile_replace" pid=821 name=/usr/sbin/cupsd
[    7.299507] type=1505 audit(1266478636.899:23): operation="profile_replace" pid=822 name=/usr/sbin/mysqld
[    8.399972] ip_tables: (C) 2000-2006 Netfilter Core Team
[    9.575680] intel_rng: FWH not detected
[    9.846776] lp: driver loaded but no devices found
[   10.082024] parport_pc 00:09: reported by Plug and Play ACPI
[   10.082074] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   10.176260] lp0: using parport0 (interrupt-driven).
[   10.427847] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   10.670513]   alloc irq_desc for 17 on node -1
[   10.670520]   alloc kstat_irqs on node -1
[   10.670532] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.670596] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   10.678168] ppdev: user-space parallel port driver
[   10.687547] Linux video capture interface: v2.00
[   10.878871] psmouse serio1: ID: 10 00 64
[   10.997036] intel8x0_measure_ac97_clock: measured 54706 usecs (2636 samples)
[   10.997041] intel8x0: clocking to 48000
[   11.412106] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   12.191677] saa7130/34: v4l2 driver version 0.2.15 loaded
[   12.191755]   alloc irq_desc for 20 on node -1
[   12.191760]   alloc kstat_irqs on node -1
[   12.191772] saa7134 0000:01:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   12.191783] saa7130[0]: found at 0000:01:01.0, rev: 1, irq: 20, latency: 32, mmio: 0xf0000000
[   12.191793] saa7134: <rant>
[   12.191794] saa7134:  Congratulations!  Your TV card vendor saved a few
[   12.191796] saa7134:  cents for a eeprom, thus your pci board has no
[   12.191799] saa7134:  subsystem ID and I can't identify it automatically
[   12.191801] saa7134: </rant>
[   12.191802] saa7134: I feel better now.  Ok, here are the good news:
[   12.191804] saa7134: You can use the card=<nr> insmod option to specify
[   12.191806] saa7134: which board do you have.  The list:
[   12.191813] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   12.191821] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   12.191831] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   12.191840] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   12.191848] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   12.191855] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   12.191863] saa7134:   card=6 -> Tevion MD 9717                          
[   12.191869] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   12.191878] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   12.191885] saa7134:   card=9 -> Medion 5044                             
[   12.191891] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   12.191897] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   12.191904] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[   12.191913] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   12.191918] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   12.191926] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   12.191933] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   12.191943] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   12.191951] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   12.191956] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   12.191964] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   12.191971] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   12.191979] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   12.191986] saa7134:   card=23 -> BMK MPEX Tuner                          
[   12.191993] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   12.192037] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   12.192044] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   12.192053] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[   12.192060] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[   12.192066] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   12.192075] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   12.192082] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   12.192090] saa7134:   card=32 -> AVACS SmartTV                           
[   12.192096] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   12.192103] saa7134:   card=34 -> Noval Prime TV 7133                     
[   12.192109] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   12.192116] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   12.192124] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   12.192129] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   12.192136] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   12.192148] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   12.192156] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   12.192163] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   12.192170] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   12.192176] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   12.192182] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   12.192190] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   12.192198] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   12.192205] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   12.192213] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   12.192220] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   12.192227] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   12.192235] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   12.192242] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   12.192249] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   12.192261] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   12.192270] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   12.192277] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   12.192284] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   12.192296] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   12.192303] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   12.192314] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   12.192322] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   12.192328] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   12.192334] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   12.192343] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   12.192348] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   12.192355] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   12.192363] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   12.192370] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   12.192377] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   12.192384] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   12.192391] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   12.192399] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   12.192407] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   12.192415] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   12.192424] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   12.192431] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   12.192439] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[   12.192446] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   12.192452] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   12.192459] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   12.192466] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   12.192474] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   12.192481] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   12.192488] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   12.192498] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   12.192507] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   12.192514] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   12.192521] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   12.192529] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   12.192538] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   12.192545] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   12.192553] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   12.192560] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   12.192572] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   12.192580] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   12.192590] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   12.192599] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   12.192606] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   12.192613] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   12.192620] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   12.192627] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   12.192636] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   12.192643] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   12.192659] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   12.192666] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   12.192677] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   12.192684] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   12.192692] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   12.192697] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   12.192704] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   12.192712] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   12.192720] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   12.192727] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   12.192734] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   12.192742] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   12.192749] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   12.192757] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   12.192765] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   12.192773] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   12.192781] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   12.192788] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   12.192795] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   12.192803] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   12.192811] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   12.192818] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[   12.192825] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[   12.192834] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[   12.192842] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[   12.192849] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   12.192857] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   12.192864] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[   12.192870] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[   12.192876] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   12.192883] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   12.192891] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   12.192898] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   12.192905] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   12.192913] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   12.192921] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   12.192928] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   12.192936] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   12.192943] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   12.192950] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   12.192958] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[   12.192968] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[   12.192973] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[   12.192982] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[   12.192991] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[   12.192998] saa7134:   card=150 -> Zogis Real Angel 220                    
[   12.193004] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[   12.193012] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[   12.193020] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[   12.193028] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[   12.193036] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[   12.193045] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[   12.193056] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[   12.193063] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[   12.193071] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[   12.193078] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[   12.193086] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[   12.193093] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[   12.193101] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[   12.193108] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[   12.193115] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[   12.193123] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[   12.193131] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[   12.193138] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[   12.193147] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   12.193166] saa7130[0]: board init: gpio is 38500
[   12.193175] IRQ 20/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   12.296302] saa7130[0]: Huh, no eeprom present (err=-5)?
[   12.296311] i2c-adapter i2c-1: Invalid 7-bit address 0x7a
[   12.297005] saa7130[0]: registered device video0 [v4l2]
[   12.297055] saa7130[0]: registered device vbi0
[   12.612414] saa7134 ALSA driver for DMA sound loaded
[   12.612421] saa7130[0]/alsa: UNKNOWN/GENERIC doesn't support digital audio
[   12.840755] __ratelimit: 9 callbacks suppressed
[   12.840762] type=1503 audit(1266478642.443:27): operation="open" pid=1118 parent=1117 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   13.161944] type=1503 audit(1266478642.763:28): operation="open" pid=1236 parent=1125 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   13.932413] type=1503 audit(1266478643.535:29): operation="open" pid=1247 parent=1246 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   14.953090] type=1503 audit(1266478644.555:30): operation="open" pid=1258 parent=1257 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   16.105917] type=1503 audit(1266478645.708:31): operation="open" pid=1275 parent=1274 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   16.299779] type=1503 audit(1266478645.899:32): operation="open" pid=1286 parent=1285 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   20.734917] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.734923] vboxdrv: Successfully done.
[   20.734927] vboxdrv: Found 2 processor cores.
[   20.735043] vboxdrv: fAsync=0 offMin=0x439 offMax=0x11e1
[   20.735120] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.735126] vboxdrv: Successfully loaded version 3.1.2 (interface 0x00100001).
[   20.912035] eth0: no IPv6 routers present
[   22.916675] CPU0 attaching NULL sched-domain.
[   22.916682] CPU1 attaching NULL sched-domain.
[   22.929106] CPU0 attaching sched-domain:
[   22.929112]  domain 0: span 0-1 level SIBLING
[   22.929116]   groups: 0 1
[   22.929122]   domain 1: span 0-1 level MC
[   22.929126]    groups: 0-1 (__cpu_power = 2048)
[   22.929133] CPU1 attaching sched-domain:
[   22.929136]  domain 0: span 0-1 level SIBLING
[   22.929140]   groups: 1 0
[   22.929145]   domain 1: span 0-1 level MC
[   22.929148]    groups: 0-1 (__cpu_power = 2048)
[   23.682075] CPU0 attaching NULL sched-domain.
[   23.682083] CPU1 attaching NULL sched-domain.
[   23.696112] CPU0 attaching sched-domain:
[   23.696118]  domain 0: span 0-1 level SIBLING
[   23.696122]   groups: 0 1
[   23.696130] CPU1 attaching sched-domain:
[   23.696133]  domain 0: span 0-1 level SIBLING
[   23.696137]   groups: 1 0

---

### Post by Jose Catre-Vandis on 2010-02-18
You should find your answer here:

[http://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux](http://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux)

---

### Post by ukmad on 2010-02-20
hi still not able to crack it 
can u just intrpret that for me the last link on google sites 
i am very new to ubuntu

---

### Post by Jose Catre-Vandis on 2010-02-20
OK, in simple terms, we know you have a Philips SAA7130 tv adapter.What we don't know is what card or tuner is on the adapter. So we have to try to find out if the drivers have already be included in the kernel, either by googling or by trial and error.

From googling your infoit might be that card 3 and tuner 14 will work. This is what you need to do:

Open a terminal and type the following:
```
sudo rmmod saa7134 && sudo modprobe saa7134 card=3 tuner=14
```
then run dmesg again and see if it looks any different. If successful you shouldn't get the big long list of cards. in the meantime I'll keep searching

Also found this post on the forum, check your card info against this one
[http://ubuntuforums.org/showthread.php?t=626780](http://ubuntuforums.org/showthread.php?t=626780)

---

### Post by ukmad on 2010-02-20
Sorry but the dmesg gives the same result all card as per my previous post.
dont really understand what is wrong.  

in the link that u sent me 
[http://ubuntuforums.org/showthread.php?t=626780](http://ubuntuforums.org/showthread.php?t=626780)
"In saa7134-cards.c, I noticed that card 3 (4th array element) was SAA7134_BOARD_FLYVIDEO2000. The array entry was the following:"
how and where can i interchange these vaules as he had done.

---

### Post by ukmad on 2010-02-21
still same message on dmesg 

In saa7134-cards.c, I noticed that card 3 (4th array element) was SAA7134_BOARD_FLYVIDEO2000. The array entry was the following:
this was in that link you gave:
but how and where do i go and change this

---

### Post by ukmad on 2010-02-21
current -- dmesg report------

 9.841574] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[    9.841579] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[    9.841584] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[    9.841616] saa7130[0]: board init: gpio is 38500
[    9.841623] IRQ 20/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.859098] intel_rng: FWH not detected
[    9.870226] parport_pc 00:09: reported by Plug and Play ACPI
[    9.870279] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    9.879777] lp: driver loaded but no devices found
[    9.890113] ppdev: user-space parallel port driver
**[COLOR="Red"][    9.948599] saa7130[0]: Huh, no eeprom present (err=-5)?[/COLOR]**
[    9.948606] i2c-adapter i2c-1: Invalid 7-bit address 0x7a
[    9.949222] saa7130[0]: registered device video0 [v4l2]
[    9.949290] saa7130[0]: registered device vbi0
[    9.953354] lp0: using parport0 (interrupt-driven).
[    9.962036] saa7134 ALSA driver for DMA sound loaded
[    9.962045] saa7130[0]/alsa: UNKNOWN/GENERIC doesn't support digital audio
[   10.077333] psmouse serio1: ID: 10 00 64
[   10.610601] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   11.969198] __ratelimit: 6 callbacks suppressed
[   11.969205] type=1503 audit(1266729622.572:26): operation="open" pid=992 parent=991 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   12.662692]   alloc irq_desc for 17 on node -1
[   12.662699]   alloc kstat_irqs on node -1
[   12.662713] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.662779] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   12.715503] type=1503 audit(1266729623.315:27): operation="open" pid=1063 parent=1062 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   12.963726] type=1503 audit(1266729623.564:28): operation="open" pid=1180 parent=1071 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   12.985049] intel8x0_measure_ac97_clock: measured 54594 usecs (2631 samples)
[   12.985054] intel8x0: clocking to 48000
[   13.308675] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   13.800329] type=1503 audit(1266729624.400:29): operation="open" pid=1215 parent=1214 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   14.820549] type=1503 audit(1266729625.423:30): operation="open" pid=1236 parent=1235 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   16.104365] type=1503 audit(1266729626.707:31): operation="open" pid=1253 parent=1252 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   16.199052] type=1503 audit(1266729626.799:32): operation="open" pid=1264 parent=1263 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   20.529933] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.529938] vboxdrv: Successfully done.
[   20.529941] vboxdrv: Found 2 processor cores.
[   20.530055] vboxdrv: fAsync=0 offMin=0x47e offMax=0x3afc
[   20.530120] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.530123] vboxdrv: Successfully loaded version 3.1.2 (interface 0x00100001).
[   23.504025] eth0: no IPv6 routers present
[   23.727927] CPU0 attaching NULL sched-domain.
[   23.727935] CPU1 attaching NULL sched-domain.
[   23.741109] CPU0 attaching sched-domain:
[   23.741116]  domain 0: span 0-1 level SIBLING
[   23.741120]   groups: 0 1
[   23.741126]   domain 1: span 0-1 level MC
[   23.741129]    groups: 0-1 (__cpu_power = 2048)
[   23.741138] CPU1 attaching sched-domain:
[   23.741140]  domain 0: span 0-1 level SIBLING
[   23.741144]   groups: 1 0
[   23.741149]   domain 1: span 0-1 level MC
[   23.741152]    groups: 0-1 (__cpu_power = 2048)
[   24.273139] CPU0 attaching NULL sched-domain.
[   24.273146] CPU1 attaching NULL sched-domain.
[   24.288119] CPU0 attaching sched-domain:
[   24.288125]  domain 0: span 0-1 level SIBLING
[   24.288129]   groups: 0 1
[   24.288137] CPU1 attaching sched-domain:
[   24.288140]  domain 0: span 0-1 level SIBLING
[   24.288144]   groups: 1 0

---

### Post by ukmad on 2010-02-21
i some how got it working thanks for your help

---

### Post by Jose Catre-Vandis on 2010-02-21
Do you know what you did?

---

### Post by ukmad on 2010-02-24
still not working

---

### Post by ukmad on 2010-02-24
the problem is it works 
sudo modprobe saa7134 card=3 tuner=55 
channel secam
frequency table Europe

this card and tuner works
but when i restart my pc settings are gone 
and if i straight away tyoe the above code it never starts in one go.

I have to keep on trying and then i succeed some time later.
Can u help in this 
 
can those settings be saved permanently.here is the dmesg for you while i am watching the TV time 

















































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































[    0.250751] pci 0000:00:1e.0:   MEM window: 0xf0000000-0xf00fffff
[    0.250756] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.250771] pci 0000:00:1e.0: setting latency timer to 64
[    0.250777] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.250780] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.250784] pci_bus 0000:01: resource 0 io:  [0xa000-0xafff]
[    0.250787] pci_bus 0000:01: resource 1 mem: [0xf0000000-0xf00fffff]
[    0.250790] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.250793] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.250848] NET: Registered protocol family 2
[    0.250989] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.251456] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.252206] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.252723] TCP: Hash tables configured (established 131072 bind 65536)
[    0.252727] TCP reno registered
[    0.252899] NET: Registered protocol family 1
[    0.252998] Trying to unpack rootfs image as initramfs...
[    0.486928] Freeing initrd memory: 7456k freed
[    0.494597] cpufreq-nforce2: No nForce2 chipset.
[    0.494637] Scanning for low memory corruption every 60 seconds
[    0.494779] audit: initializing netlink socket (disabled)
[    0.494804] type=2000 audit(1267017274.492:1): initialized
[    0.503570] highmem bounce pool size: 64 pages
[    0.503581] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.505434] VFS: Disk quotas dquot_6.5.2
[    0.505513] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.506241] fuse init (API version 7.12)
[    0.506350] msgmni has been set to 1719
[    0.506654] alg: No test for stdrng (krng)
[    0.506675] io scheduler noop registered
[    0.506679] io scheduler anticipatory registered
[    0.506681] io scheduler deadline registered
[    0.506740] io scheduler cfq registered (default)
[    0.506759] pci 0000:00:02.0: Boot video device
[    0.506944] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.506980] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.507170] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.507175] ACPI: Power Button [PWRF]
[    0.507242] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.507246] ACPI: Power Button [PWRB]
[    0.507641] processor LNXCPU:00: registered as cooling_device0
[    0.507647] ACPI: Processor [CPU0] (supports 2 throttling states)
[    0.507724] processor LNXCPU:01: registered as cooling_device1
[    0.507729] ACPI: Processor [CPU1] (supports 2 throttling states)
[    0.509670] isapnp: Scanning for PnP cards...
[    0.697146] Switched to high resolution mode on CPU 1
[    0.700018] Switched to high resolution mode on CPU 0
[    0.862863] isapnp: No Plug & Play device found
[    0.864351] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.864466] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.864569] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.864932] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.865104] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.866503] brd: module loaded
[    0.867095] loop: module loaded
[    0.867196] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.867337] ata_piix 0000:00:1f.2: version 2.13
[    0.867363]   alloc irq_desc for 19 on node -1
[    0.867366]   alloc kstat_irqs on node -1
[    0.867377] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.867384] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.867442] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.867566] scsi0 : ata_piix
[    0.867694] scsi1 : ata_piix
[    0.868664] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.868669] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.869884] Fixed MDIO Bus: probed
[    0.869933] PPP generic driver version 2.4.2
[    0.870066] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.870094]   alloc irq_desc for 23 on node -1
[    0.870097]   alloc kstat_irqs on node -1
[    0.870104] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.870126] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.870131] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.870197] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.874131] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.874150] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf01c0000
[    0.889028] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.889118] usb usb1: configuration #1 chosen from 1 choice
[    0.889161] hub 1-0:1.0: USB hub found
[    0.889176] hub 1-0:1.0: 8 ports detected
[    0.889266] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.889287] uhci_hcd: USB Universal Host Controller Interface driver
[    0.889325] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.889333] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.889337] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.889380] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.889406] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b000
[    0.889508] usb usb2: configuration #1 chosen from 1 choice
[    0.889544] hub 2-0:1.0: USB hub found
[    0.889554] hub 2-0:1.0: 2 ports detected
[    0.889622] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.889630] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.889634] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.889674] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.889709] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[    0.889807] usb usb3: configuration #1 chosen from 1 choice
[    0.889843] hub 3-0:1.0: USB hub found
[    0.889852] hub 3-0:1.0: 2 ports detected
[    0.889914]   alloc irq_desc for 18 on node -1
[    0.889917]   alloc kstat_irqs on node -1
[    0.889928] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.889935] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.889939] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.889981] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.890015] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b800
[    0.890120] usb usb4: configuration #1 chosen from 1 choice
[    0.890158] hub 4-0:1.0: USB hub found
[    0.890167] hub 4-0:1.0: 2 ports detected
[    0.890226]   alloc irq_desc for 16 on node -1
[    0.890229]   alloc kstat_irqs on node -1
[    0.890235] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.890242] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.890246] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.890288] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.890321] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000bc00
[    0.890429] usb usb5: configuration #1 chosen from 1 choice
[    0.890465] hub 5-0:1.0: USB hub found
[    0.890474] hub 5-0:1.0: 2 ports detected
[    0.890616] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.893481] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.893492] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.893606] mice: PS/2 mouse device common for all mice
[    0.893731] rtc_cmos 00:03: RTC can wake from S4
[    0.893774] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.893805] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.893946] device-mapper: uevent: version 1.0.3
[    0.894078] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.894183] device-mapper: multipath: version 1.1.0 loaded
[    0.894188] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.894349] EISA: Probing bus 0 at eisa.0
[    0.894383] EISA: Detected 0 cards.
[    0.894515] cpuidle: using governor ladder
[    0.894520] cpuidle: using governor menu
[    0.895233] TCP cubic registered
[    0.895400] NET: Registered protocol family 10
[    0.896021] lo: Disabled Privacy Extensions
[    0.896483] NET: Registered protocol family 17
[    0.896509] Bluetooth: L2CAP ver 2.13
[    0.896512] Bluetooth: L2CAP socket layer initialized
[    0.896515] Bluetooth: SCO (Voice Link) ver 0.6
[    0.896517] Bluetooth: SCO socket layer initialized
[    0.896566] Bluetooth: RFCOMM TTY layer initialized
[    0.896572] Bluetooth: RFCOMM socket layer initialized
[    0.896575] Bluetooth: RFCOMM ver 1.11
[    0.896641] Using IPI No-Shortcut mode
[    0.896732] PM: Resume from disk failed.
[    0.896749] registered taskstats version 1
[    0.896883]   Magic number: 14:324:231
[    0.896965] rtc_cmos 00:03: setting system clock to 2010-02-24 13:14:35 UTC (1267017275)
[    0.896969] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.896971] EDD information not available.
[    0.913621] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.028512] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-H10A, JL02, max UDMA/33
[    1.044233] ata2.00: configured for UDMA/33
[    1.064208] ata1.00: HPA unlocked: 976771055 -> 976773168, native 976773168
[    1.064215] ata1.00: ATA-8: ST3500418AS, CC38, max UDMA/133
[    1.064219] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.080440] ata1.00: configured for UDMA/133
[    1.080590] scsi 0:0:0:0: Direct-Access     ATA      ST3500418AS      CC38 PQ: 0 ANSI: 5
[    1.080754] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.080808] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.080882] sd 0:0:0:0: [sda] Write Protect is off
[    1.080886] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.080921] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.081103]  sda:
[    1.084908] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10A  JL02 PQ: 0 ANSI: 5
[    1.097382] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.097387] Uniform CD-ROM driver Revision: 3.20
[    1.097495] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.097553] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.108670]  sda1 sda2 < sda5 >
[    1.134950] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.134974] Freeing unused kernel memory: 540k freed
[    1.135571] Write protecting the kernel text: 4568k
[    1.135627] Write protecting the kernel read-only data: 1836k
[    1.292237] Linux agpgart interface v0.103
[    1.298818] agpgart-intel 0000:00:00.0: Intel 915G Chipset
[    1.299348] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.366837] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.366889] 8139cp 0000:01:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.371922] 8139too Fast Ethernet driver 0.9.28
[    1.372005]   alloc irq_desc for 21 on node -1
[    1.372010]   alloc kstat_irqs on node -1
[    1.372023] 8139too 0000:01:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.373804] eth0: RealTek RTL8139 at 0xa000, 00:14:85:e2:49:89, IRQ 21
[    1.375277] Floppy drive(s): fd0 is 1.44M
[    1.378643] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.434176] FDC 0 is a post-1991 82077
[    1.491638] [drm] Initialized drm 1.1.0 20060810
[    1.507741] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.507753] i915 0000:00:02.0: setting latency timer to 64
[    1.624838] [drm] fb0: inteldrmfb frame buffer device
[    1.624850] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.687744] render error detected, EIR: 0x00000010
[    1.687749] page table error
[    1.687751]   PGTBL_ER: 0x00000010
[    1.687756] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[    1.687765] render error detected, EIR: 0x00000010
[    1.687768] page table error
[    1.687770]   PGTBL_ER: 0x00000010
[    1.694073] [drm] DAC-6: set mode 1024x768 15
[    1.717166] Console: switching to colour frame buffer device 128x48
[    2.034860] PM: Starting manual resume from disk
[    2.034866] PM: Resume from partition 8:5
[    2.034868] PM: Checking hibernation image.
[    2.035048] PM: Resume from disk failed.
[    2.071195] EXT4-fs (sda1): barriers enabled
[    2.088915] kjournald2 starting: pid 378, dev sda1:8, commit interval 5 seconds
[    2.088927] EXT4-fs (sda1): delayed allocation enabled
[    2.088933] EXT4-fs: file extents enabled
[    2.158134] EXT4-fs: mballoc enabled
[    2.158161] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.620350] type=1505 audit(1267017277.223:2): operation="profile_load" pid=401 name=/usr/share/gdm/guest-session/Xsession
[    2.624028] type=1505 audit(1267017277.223:3): operation="profile_load" pid=402 name=/sbin/dhclient3
[    2.624767] type=1505 audit(1267017277.227:4): operation="profile_load" pid=402 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    2.625163] type=1505 audit(1267017277.227:5): operation="profile_load" pid=402 name=/usr/lib/connman/scripts/dhclient-script
[    2.647475] type=1505 audit(1267017277.247:6): operation="profile_load" pid=403 name=/usr/bin/evince
[    2.658944] type=1505 audit(1267017277.259:7): operation="profile_load" pid=403 name=/usr/bin/evince-previewer
[    2.665673] type=1505 audit(1267017277.267:8): operation="profile_load" pid=403 name=/usr/bin/evince-thumbnailer
[    2.689613] type=1505 audit(1267017277.291:9): operation="profile_load" pid=405 name=/usr/lib/cups/backend/cups-pdf
[    2.690454] type=1505 audit(1267017277.291:10): operation="profile_load" pid=405 name=/usr/sbin/cupsd
[    3.660938] Adding 4498160k swap on /dev/sda5.  Priority:-1 extents:1 across:4498160k 
[    3.714502] udev: starting version 147
[    3.761151] EXT4-fs (sda1): internal journal on sda1:8
[    5.315890] ip_tables: (C) 2000-2006 Netfilter Core Team
[    5.680089]   alloc irq_desc for 17 on node -1
[    5.680096]   alloc kstat_irqs on node -1
[    5.680109] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.680158] Intel ICH 0000:00:1e.2: setting latency timer to 64
[    6.004045] intel8x0_measure_ac97_clock: measured 54311 usecs (2617 samples)
[    6.004050] intel8x0: clocking to 48000
[    7.671657] __ratelimit: 9 callbacks suppressed
[    7.671662] type=1505 audit(1267017282.271:14): operation="profile_replace" pid=789 name=/usr/share/gdm/guest-session/Xsession
[    7.674334] type=1505 audit(1267017282.275:15): operation="profile_replace" pid=790 name=/sbin/dhclient3
[    7.675058] type=1505 audit(1267017282.275:16): operation="profile_replace" pid=790 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.675453] type=1505 audit(1267017282.275:17): operation="profile_replace" pid=790 name=/usr/lib/connman/scripts/dhclient-script
[    7.681516] type=1505 audit(1267017282.283:18): operation="profile_replace" pid=791 name=/usr/bin/evince
[    7.693456] type=1505 audit(1267017282.295:19): operation="profile_replace" pid=791 name=/usr/bin/evince-previewer
[    7.701175] type=1505 audit(1267017282.303:20): operation="profile_replace" pid=791 name=/usr/bin/evince-thumbnailer
[    7.711721] type=1505 audit(1267017282.311:21): operation="profile_replace" pid=795 name=/usr/lib/cups/backend/cups-pdf
[    7.712566] type=1505 audit(1267017282.315:22): operation="profile_replace" pid=795 name=/usr/sbin/cupsd
[    7.716231] type=1505 audit(1267017282.319:23): operation="profile_replace" pid=796 name=/usr/sbin/mysqld
[    8.912569] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   12.733829] Linux video capture interface: v2.00
[   12.889271] saa7130/34: v4l2 driver version 0.2.15 loaded
[   12.889359]   alloc irq_desc for 20 on node -1
[   12.889364]   alloc kstat_irqs on node -1
[   12.889377] saa7134 0000:01:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   12.889389] saa7130[0]: found at 0000:01:01.0, rev: 1, irq: 20, latency: 32, mmio: 0xf0000000
[   12.889399] saa7134: <rant>
[   12.889401] saa7134:  Congratulations!  Your TV card vendor saved a few
[   12.889403] saa7134:  cents for a eeprom, thus your pci board has no
[   12.889405] saa7134:  subsystem ID and I can't identify it automatically
[   12.889407] saa7134: </rant>
[   12.889409] saa7134: I feel better now.  Ok, here are the good news:
[   12.889411] saa7134: You can use the card=<nr> insmod option to specify
[   12.889413] saa7134: which board do you have.  The list:
[   12.889419] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   12.889427] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   12.889436] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   12.889444] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   12.889453] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   12.889461] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   12.889469] saa7134:   card=6 -> Tevion MD 9717                          
[   12.889476] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   12.889485] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   12.889492] saa7134:   card=9 -> Medion 5044                             
[   12.889498] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   12.889503] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   12.889510] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[   12.889519] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   12.889525] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   12.889532] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   12.889539] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   12.889550] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   12.889557] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   12.889563] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   12.889571] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   12.889577] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   12.889584] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   12.889591] saa7134:   card=23 -> BMK MPEX Tuner                          
[   12.889597] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   12.889603] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   12.889610] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   12.889618] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[   12.889623] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[   12.889629] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   12.889637] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   12.889644] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   12.889652] saa7134:   card=32 -> AVACS SmartTV                           
[   12.889658] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   12.889666] saa7134:   card=34 -> Noval Prime TV 7133                     
[   12.889671] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   12.889679] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   12.889687] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   12.889692] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   12.889700] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   12.889710] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   12.889717] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   12.889725] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   12.889731] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   12.889737] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   12.889742] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   12.889749] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   12.889756] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   12.889764] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   12.889771] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   12.889778] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   12.889785] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   12.889793] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   12.889801] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   12.889809] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   12.889821] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   12.889830] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   12.889837] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   12.889844] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   12.889858] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   12.889864] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   12.889876] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   12.889884] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   12.889890] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   12.889897] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   12.889904] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   12.889909] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   12.889915] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   12.889922] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   12.889930] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   12.889937] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   12.889945] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   12.889952] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   12.889960] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   12.889967] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   12.889975] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   12.889982] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   12.889989] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   12.889997] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[   12.890005] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   12.890011] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   12.890019] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   12.890026] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   12.890035] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   12.890043] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   12.890052] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   12.890062] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   12.890072] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   12.890081] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   12.890089] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   12.890096] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   12.890106] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   12.890116] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   12.890127] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   12.890135] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   12.890149] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   12.890158] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   12.890171] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   12.890181] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   12.890190] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   12.890200] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   12.890210] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   12.890218] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   12.890226] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   12.890233] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   12.890250] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   12.890258] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   12.890270] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   12.890277] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   12.890286] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   12.890293] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   12.890301] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   12.890311] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   12.890319] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   12.890327] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   12.890335] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   12.890343] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   12.890350] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   12.890359] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   12.890366] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   12.890373] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   12.890383] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   12.890391] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   12.890398] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   12.890405] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   12.890413] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   12.890420] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[   12.890428] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[   12.890437] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[   12.890445] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[   12.890453] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   12.890460] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   12.890467] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[   12.890473] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[   12.890480] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   12.890489] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   12.890497] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   12.890506] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   12.890513] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   12.890521] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   12.890529] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   12.890535] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   12.890543] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   12.890551] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   12.890559] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   12.890567] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[   12.890577] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[   12.890583] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[   12.890591] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[   12.890599] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[   12.890606] saa7134:   card=150 -> Zogis Real Angel 220                    
[   12.890612] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[   12.890620] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[   12.890629] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[   12.890637] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[   12.890648] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[   12.890657] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[   12.890668] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[   12.890677] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[   12.890685] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[   12.890693] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[   12.890700] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[   12.890707] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[   12.890715] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[   12.890722] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[   12.890731] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[   12.890739] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[   12.890747] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[   12.890755] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[   12.890766] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   12.890793] saa7130[0]: board init: gpio is 38500
[   12.890803] IRQ 20/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   12.992263] saa7130[0]: Huh, no eeprom present (err=-5)?
[   12.992270] i2c-adapter i2c-1: Invalid 7-bit address 0x7a
[   12.992882] saa7130[0]: registered device video0 [v4l2]
[   12.992915] saa7130[0]: registered device vbi0
[   13.040415] saa7134 ALSA driver for DMA sound loaded
[   13.040423] saa7130[0]/alsa: UNKNOWN/GENERIC doesn't support digital audio
[   13.144719] __ratelimit: 12 callbacks suppressed
[   13.144726] type=1503 audit(1267017287.747:28): operation="open" pid=1210 parent=1086 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   13.602581] type=1503 audit(1267017288.203:29): operation="open" pid=1218 parent=1217 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   14.474815] parport_pc 00:09: reported by Plug and Play ACPI
[   14.474870] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   14.557293] lp: driver loaded but no devices found
[   14.573362] lp0: using parport0 (interrupt-driven).
[   14.624687] type=1503 audit(1267017289.227:30): operation="open" pid=1242 parent=1241 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   14.634945] intel_rng: FWH not detected
[   14.714482] ppdev: user-space parallel port driver
[   14.926758] psmouse serio1: ID: 10 00 64
[   15.454696] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   15.645110] type=1503 audit(1267017290.247:31): operation="open" pid=1267 parent=1266 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   17.117742] type=1503 audit(1267017291.719:32): operation="open" pid=1285 parent=1284 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   17.269833] type=1503 audit(1267017291.871:33): operation="open" pid=1296 parent=1295 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   19.264024] eth0: no IPv6 routers present
[   20.447644] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.447651] vboxdrv: Successfully done.
[   20.447655] vboxdrv: Found 2 processor cores.
[   20.447789] vboxdrv: fAsync=0 offMin=0x450 offMax=0x3d18
[   20.447873] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.447878] vboxdrv: Successfully loaded version 3.1.2 (interface 0x00100001).
[   23.352587] CPU0 attaching NULL sched-domain.
[   23.352597] CPU1 attaching NULL sched-domain.
[   23.364104] CPU0 attaching sched-domain:
[   23.364110]  domain 0: span 0-1 level SIBLING
[   23.364114]   groups: 0 1
[   23.364120]   domain 1: span 0-1 level MC
[   23.364124]    groups: 0-1 (__cpu_power = 2048)
[   23.364132] CPU1 attaching sched-domain:
[   23.364135]  domain 0: span 0-1 level SIBLING
[   23.364139]   groups: 1 0
[   23.364144]   domain 1: span 0-1 level MC
[   23.364147]    groups: 0-1 (__cpu_power = 2048)
[   25.208423] CPU0 attaching NULL sched-domain.
[   25.208431] CPU1 attaching NULL sched-domain.
[   25.221110] CPU0 attaching sched-domain:
[   25.221115]  domain 0: span 0-1 level SIBLING
[   25.221119]   groups: 0 1
[   25.221126] CPU1 attaching sched-domain:
[   25.221129]  domain 0: span 0-1 level SIBLING
[   25.221133]   groups: 1 0
[  110.137673] saa7134 ALSA driver for DMA sound unloaded
[  179.333018] saa7130/34: v4l2 driver version 0.2.15 loaded
[  179.333100] saa7130[0]: found at 0000:01:01.0, rev: 1, irq: 20, latency: 32, mmio: 0xf0000000
[  179.333115] saa7130[0]: subsystem: 1131:0000, board: LifeView/Typhoon FlyVIDEO2000 [card=3,insmod option]
[  179.333168] saa7130[0]: board init: gpio is 38500
[  179.333173] saa7130[0]: there are different flyvideo cards with different tuners
[  179.333176] saa7130[0]: out there, you might have to use the tuner=<nr> insmod
[  179.333178] saa7130[0]: option to override the default value.
[  179.333297] input: saa7134 IR (LifeView/Typhoon Fl as /devices/pci0000:00/0000:00:1e.0/0000:01:01.0/input/input5
[  179.333386] IRQ 20/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[  179.436307] saa7130[0]: Huh, no eeprom present (err=-5)?
[  179.436314] i2c-adapter i2c-1: Invalid 7-bit address 0x7a
[  179.465102] tuner 1-0061: chip found @ 0xc2 (saa7130[0])
[  179.513036] tuner-simple 1-0061: creating new instance
[  179.513042] tuner-simple 1-0061: type set to 55 (TCL 2002MB)
[  179.537142] saa7130[0]: registered device video0 [v4l2]
[  179.537190] saa7130[0]: registered device vbi0
[  179.537237] saa7130[0]: registered device radio0
[  179.549158] saa7134 ALSA driver for DMA sound loaded
[  179.549163] saa7130[0]/alsa: LifeView/Typhoon FlyVIDEO2000 doesn't support digital audio
[ 2669.591704] saa7134 ALSA driver for DMA sound unloaded
root@allaboutbelgaum:~#

---

### Post by Jose Catre-Vandis on 2010-02-25
Now you have it working, lets make the changes permanent so it works each time you boot up. I am going to work at the terminal for this one, but you can use gedit/mousepad, whatever.

```
sudo nano /etc/modprobe.d/tvcard.conf
```
Enter the following in the file you have just created
```
options saa7134 card=3 tuner=55
```
Then CTRL+X to exit out and save the file. Next time you boot/reboot the modules should be automatically loaded with your card details

---

### Post by ukmad on 2010-02-25
Hurayyyyyyyyyyyyyyy! it worked correctly after that tvcard.cof file insertion.

Thank you very much for your help.

---

### Post by Jose Catre-Vandis on 2010-02-25
:) - please mark as solved (?)

---

### Post by ukmad on 2010-02-26
a small problem is with the sound the alsa mixer mutes the line in sometimes and sometimes i can hear sound 
can we fix this as well
and also how do i say solved just a msg

---

### Post by Jose Catre-Vandis on 2010-02-26
Marking as solved:
At top of thread, Thread Tools, last option

Sound:
Hopefully, if you have alsamixer installed, open a terminal and type **alsamixer**.

Set everything as you need it and then press ESC to exit

then in the terminal type:
```
sudo alsactl store 0
```
This should save your settings through reboots

---

### Post by kggirishkumar on 2011-02-18
dmesg:
[    0.187902] pci 0000:00:0b.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.187925] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
[    0.187930] pci 0000:00:0c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.187933] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.187938] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.187948] pci_bus 0000:00: on NUMA node 0
[    0.187953] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.188164] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.188268] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.188336] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.188405] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.197180] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *11
[    0.197400] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *10
[    0.197622] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.197837] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.198052] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.198266] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.198481] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.198698] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.198915] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[    0.199130] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[    0.199346] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5
[    0.199573] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[    0.199788] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[    0.200011] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *11
[    0.200229] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
[    0.200452] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.200667] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *11
[    0.200892] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.
[    0.201144] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.201193] HEST: Table is not found!
[    0.201301] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=io+mem,locks=none
[    0.201307] vgaarb: loaded
[    0.201503] SCSI subsystem initialized
[    0.204425] libata version 3.00 loaded.
[    0.204425] usbcore: registered new interface driver usbfs
[    0.204425] usbcore: registered new interface driver hub
[    0.204425] usbcore: registered new device driver usb
[    0.204425] ACPI: WMI: Mapper loaded
[    0.204425] PCI: Using ACPI for IRQ routing
[    0.204425] PCI: pci_cache_line_size set to 64 bytes
[    0.204425] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.204425] reserve RAM buffer: 0000000037fb0000 - 0000000037ffffff 
[    0.204530] NetLabel: Initializing
[    0.204533] NetLabel:  domain hash size = 128
[    0.204534] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.204549] NetLabel:  unlabeled traffic allowed by default
[    0.204594] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.204602] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.204607] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.212037] Switching to clocksource hpet
[    0.223659] AppArmor: AppArmor Filesystem Enabled
[    0.223684] pnp: PnP ACPI init
[    0.223708] ACPI: bus type pnp registered
[    0.227868] pnp 00:07: disabling [io  0x0900-0x097f] because it overlaps 0000:00:01.0 BAR 0 [io  0x0900-0x09ff]
[    0.227873] pnp 00:07: disabling [io  0x0980-0x09ff] because it overlaps 0000:00:01.0 BAR 0 [io  0x0900-0x09ff]
[    0.231588] pnp: PnP ACPI: found 16 devices
[    0.231590] ACPI: ACPI bus type pnp unregistered
[    0.231595] PnPBIOS: Disabled by ACPI PNP
[    0.231611] system 00:07: [io  0x0a30-0x0a37] has been reserved
[    0.231614] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.231618] system 00:07: [io  0x0800-0x080f] has been reserved
[    0.231621] system 00:07: [io  0x0500-0x057f] has been reserved
[    0.231624] system 00:07: [io  0x0580-0x05ff] has been reserved
[    0.231628] system 00:07: [io  0x0800-0x087f] could not be reserved
[    0.231631] system 00:07: [io  0x0880-0x08ff] has been reserved
[    0.231634] system 00:07: [io  0x0d00-0x0d7f] has been reserved
[    0.231638] system 00:07: [io  0x0d80-0x0dff] has been reserved
[    0.231641] system 00:07: [io  0x2000-0x207f] has been reserved
[    0.231645] system 00:07: [io  0x2080-0x20ff] has been reserved
[    0.231649] system 00:07: [mem 0x000d0000-0x000d3fff window] has been reserved
[    0.231652] system 00:07: [mem 0x000d4000-0x000d7fff window] has been reserved
[    0.231656] system 00:07: [mem 0x000de000-0x000dffff window] has been reserved
[    0.231660] system 00:07: [mem 0xfefe0000-0xfefe01ff] has been reserved
[    0.231664] system 00:07: [mem 0xfefe1000-0xfefe1fff] has been reserved
[    0.231667] system 00:07: [mem 0xfee01000-0xfeefffff] has been reserved
[    0.231671] system 00:07: [mem 0xffb80000-0xffffffff] could not be reserved
[    0.231674] system 00:07: [mem 0xff300000-0xff3fffff] has been reserved
[    0.231681] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.231685] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.231688] system 00:09: [mem 0x38000000-0x3fffffff] has been reserved
[    0.231695] system 00:0c: [io  0x0230-0x023f] has been reserved
[    0.231698] system 00:0c: [io  0x0290-0x029f] has been reserved
[    0.231702] system 00:0c: [io  0x0a00-0x0a0f] has been reserved
[    0.231705] system 00:0c: [io  0x0a10-0x0a1f] has been reserved
[    0.231711] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.231718] system 00:0f: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.231721] system 00:0f: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.231725] system 00:0f: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.231728] system 00:0f: [mem 0x00100000-0x37ffffff] could not be reserved
[    0.231732] system 00:0f: [mem 0xff700000-0xffffffff] could not be reserved
[    0.268103] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.268108] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.268113] pci 0000:00:04.0:   bridge window [mem 0xdff00000-0xdfffffff]
[    0.268117] pci 0000:00:04.0:   bridge window [mem pref disabled]
[    0.268121] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.268124] pci 0000:00:09.0:   bridge window [io  disabled]
[    0.268127] pci 0000:00:09.0:   bridge window [mem disabled]
[    0.268130] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    0.268134] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
[    0.268136] pci 0000:00:0b.0:   bridge window [io  disabled]
[    0.268140] pci 0000:00:0b.0:   bridge window [mem disabled]
[    0.268142] pci 0000:00:0b.0:   bridge window [mem pref disabled]
[    0.268147] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
[    0.268149] pci 0000:00:0c.0:   bridge window [io  disabled]
[    0.268152] pci 0000:00:0c.0:   bridge window [mem disabled]
[    0.268155] pci 0000:00:0c.0:   bridge window [mem pref disabled]
[    0.268165] pci 0000:00:04.0: setting latency timer to 64
[    0.268171] pci 0000:00:09.0: setting latency timer to 64
[    0.268177] pci 0000:00:0b.0: setting latency timer to 64
[    0.268182] pci 0000:00:0c.0: setting latency timer to 64
[    0.268186] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.268189] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.268192] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.268195] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.268198] pci_bus 0000:00: resource 8 [mem 0x38000000-0xff6fffff]
[    0.268202] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.268205] pci_bus 0000:01: resource 1 [mem 0xdff00000-0xdfffffff]
[    0.268208] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.268210] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.268213] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.268216] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.268219] pci_bus 0000:01: resource 8 [mem 0x38000000-0xff6fffff]
[    0.268266] NET: Registered protocol family 2
[    0.268342] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.268712] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.269651] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.270137] TCP: Hash tables configured (established 131072 bind 65536)
[    0.270140] TCP reno registered
[    0.270144] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.270161] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.270302] NET: Registered protocol family 1
[    0.270435] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.270485] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.270546] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.270605] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.270669] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.270738] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.270811] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.270818] pci 0000:00:0d.0: Boot video device
[    0.270833] PCI: CLS 64 bytes, default 64
[    0.271088] cpufreq-nforce2: No nForce2 chipset.
[    0.271129] Scanning for low memory corruption every 60 seconds
[    0.271263] audit: initializing netlink socket (disabled)
[    0.271274] type=2000 audit(1298096028.268:1): initialized
[    0.283258] highmem bounce pool size: 64 pages
[    0.283264] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.285602] VFS: Disk quotas dquot_6.5.2
[    0.285682] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.286476] fuse init (API version 7.14)
[    0.286603] msgmni has been set to 1712
[    0.286959] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.286962] io scheduler noop registered
[    0.286965] io scheduler deadline registered
[    0.286986] io scheduler cfq registered (default)
[    0.287129] pcieport 0000:00:09.0: setting latency timer to 64
[    0.287150]   alloc irq_desc for 40 on node -1
[    0.287153]   alloc kstat_irqs on node -1
[    0.287164] pcieport 0000:00:09.0: irq 40 for MSI/MSI-X
[    0.287221] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.287237]   alloc irq_desc for 41 on node -1
[    0.287239]   alloc kstat_irqs on node -1
[    0.287245] pcieport 0000:00:0b.0: irq 41 for MSI/MSI-X
[    0.287295] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.287311]   alloc irq_desc for 42 on node -1
[    0.287313]   alloc kstat_irqs on node -1
[    0.287319] pcieport 0000:00:0c.0: irq 42 for MSI/MSI-X
[    0.287406] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.287437] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.287675] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.287682] ACPI: Power Button [PWRB]
[    0.287742] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.287746] ACPI: Power Button [PWRF]
[    0.287984] ACPI: acpi_idle registered with cpuidle
[    0.292336] ERST: Table is not found!
[    0.292680] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.292785] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.293176] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.294655] brd: module loaded
[    0.295332] loop: module loaded
[    0.295656] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.296015] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    0.296021]   alloc irq_desc for 23 on node -1
[    0.296024]   alloc kstat_irqs on node -1
[    0.296036] pata_acpi 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.296053] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.296062] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.296468] Fixed MDIO Bus: probed
[    0.296553] PPP generic driver version 2.4.2
[    0.296600] tun: Universal TUN/TAP device driver, 1.6
[    0.296603] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.296703] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.297005] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    0.297009]   alloc irq_desc for 22 on node -1
[    0.297011]   alloc kstat_irqs on node -1
[    0.297019] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[    0.297038] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.297042] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.297082] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.297112] ehci_hcd 0000:00:02.1: debug port 1
[    0.297120] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.297146] ehci_hcd 0000:00:02.1: irq 22, io mem 0xdfefec00
[    0.297238] isapnp: Scanning for PnP cards...
[    0.346203] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.346340] hub 1-0:1.0: USB hub found
[    0.346346] hub 1-0:1.0: 8 ports detected
[    0.346432] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.346725] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[    0.346728]   alloc irq_desc for 21 on node -1
[    0.346730]   alloc kstat_irqs on node -1
[    0.346739] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 21 (level, low) -> IRQ 21
[    0.346748] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.346751] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.346797] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.346826] ohci_hcd 0000:00:02.0: irq 21, io mem 0xdfeff000
[    0.436062] hub 2-0:1.0: USB hub found
[    0.436068] hub 2-0:1.0: 8 ports detected
[    0.436142] uhci_hcd: USB Universal Host Controller Interface driver
[    0.436255] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.436679] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.436685] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.436814] mice: PS/2 mouse device common for all mice
[    0.436964] rtc_cmos 00:02: RTC can wake from S4
[    0.437013] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.437052] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.437209] device-mapper: uevent: version 1.0.3
[    0.480934] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.486846] Freeing initrd memory: 10520k freed
[    0.495975] device-mapper: multipath: version 1.1.1 loaded
[    0.495980] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.496228] EISA: Probing bus 0 at eisa.0
[    0.496232] EISA: Cannot allocate resource for mainboard
[    0.496235] Cannot allocate resource for EISA slot 1
[    0.496238] Cannot allocate resource for EISA slot 2
[    0.496241] Cannot allocate resource for EISA slot 3
[    0.496243] Cannot allocate resource for EISA slot 4
[    0.496246] Cannot allocate resource for EISA slot 5
[    0.496248] Cannot allocate resource for EISA slot 6
[    0.496251] Cannot allocate resource for EISA slot 7
[    0.496254] Cannot allocate resource for EISA slot 8
[    0.496256] EISA: Detected 0 cards.
[    0.496353] cpuidle: using governor ladder
[    0.496356] cpuidle: using governor menu
[    0.496729] TCP cubic registered
[    0.496924] NET: Registered protocol family 10
[    0.497379] lo: Disabled Privacy Extensions
[    0.497658] NET: Registered protocol family 17
[    0.497708] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ (2 cpu cores) (version 2.20.00)
[    0.497721] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    0.497722] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    0.497745] Using IPI No-Shortcut mode
[    0.497859] PM: Resume from disk failed.
[    0.497873] registered taskstats version 1
[    0.498134]   Magic number: 15:204:216
[    0.498260] rtc_cmos 00:02: setting system clock to 2011-02-19 06:13:49 UTC (1298096029)
[    0.498263] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.498265] EDD information not available.
[    0.509103] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.654914] isapnp: No Plug & Play device found
[    0.654940] Freeing unused kernel memory: 688k freed
[    0.655505] Write protecting the kernel text: 4936k
[    0.655549] Write protecting the kernel read-only data: 1976k
[    0.675518] udev[75]: starting version 163
[    0.739234] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.739608] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    0.739615]   alloc irq_desc for 20 on node -1
[    0.739618]   alloc kstat_irqs on node -1
[    0.739632] forcedeth 0000:00:07.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    0.739637] forcedeth 0000:00:07.0: setting latency timer to 64
[    0.812248] Floppy drive(s): fd0 is 1.44M
[    0.831907] FDC 0 is a post-1991 82077
[    1.256798] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x1374 @ 1, addr 00:1e:8c:1e:3f:39
[    1.256803] forcedeth 0000:00:07.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    1.256833] pata_amd 0000:00:06.0: version 0.4.1
[    1.256896] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.257002] scsi0 : pata_amd
[    1.257154] scsi1 : pata_amd
[    1.258016] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.258020] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.258069] sata_nv 0000:00:08.0: version 3.5
[    1.258088] sata_nv 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.258150] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.258225] scsi2 : sata_nv
[    1.258299] scsi3 : sata_nv
[    1.258476] ata3: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xc880 irq 23
[    1.258480] ata4: SATA max UDMA/133 cmd 0xd000 ctl 0xcc00 bmdma 0xc888 irq 23
[    1.428339] ata1.01: ATAPI: SONY    DVD RW AW-Q170A, 1.70, max UDMA/66
[    1.428368] ata1: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc50000) ACPI=0x1f01f (900:30:0x14)
[    1.444284] ata1.01: configured for UDMA/66
[    1.445473] scsi 0:0:1:0: CD-ROM            SONY     DVD RW AW-Q170A  1.70 PQ: 0 ANSI: 5
[    1.447950] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.447954] Uniform CD-ROM driver Revision: 3.20
[    1.448107] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.448195] sr 0:0:1:0: Attached scsi generic sg0 type 5
[    1.448297] ata2: port disabled. ignoring.
[    1.724037] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.777014] ata3.00: ATA-7: ST3160211AS, 3.AAE, max UDMA/133
[    1.777018] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.858051] ata3.00: configured for UDMA/133
[    1.858181] scsi 2:0:0:0: Direct-Access     ATA      ST3160211AS      3.AA PQ: 0 ANSI: 5
[    1.858368] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.858393] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.858428] sd 2:0:0:0: [sda] Write Protect is off
[    1.858432] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.858461] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.858683]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    1.940895] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.178268] ata4: SATA link down (SStatus 0 SControl 300)
[    3.133555] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   12.054551] udev[315]: starting version 163
[   12.104957] Adding 999420k swap on /dev/sda6.  Priority:-1 extents:1 across:999420k 
[   12.174508] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   12.175265] i2c i2c-0: nForce2 SMBus adapter at 0x600
[   12.175324] i2c i2c-1: nForce2 SMBus adapter at 0x700
[   12.213834] lp: driver loaded but no devices found
[   12.227358] Linux agpgart interface v0.103
[   12.382981] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   12.406647] parport_pc 00:06: reported by Plug and Play ACPI
[   12.406697] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   12.407001] IR NEC protocol handler initialized
[   12.414269] Linux video capture interface: v2.00
[   12.431304] type=1400 audit(1298076241.430:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=527 comm="apparmor_parser"
[   12.431635] type=1400 audit(1298076241.430:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=527 comm="apparmor_parser"
[   12.431828] type=1400 audit(1298076241.430:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=527 comm="apparmor_parser"
[   12.433612] type=1400 audit(1298076241.434:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=530 comm="apparmor_parser"
[   12.433946] type=1400 audit(1298076241.434:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=530 comm="apparmor_parser"
[   12.434139] type=1400 audit(1298076241.434:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=530 comm="apparmor_parser"
[   12.434433] psmouse serio1: ID: 10 00 64
[   12.442212] [drm] Initialized drm 1.1.0 20060810
[   12.451388] ppdev: user-space parallel port driver
[   12.454932] IR RC5(x) protocol handler initialized
[   12.485040] saa7130/34: v4l2 driver version 0.2.16 loaded
[   12.485459] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 19
[   12.485466]   alloc irq_desc for 19 on node -1
[   12.485469]   alloc kstat_irqs on node -1
[   12.485481] saa7134 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[   12.485488] saa7130[0]: found at 0000:01:07.0, rev: 1, irq: 19, latency: 64, mmio: 0xdffefc00
[   12.485496] saa7130[0]: subsystem: 1131:0000, board: LifeView/Typhoon FlyVIDEO2000 [card=3,insmod option]
[   12.485523] saa7130[0]: board init: gpio is 38500
[   12.485526] saa7130[0]: there are different flyvideo cards with different tuners
[   12.485528] saa7130[0]: out there, you might have to use the tuner=<nr> insmod
[   12.485529] saa7130[0]: option to override the default value.
[   12.486034] IR RC6 protocol handler initialized
[   12.499226] IR JVC protocol handler initialized
[   12.508291] lp0: using parport0 (interrupt-driven).
[   12.515394] IR Sony protocol handler initialized
[   12.535580] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 23
[   12.535589] nouveau 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 23 (level, low) -> IRQ 23
[   12.535594] nouveau 0000:00:0d.0: setting latency timer to 64
[   12.538873] lirc_dev: IR Remote Control driver registered, major 251 
[   12.540850] IR LIRC bridge handler initialized
[   12.542799] [drm] nouveau 0000:00:0d.0: Detected an NV40 generation card (0x04c000a2)
[   12.544785] [drm] nouveau 0000:00:0d.0: Attempting to load BIOS image from PRAMIN
[   12.584671] [drm] nouveau 0000:00:0d.0: ... appears to be valid
[   12.584675] [drm] nouveau 0000:00:0d.0: BIT BIOS found
[   12.584679] [drm] nouveau 0000:00:0d.0: Bios version 05.61.32.26
[   12.584683] [drm] nouveau 0000:00:0d.0: BIT table 'd' not found
[   12.584687] [drm] nouveau 0000:00:0d.0: Found Display Configuration Block version 3.0
[   12.584691] [drm] nouveau 0000:00:0d.0: Raw DCB entry 0: 01000310 00000023
[   12.584695] [drm] nouveau 0000:00:0d.0: Raw DCB entry 1: 00110204 942b0003
[   12.584700] [drm] nouveau 0000:00:0d.0: DCB connector table: VHER 0x30 5 10 2
[   12.584704] [drm] nouveau 0000:00:0d.0:   0: 0x00000000: type 0x00 idx 0 tag 0xff
[   12.584707] [drm] nouveau 0000:00:0d.0:   1: 0x00001131: type 0x31 idx 1 tag 0x07
[   12.584711] [drm] nouveau 0000:00:0d.0:   2: 0x00000110: type 0x10 idx 2 tag 0xff
[   12.584714] [drm] nouveau 0000:00:0d.0:   3: 0x00000111: type 0x11 idx 3 tag 0xff
[   12.584718] [drm] nouveau 0000:00:0d.0:   4: 0x00000113: type 0x13 idx 4 tag 0xff
[   12.584728] [drm] nouveau 0000:00:0d.0: Parsing VBIOS init table 0 at offset 0xD9C9
[   12.584732] [drm] nouveau 0000:00:0d.0: ======= misaligned reg 0x0060081D =======
[   12.584790] [drm] nouveau 0000:00:0d.0: ======= misaligned reg 0x0060081D =======
[   12.584899] [drm] nouveau 0000:00:0d.0: Parsing VBIOS init table 1 at offset 0xDB17
[   12.584902] [drm] nouveau 0000:00:0d.0: Parsing VBIOS init table 2 at offset 0xDB18
[   12.584969] [drm] nouveau 0000:00:0d.0: Parsing VBIOS init table 3 at offset 0xDC9A
[   12.584974] [drm] nouveau 0000:00:0d.0: Parsing VBIOS init table 4 at offset 0xDCE3
[   12.584979] [drm] nouveau 0000:00:0d.0: Detected 128MiB VRAM
[   12.590162] [TTM] Zone  kernel: Available graphics memory: 443988 kiB.
[   12.590167] [TTM] Zone highmem: Available graphics memory: 447928 kiB.
[   12.590169] [TTM] Initializing pool allocator.
[   12.591086] [drm] nouveau 0000:00:0d.0: 64 MiB GART (aperture)
[   12.591612] [drm] nouveau 0000:00:0d.0: Allocating FIFO number 0
[   12.591936] [drm] nouveau 0000:00:0d.0: nouveau_channel_alloc: initialised FIFO 0
[   12.591943] [drm] nouveau 0000:00:0d.0: Initial CRTC_OWNER is 0
[   12.591949] [drm] nouveau 0000:00:0d.0: Saving VGA fonts
[   12.633859] [drm] nouveau 0000:00:0d.0: DCB type 4 not known
[   12.633864] [drm] nouveau 0000:00:0d.0: Detected a VGA connector
[   12.638139] [drm] nouveau 0000:00:0d.0: Setting dpms mode 3 on vga encoder (output 0)
[   12.763718] [drm] nouveau 0000:00:0d.0: allocated 1024x768 fb: 0x49000, bo ef9d3400
[   12.796558] Registered IR keymap rc-flyvideo
[   12.796680] input: saa7134 IR (LifeView/Typhoon Fl as /devices/pci0000:00/0000:00:04.0/0000:01:07.0/rc/rc0/input3
[   12.796759] rc0: saa7134 IR (LifeView/Typhoon Fl as /devices/pci0000:00/0000:00:04.0/0000:01:07.0/rc/rc0
[   12.830888] [drm] nouveau 0000:00:0d.0: Setting dpms mode 0 on vga encoder (output 0)
[   12.830894] [drm] nouveau 0000:00:0d.0: Output VGA-1 is running on CRTC 0 using output A
[   12.831998] Console: switching to colour frame buffer device 128x48
[   12.832779] fb0: nouveaufb frame buffer device
[   12.832782] drm: registered panic notifier
[   12.832790] Slow work thread pool: Starting up
[   12.832931] Slow work thread pool: Ready
[   12.832950] [drm] Initialized nouveau 0.0.16 20090420 for 0000:00:0d.0 on minor 0
[   12.833893] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   12.833900] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   12.833905] hda_intel: Disable MSI for Nvidia chipset
[   12.833956] HDA Intel 0000:00:05.0: setting latency timer to 64
[   12.900727] saa7130[0]: Huh, no eeprom present (err=-5)?
[   12.919224] type=1400 audit(1298076241.918:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=736 comm="apparmor_parser"
[   12.919407] type=1400 audit(1298076241.918:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=737 comm="apparmor_parser"
[   12.919754] type=1400 audit(1298076241.918:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=737 comm="apparmor_parser"
[   12.919952] type=1400 audit(1298076241.918:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=737 comm="apparmor_parser"
[   12.976151] tuner 3-0061: chip found @ 0xc2 (saa7130[0])
[   12.980599]   alloc irq_desc for 43 on node -1
[   12.980604]   alloc kstat_irqs on node -1
[   12.980615] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
[   13.162404] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   13.708078] tuner-simple 3-0061: creating new instance
[   13.708084] tuner-simple 3-0061: type set to 55 (TCL 2002MB)
[   13.732202] saa7130[0]: registered device video0 [v4l2]
[   13.732247] saa7130[0]: registered device vbi0
[   13.732298] saa7130[0]: registered device radio0
[   13.744081] saa7134 ALSA driver for DMA sound loaded
[   13.744086] saa7130[0]/alsa: LifeView/Typhoon FlyVIDEO2000 doesn't support digital audio
[   14.340469] [drm] nouveau 0000:00:0d.0: Allocating FIFO number 1
[   14.340796] [drm] nouveau 0000:00:0d.0: nouveau_channel_alloc: initialised FIFO 1
[   17.316864] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   19.738892] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   23.096023] eth0: no IPv6 routers present
[   46.912225] lo: Disabled Privacy Extensions
girish@girish-System-Product-Name:~$

---

