---
title: "Live CD Freeze"
date: 2005-10-30
forum: Installation &amp; Upgrades
---

### Post by schnarff on 2005-10-30
I run Ubuntu on my desktop at work, and I was getting ready to bite the bullet and move from my really old Slackware system at home over to Ubuntu, mainly so I could run ndiswrapper and have wireless not suck so bad. Since the machine is a PIII-800 w/384 MB of RAM, I figured I'd try the live CD first, to make sure Ubuntu wasn't going to chew up all of my resources just existing before I went through all of the hassle of switching OSes.

Unfortunately, however, when I boot up with the latest Breezy Badger live CD for i386, I never finish the boot process. I can pick my language, it detects devices, pulls up the little Ubuntu screen with the horribly unreadable brown text below, runs through a bunch of items there...and then gives me a black screen with a cursor at the top left, completely freezing in the process. I let it sit for over 10 minutes the second time, to make sure it wasn't just thinking really hard, and nada.

I don't think I've got any particularly oddball hardware. Since I don't know for certain what causes Ubuntu problems, however, here's the dmesg from my current kernel. If anyone can help me figure out what's going on, I'd appreciate it very much.

Thanks,
Alex Kirk

```
Linux version 2.4.22 (root@midas) (gcc version 3.2.3) #6 Tue Sep 2 17:43:01 PDT 2003
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 0000000017ef0000 (usable)
 BIOS-e820: 0000000017ef0000 - 0000000017ef3000 (ACPI NVS)
 BIOS-e820: 0000000017ef3000 - 0000000017f00000 (ACPI data)
 BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
382MB LOWMEM available.
On node 0 totalpages: 98032
zone(0): 4096 pages.
zone(1): 93936 pages.
zone(2): 0 pages.
Kernel command line: auto BOOT_IMAGE=Linux-Good ro root=301 hdd=ide-scsi
ide_setup: hdd=ide-scsi
Initializing CPU#0
Detected 801.835 MHz processor.
Console: colour dummy device 80x25
Calibrating delay loop... 1599.07 BogoMIPS
Memory: 384688k/392128k available (1813k kernel code, 7052k reserved, 614k data, 116k init, 0k highmem)
Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
Inode cache hash table entries: 32768 (order: 6, 262144 bytes)
Mount cache hash table entries: 512 (order: 0, 4096 bytes)
Buffer cache hash table entries: 32768 (order: 5, 131072 bytes)
Page-cache hash table entries: 131072 (order: 7, 524288 bytes)
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 256K
CPU:     After generic, caps: 0383f9ff 00000000 00000000 00000000
CPU:             Common caps: 0383f9ff 00000000 00000000 00000000
CPU: Intel Pentium III (Coppermine) stepping 06
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
POSIX conformance testing by UNIFIX
mtrr: v1.40 (20010327) Richard Gooch (rgooch@atnf.csiro.au)
mtrr: detected mtrr type: Intel
PCI: PCI BIOS revision 2.10 entry at 0xfb210, last bus=1
PCI: Using configuration type 1
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
Transparent bridge - Intel Corp. 82801BA/CA/DB/EB PCI Bridge
PCI: Using IRQ router PIIX [8086/2440] at 00:1f.0
Linux NET4.0 for Linux 2.4
Based upon Swansea University Computer Society NET3.039
Initializing RT netlink socket
Starting kswapd
VFS: Disk quotas vdquot_6.5.1
Journalled Block Device driver loaded
vesafb: framebuffer at 0xd6000000, mapped to 0xd880d000, size 1536k
vesafb: mode is 1024x768x8, linelength=1024, pages=4
vesafb: protected mode interface info at c7d3:0000
vesafb: scrolling: redraw
Console: switching to colour frame buffer device 128x48
fb0: VESA VGA frame buffer device
pty: 512 Unix98 ptys configured
Serial driver version 5.05c (2001-07-08) with HUB-6 MANY_PORTS MULTIPORT SHARE_IRQ SERIAL_PCI enabled
ttyS00 at 0x03f8 (irq = 4) is a 16550A
ttyS01 at 0x02f8 (irq = 3) is a 16550A
Real Time Clock Driver v1.10e
FDC 0 is a post-1991 82077
RAMDISK driver initialized: 16 RAM disks of 7777K size 1024 blocksize
loop: loaded (max 8 devices)
Uniform Multi-Platform E-IDE driver Revision: 7.00beta4-2.4
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH2: IDE controller at PCI slot 00:1f.1
ICH2: chipset revision 2
ICH2: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
hda: WDC WD1600JB-00FUA0, ATA DISK drive
hdb: Maxtor 92049U6, ATA DISK drive
blk: queue c03a9d80, I/O limit 4095Mb (mask 0xffffffff)
blk: queue c03a9ebc, I/O limit 4095Mb (mask 0xffffffff)
hdc: CD-R/RW RW7080A, ATAPI CD/DVD-ROM drive
hdd: CREATIVE CD-RW RW1210E, ATAPI CD/DVD-ROM drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
ide1 at 0x170-0x177,0x376 on irq 15
hda: attached ide-disk driver.
hda: host protected area => 1
hda: 312581808 sectors (160042 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
hdb: attached ide-disk driver.
hdb: host protected area => 1
hdb: 39882528 sectors (20420 MB) w/2048KiB Cache, CHS=2482/255/63, UDMA(66)
hdc: attached ide-cdrom driver.
hdc: ATAPI 32X CD-ROM CD-R/RW drive, 4096kB Cache, DMA
Uniform CD-ROM driver Revision: 3.12
Partition check:
 hda: hda1 hda2 hda3 hda4
 hdb: hdb1 hdb2 hdb3 hdb4
SCSI subsystem driver Revision: 1.00
kmod: failed to exec /sbin/modprobe -s -k scsi_hostadapter, errno = 2
kmod: failed to exec /sbin/modprobe -s -k scsi_hostadapter, errno = 2
kmod: failed to exec /sbin/modprobe -s -k scsi_hostadapter, errno = 2
md: linear personality registered as nr 1
md: raid0 personality registered as nr 2
md: raid1 personality registered as nr 3
md: raid5 personality registered as nr 4
raid5: measuring checksumming speed
   8regs     :  1327.200 MB/sec
   32regs    :   796.000 MB/sec
   pIII_sse  :  1644.000 MB/sec
   pII_mmx   :  1799.200 MB/sec
   p5_mmx    :  1877.200 MB/sec
raid5: using function: pIII_sse (1644.000 MB/sec)
md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
md: Autodetecting RAID arrays.
md: autorun ...
md: ... autorun DONE.
LVM version 1.0.5+(22/07/2002)
Initializing Cryptographic API
NET4: Linux TCP/IP 1.0 for NET4.0
IP Protocols: ICMP, UDP, TCP
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET4: Unix domain sockets 1.0/SMP for Linux NET4.0.
VFS: Mounted root (ext2 filesystem) readonly.
Freeing unused kernel memory: 116k freed
Adding Swap: 257032k swap-space (priority -1)
Adding Swap: 522104k swap-space (priority -2)
Linux agpgart interface v0.99 (c) Jeff Hartmann
agpgart: Maximum main memory to use for agp memory: 320M
agpgart: agpgart: Detected an Intel i815 Chipset.
agpgart: detected 4MB dedicated video ram.
agpgart: AGP aperture is 64M @ 0xd0000000
hdd: attached ide-scsi driver.
scsi0 : SCSI host adapter emulation for IDE ATAPI devices
  Vendor: CREATIVE  Model: CD-RW RW1210E     Rev: LCS6
  Type:   CD-ROM                             ANSI SCSI revision: 02
Attached scsi CD-ROM sr0 at scsi0, channel 0, id 0, lun 0
sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
prism2pci_init: prism2_pci.o: 0.2.1-pre23 Loaded
prism2pci_init: dev_info is: prism2_pci
PCI: Found IRQ 10 for device 01:0b.0
A Prism2.5 PCI device found, phymem:0xd6800000, irq:10, mem:0xd8ab0000
Linux Tulip driver version 0.9.15-pre12 (Aug 9, 2002)
PCI: Found IRQ 11 for device 01:09.0
tulip0:  MII transceiver #1 config 3000 status 7829 advertising 01e1.
eth0: Lite-On 82c168 PNIC rev 32 at 0xc400, 00:A0:CC:5D:95:8D, IRQ 11.
hfa384x_docmd_wait: hfa384x_cmd timeout(2), reg=0x0.
prism2mgmt_readpda: hfa384x_drvr_readpda() failed, result=-110
hfa384x_docmd_wait: hfa384x_cmd timeout(1), reg=0xc100.
hfa384x_cmd_access: Call to hfa384x_docmd_wait failed (-110 1)
Writing 2352 bytes to ram @0x7e0000
Writing 2520 bytes to ram @0x7e0a00
Writing 2 bytes to ram @0x7e17fe
PCI: Setting latency timer of device 00:1f.5 to 64
intel8x0: clocking to 48000
PDA Read from 0x007f0000 in EXTDS space.
PDA Read from 0x007f0000 in EXTDS space.
PDA Read from 0x007f0000 in EXTDS space.
usb.c: registered new driver usbdevfs
usb.c: registered new driver hub
Writing 2590 bytes to ram @0x7e0000
Writing 2268 bytes to ram @0x7e0b00
Writing 2 bytes to ram @0x7e17fe
uhci.c: USB Universal Host Controller Interface driver v1.1
PCI: Setting latency timer of device 00:1f.2 to 64
uhci.c: USB UHCI at I/O 0xd000, IRQ 10
usb.c: new USB bus registered, assigned bus number 1
hub.c: USB hub found
hub.c: 2 ports detected
PCI: Setting latency timer of device 00:1f.4 to 64
uhci.c: USB UHCI at I/O 0xd400, IRQ 9
usb.c: new USB bus registered, assigned bus number 2
hub.c: USB hub found
hub.c: 2 ports detected
Writing 4096 bytes to ram @0x7e17fe
Writing 4096 bytes to ram @0x7e27fe
Writing 4096 bytes to ram @0x7e37fe
Writing 4096 bytes to ram @0x7e47fe
Writing 4096 bytes to ram @0x7e57fe
Writing 4096 bytes to ram @0x7e67fe
Writing 4096 bytes to ram @0x7e77fe
Writing 4096 bytes to ram @0x7e87fe
Writing 4096 bytes to ram @0x7e97fe
Writing 4096 bytes to ram @0x7ea7fe
Writing 4096 bytes to ram @0x7eb7fe
Writing 4096 bytes to ram @0x7ec7fe
Writing 4096 bytes to ram @0x7ed7fe
Writing 676 bytes to ram @0x7ee7fe
Writing 4096 bytes to ram @0x7f0800
Writing 3282 bytes to ram @0x7fe000
ident: nic h/w: id=0x8013 1.0.0
ident: pri f/w: id=0x15 1.1.4
ident: sta f/w: id=0x1f 1.8.3
MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=4/5
STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/15
PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
Prism2 card SN: 99SA01000000
parport0: PC-style at 0x378 (0x778) [PCSPP,TRISTATE,EPP]
parport0: irq 7 detected
parport0: Printer, Hewlett-Packard hp LaserJet 1150
lp0: using parport0 (polling).
prism2_pci.o: 0.2.1-pre23 Unloaded
Cisco Systems VPN Client Version 4.0.3 (B) kernel module loaded
hostap_crypt: registered algorithm 'NULL'
hostap_pci: 0.4.0 - 2005-04-25 (Jouni Malinen <jkmaline@cc.hut.fi>)
PCI: Found IRQ 10 for device 01:0b.0
hostap_pci: Registered netdevice wifi0
wifi0: Original COR value: 0x0
hostap_pci: assuming no Primary image in flash - card initialization not completed
wifi0: test Genesis mode with HCR 0x1f
wifi0: Original COR value: 0x0
Readback test failed, HCR 0x1f write 00 e1 a1 ff read 00 c1 a1 c1
wifi0: test Genesis mode with HCR 0x0f
wifi0: Original COR value: 0xa1
Readback test succeeded, HCR 0x0f
wifi0: Intersil Prism2.5 PCI: mem=0xd6800000, irq=10
wifi0: registered netdevice wlan0
wlan0: cannot set RID fc02 (len=34) - no PRI f/w
hostap_crypt: registered algorithm 'WEP'
wifi0: cannot get RID fc28 (len=2) - no PRI f/w
Could not read current WEP flags.
wifi0: encryption setup failed
wlan0: set_encryption failed
wlan0: could not set interface UP - no PRI f/w
ip_tables: (C) 2000-2002 Netfilter core team
ip_conntrack version 2.1 (3063 buckets, 24504 max) - 292 bytes per conntrack
```

---

### Post by aysiu on 2005-10-30
If you're absolutely certain it's not your hardware, then it's the disc--corrupted during download or during the burn.

---

### Post by schnarff on 2005-10-30
Actually, I'm pretty sure it's not a corrupted CD. I had burned a copy at work and then lost it, and so I had to burn the copy I was using when I made my original post from a separate download. Well, I just found the one I'd burned at work, and I got the exact same result with it, too. Seeing as how the two CDs came from distinct downloads and were burned on distinct machines, I doubt if it was just a bad CD.

---

### Post by twbutler on 2005-11-28
I am also having the exact same issue with my system - I am using the live CD of kubuntu 5.10, and when the system is getting ready to start X windows, I get a black screen with the white "cursor" underbar in the top left and then the system hangs!   :confused: 

Here are my specs:
MSI K8N Neo4 Platinum
AMD64 3200+
MSI NX6600LE TD256E Pci-e video card

Any one know of a solution?

Thanks...
T

---

### Post by DimaT on 2005-11-29
I have the same problem. I just got Ubantu live CD and tryed to load my old laptop IBM Thinkpad X600. I could pick up language, go throught process, after I have seen progress bar and Ubantu's logo. After I just sow black screen with mouse arrow. I could move the arrow with mouth but that's it.

---

### Post by Alcwyn George on 2005-12-01
Please if you find the answer mail me, I have tried with 5 new CD's not downloads and only get as for as the cursur?
    [email]algeorge@dowco.com[/email]

---

### Post by tcjudd on 2005-12-01
I am getting the same problem with both Ubuntu 5.10 and Kubuntu 5.10 live...the screen goes black with the mouse cursor (underscore) when either Gnome or KDE is starting up.

My system specs:

Intel PIII, 866 MHz
256 MB RAM
NVIDIA GeForce 2 MX 440 (64MB)

I'm certainly open to this being a hardware issue, but I have run several other live distros on this machine with both Gnome and KDE (i.e., Knoppix, Goblin, Beatrix, Slax).

Any help would be greatly appreciated!  Thanks!

---

### Post by linear on 2005-12-01
[QUOTE=tcjudd]the screen goes black with the mouse cursor (underscore) when either Gnome or KDE is starting up.[/QUOTE]

Might be incorrect settings in xorg.conf. Can you get to a shell prompt?

---

### Post by HippoMan on 2005-12-01
I don't know if this will help, but I sometimes get this black screen with the white cursor after I log out from an X session on a perfectly well-installed Ubuntu system.  What I do in this case is to issue a Control-Shift-F8, wait a few seconds, and then issue a Control-Shift-F7.  The normal login screen then appears.

I'm guessing that this is due to some sort of race condition in the X-Window startup code, and that switching to a non-X getty and then back to the X getty gets the server back into a usable state.

Perhaps something like this will work for you ... ???

---

### Post by tcjudd on 2005-12-03
The white cursor I get on the screen does not 'flash' like the cursor I get on my AMD64 machine...there I can get to a prompt, edit xorg.conf and restart Gnome.  On this older machine it really seems to be hung up...I can't get to a prompt, get the sytem to logoff/shutdown, etc.  I end up having to go for the power switch, which is suspiciously like Win Mistake Edition that is on this machine's hd :rolleyes:

That said, editing the xorg.conf on the 64bit machine to change the video driver to VESA allows me to run startx and get right into Gnome.  Maybe that will work for some of you folks who actually have a flashing cursor here and not a completely locked up machine.  I think I'm about to punt on this older one and load BeatriX on it (which works great) and save Ubuntu for the newer box.

---

### Post by zeroknowledge on 2006-12-29
same situation here with the "live cd" installation.(ver.5.04)
after all question are answered the screen blanks and this text appears ... 
starting ubuntu ...
exec of '/sbin/init" failed: no such file or directory
system halted
the problem has been identical in three attempts.
the system locks up and a cold boot is required.

the hardware is known good because xp pro is currently running flawlessly.
hardware details ...
dfi ca64
p3 750
384 mb ram
32mb nv riva tnt2 model 64
8 gig fujitsu hdd
soundblaster
56k usr "isa" hardware modem
dlink dfe530tx nic
this whole exercise it to determine if the hardware is compatable with ubuntu. if so then i'm working towards a full install.
thanks and adios ... jimmy t.

---

### Post by unisol on 2006-12-29
i have almost the exact same system P3 750 384mb mem and a 80gb hd and installed dapper on it .maybe you should into safe graphics mode and try to install from there. maybe try the alternate-install cd

---

### Post by zeroknowledge on 2006-12-30
i will try a more current version and see if it works. i just need to find a friend with hi-speed.

---

