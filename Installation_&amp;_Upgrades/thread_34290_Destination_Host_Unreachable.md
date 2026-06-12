---
title: "Destination Host Unreachable"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by twinky on 2005-05-14
Hello, Today I installed Ubuntu linux 5.04. During the installation I choosed option server (so only base packages was installed). My 3Com Etherlink III wasn't recognized during installation and because I found that this card isnt auto-detected ([https://site-edit.ubuntulinux.org/wiki/HardwareSupportComponentsWiredNetworkCards](https://site-edit.ubuntulinux.org/wiki/HardwareSupportComponentsWiredNetworkCards)) I continued installation.
After first boot I added 3c509 to /etc/modules and added those lines to /etc/network/interfaces

auto eth0
iface eth0 inet static
address 194.145.136.244
netmask 255.255.255.128
gateway 194.145.136.129

rebooted and pinged:

ping 194.145.136.129
PING 194.145.136.129 (194.145.136.129) 56(84) bytes of data.
From 194.145.136.244 icmp_seq=2 Destination Host Unreachable
From 194.145.136.244 icmp_seq=3 Destination Host Unreachable
From 194.145.136.244 icmp_seq=4 Destination Host Unreachable

$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:10:5A:4D:57:7E
          inet addr:194.145.136.244  Bcast:194.145.136.255  Mask:255.255.255.128
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1275 errors:0 dropped:0 overruns:0 carrier:2655
          collisions:1275 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1750 (1.7 KiB)
          Interrupt:5 Memory:0x220

$ route
Kernel IP routing table
Destination		Gateway		Genmask		Flags	Metrics	Ref	Use	Iface
194.145.136.128	*			255.255.255.128	U	0		0	0	eth0
default			194.145.136.129	0.0.0.0		UG	0		0	0	eth0

Why Destination Host Unreachable? Is it problem with card or with configuration? Card was working perfectly under Win2000.

When I switch this cable to another computer with Fedora Core with same ip & sm & gw configured i get these results:

[root@twinky sbin]# ping 194.145.136.129
PING 194.145.136.129 (194.145.136.129) 56(84) bytes of data.
64 bytes from 194.145.136.129: icmp_seq=0 ttl=64 time=1.82 ms
64 bytes from 194.145.136.129: icmp_seq=1 ttl=64 time=0.554 ms
64 bytes from 194.145.136.129: icmp_seq=2 ttl=64 time=0.557 ms

[root@twinky sbin]# ./route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
194.145.136.128 *               255.255.255.128 U     0      0        0 eth0
169.254.0.0     *               255.255.0.0     U     0      0        0 eth0
default         194.145.136.129 0.0.0.0         UG    0      0        0 eth0

[root@twinky sbin]# ./ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2F:DA:8A:17
          inet addr:194.145.136.244  Bcast:194.145.136.255  Mask:255.255.255.128
          inet6 addr: fe80::211:2fff:feda:8a17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:770107 (752.0 KiB)  TX bytes:179964 (175.7 KiB)
          Interrupt:177 Memory:fab00000-0

---

### Post by alastair on 2005-05-14
Not sure. The networking looks correctly configured. I have to wonder about the "carrier" field in system 1 though i.e.

TX packets:1275 errors:0 dropped:0 overruns:0 carrier:2655

System 2 (working) has :

TX packets:1405 errors:0 dropped:0 overruns:0 carrier:0

System 1 has a lot of collisions as well .... but this is normal in some situations (half-duplex? hub?)

The "carrier" field is some sort of "sum" of errors for TX carrier sense, abort, window or heartbeat errors (perhaps). So - usually cable or H/W issue. Perhaps driver problem.

I would :

a) compare the module load in /var/log/syslog (or messages) on both systems. Look at the driver version and messages (also compare kernel versions)

b) look at eth0 setup using something like "ethtool" on both systems i.e.

ethtool eth0

c) swap cable / port (on hub/switch)

---

### Post by nad on 2005-05-14
The definitive source for the open source driver:

[http://www.scyld.com/3c509.html](http://www.scyld.com/3c509.html)

" RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:1275 errors:0 dropped:0 overruns:0 carrier:2655
collisions:1275 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:1750 (1.7 KiB)
Interrupt:5 Memory:0x220 "

If you do not have two hosts with the same ip address, I would suspect an irq or duplex configuration problem.

---

### Post by twinky on 2005-05-14
On FC3
[root@twinky sbin]# ./ethtool eth0
Settings for eth0:
No data available

On UbuntuHH:
$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ ]
	Supported link modes:
	Supports auto-negotiation: No
	Advertised link modes: Not reported
	Advertised auto-negotiation: No
	Speed: 10Mb/s
	Duplex: Half
	Port: BNC
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: off
	Current message level: 0x00000002 (2)
	Link detected: yes

$ more messages
...
eth0: 3c5x9 found at 0x220, 10baseT port, address 00 10 5a 4d 57 7e, IRQ 5.
3c509.c:1.19b 08Nov2002 [email]becker@scyld.com[/email]
[http://www.scyld.com/network/3c509.html](http://www.scyld.com/network/3c509.html)
eth1: 3c5x9 found at 0x300, 10baseT port, address 00 10 5a 4d 57 fe, IRQ 10.
3c509.c:1.19b 08Nov2002 [email]becker@scyld.com[/email]
[http://www.scyld.com/network/3c509.html](http://www.scyld.com/network/3c509.html)
...
eth0: Setting 3c5x9/3c5x9B half-duplex mode if_port: 0, sw_info: 1321
eth0: Setting Rx mode to 1 addresses



I am sure I dont have same IP at the same time on those two computers.
Now I'm going to try changing port in the hub but I think this won't help.
I don't know why is there eth1 and I'm not using it...what is it for?  :roll:

---

### Post by nad on 2005-05-14
It certainly looks to be an irq conflict. irq5 and memory address 0x220 is typically used by a sound card.

However, you are also setup with eth1 at irq10! Have you tried using this address? (Is 0x300 a midi address?)

These older cards often required that a utility program be used to hard set an irq or pnp mode in the firmware. Please read the driver information. You may also try bios settings to force pnp mode.

---

### Post by twinky on 2005-05-14
I tryed adding same config for eth1 but it disapeared...so I commented that lines out and now I dont see eth1 also if I: ifconfig -a


Then I enabled PnP in bios and now I have:

$ ifconfig eth0
eth0 Link encap:Ethernet HWaddr 00:10:5A:4D:57:7E
inet addr:194.145.136.244 Bcast:194.145.136.255 Mask:255.255.255.128
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:26 errors:0 dropped:0 overruns:0 frame:0
TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:378 (378.0 b)
Interrupt:5 Memory:0x220

But still Destination Host Unreachable...

---

### Post by nad on 2005-05-14
RTFM!

From the fine manual:

"Special Driver Features

The 1.14 and later versions allow overriding the IOADDR, IRQ, and transceiver setting of detected cards. This capability should be rarely needed. The syntax for LILO parameters is

   ether=10,0x310,3,0x3c509,eth0

This configures the first found 3c509 card for IRQ 10, base I/O 0x310, and transceiver #3 (10base2). The flag "0x3c509" must be set to avoid conflicts with other card types when overriding the I/O address."

---

### Post by twinky on 2005-05-14
I saw that note in documentation but I didnt know it can be useful to me...

hmm I'm not sure I have lilo... when I go to /boot I see only grub dir and some other files ...

---

### Post by nad on 2005-05-14
OK

Let's see the ouptut of: cat /proc/interrupts
and: cat /proc/ioports

The boot options will be the same for grub as lilo.

---

### Post by twinky on 2005-05-14
interrupts

           CPU0       
  0:    3096001          XT-PIC  timer
  1:        523          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:          0          XT-PIC  eth0
  7:          1          XT-PIC  parport0
  8:          1          XT-PIC  rtc
  9:          0          XT-PIC  acpi, uhci_hcd
 12:        489          XT-PIC  i8042
 14:       1967          XT-PIC  ide0
 15:         27          XT-PIC  ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0

ioports

0000-001f : dma1
0020-0021 : pic1
0040-0043 : timer0
0050-0053 : timer1
0060-006f : keyboard
0070-0077 : rtc
0080-008f : dma page reg
00a0-00a1 : pic2
00c0-00df : dma2
00f0-00ff : fpu
0170-0177 : ide1
01f0-01f7 : ide0
0213-0213 : ISAPnP
0220-022f : 3c509 PnP
02f8-02ff : serial
0300-030f : 3c509
0376-0376 : ide1
0378-037a : parport0
037b-037f : parport0
03c0-03df : vga+
03f6-03f6 : ide0
03f8-03ff : serial
0778-077a : parport0
0a79-0a79 : isapnp write
0cf8-0cff : PCI conf1
1000-100f : 0000:00:07.1
  1000-1007 : ide0
  1008-100f : ide1
1020-103f : 0000:00:07.2
  1020-103f : uhci_hcd
7000-701f : 0000:00:07.3
  7000-700f : motherboard
    7000-700f : pnp 00:06
      7000-7007 : piix4-smbus
8000-803f : 0000:00:07.3
  8000-803f : motherboard
    8000-8003 : PM1a_EVT_BLK
    8004-8005 : PM1a_CNT_BLK
    8008-800b : PM_TMR
    800c-800f : GPE0_BLK
    8010-8015 : ACPI CPU throttle
9000-9fff : PCI Bus #01
  9000-90ff : 0000:01:00.0

---

### Post by nad on 2005-05-14
Do you have sound hardware in this machine?

There are a few ways to try this, either way you need to append the ether configuration line to your grub boot command.

At the grub boot menu, press 'e' to edit the grub command line. Add: 

ether=5,0x220,4,0x3c509,eth0

all on one line (no spaces) to use interrupt# 5, the 0220 base address and the 10baseT transceiver type (you are using an rj45 connector?).

The only thing I see that could be causing problems is your transceiver type (provided that you do not have an isa sound card that is not being recognized).

This will only work for this boot. To make it permanent, add the boot command to the menu.lst line that begins kopt  and run: update-grub .

---

### Post by twinky on 2005-05-14
You are right, I have a soundcard there, when I put it away it works perfectly... you are geek. I tryed also to manage to work them both together by doing what you suggested, but I think I'm giving that line in wrong position...here is what I did:


root  (hd0,0)
kernel  /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd  /boot/initrd.img-2.6.10-5-386
savedefault
boot
ether=5,0x220,4,0x3c509,eth0

and

root  (hd0,0)
kernel  /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd  /boot/initrd.img-2.6.10-5-386
savedefault
boot
ether=10,0x310,3,0x3c509,eth0

without any success...

---

### Post by nad on 2005-05-14
Put that line here:

kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash ether=10,0x310,4,0x3c509,eth0

and try it.

---

### Post by twinky on 2005-05-14
hmm i already tryed before you post with line

kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash ether=10,0x310,3,0x3c509,eth0

and after you post with line:

kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash ether=10,0x310,4,0x3c509,eth0

no one works

---

### Post by nad on 2005-05-14
Review the output of those two commands I gave you again and run the command: dmesg | less  to review the output of the startup kernel log for any errors or messages regarding eth0 and sound hardware.

---

### Post by twinky on 2005-05-14
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
 BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e7400 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 00000000040fdc00 (usable)
 BIOS-e820: 00000000040fdc00 - 00000000040ff800 (ACPI data)
 BIOS-e820: 00000000040ff800 - 00000000040ffc00 (ACPI NVS)
 BIOS-e820: 00000000040ffc00 - 000000000c000000 (usable)
 BIOS-e820: 00000000fffe7400 - 0000000100000000 (reserved)
192MB LOWMEM available.
On node 0 totalpages: 49152
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 45056 pages, LIFO batch:11
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.1 present.
ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6e90
ACPI: RSDT (v001 PTLTD    RSDT   0x00000000 PTL  0x01000000) @ 0x040fdc09
ACPI: FADT (v001 INTEL  ATLANTA  0x19990416 PTL  0x000f4240) @ 0x040ff78c
ACPI: DSDT (v001  Intel   Atlant 0x00000000 MSFT 0x0100000b) @ 0x00000000
ACPI: PM-Timer IO Port: 0x8008
Built 1 zonelists
**Kernel command line: root=/dev/hda1 ro quiet splash ether=10,0x310,4,0x3c509,eth0**
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (01183000)
Initializing CPU#0
PID hash table entries: 1024 (order: 10, 16384 bytes)
Detected 333.058 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Memory: 187420k/196608k available (1436k kernel code, 8648k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 659.45 BogoMIPS (lpj=329728)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 512K
CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000
CPU: Intel Pentium II (Deschutes) stepping 00
Enabling fast FPU save and restore... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0a00)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4248k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfd9c4, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 12 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
pnp: 00:06: ioport range 0x7000-0x700f has been reserved
pnp: 00:06: ioport range 0x8000-0x803f could not be reserved
audit: initializing netlink socket (disabled)
audit(1116109634.948:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Limiting direct PCI/PCI transfers.
isapnp: Scanning for PnP cards...
isapnp: Card '3Com 3C509B EtherLink III'
isapnp: 1 Plug & Play card detected total
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
pnp: Device 00:0b activated.
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 7
Cannot allocate resource for EISA slot 8
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 2048 buckets, 16Kbytes
TCP: Hash tables configured (established 16384 bind 32768)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices: 
PCI0 USB0 UAR1 COMB 
ACPI: (supports S0 S1 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... 
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: Fan [FAN] (on)
ACPI: CPU0 (power states: C1[C1] C2[C2])
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
PIIX4: IDE controller at PCI slot 0000:00:07.1
PIIX4: chipset revision 1
PIIX4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x1000-0x1007, BIOS settings: hda:pio, hdb:DMA
    ide1: BM-DMA at 0x1008-0x100f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: WDC AC34300L, ATA DISK drive
hdb: QUANTUM FIREBALLlct10 10, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 8406720 sectors (4304 MB) w/256KiB Cache, CHS=8896/15/63, UDMA(33)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
hdb: max request size: 128KiB
hdb: 20044080 sectors (10262 MB) w/418KiB Cache, CHS=19885/16/63, UDMA(33)
hdb: cache flushes not supported
 /dev/ide/host0/bus0/target1/lun0: p1
Probing IDE interface ide1...
hdc: CD-540E, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory...  -\|/done (455 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 208804k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdc: ATAPI 40X CD-ROM drive, 128kB Cache
Uniform CD-ROM driver Revision: 3.20
pnp: Device 00:0a activated.
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: GenPS/2 Genius Wheel Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
pnp: Device 01:01.00 activated.
[B]eth0: 3c5x9 found at 0x220, 10baseT port, address  00 10 5a 4d 57 7e, IRQ 5.
3c509.c:1.19b 08Nov2002 [email]becker@scyld.com[/email]
[http://www.scyld.com/network/3c509.html](http://www.scyld.com/network/3c509.html)
eth1: 3c5x9 found at 0x300, 10baseT port, address  00 10 5a 4d 57 fe, IRQ 10.
3c509.c:1.19b 08Nov2002 [email]becker@scyld.com[/email]
[http://www.scyld.com/network/3c509.html](http://www.scyld.com/network/3c509.html)[/B]
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a National Semiconductor PC87306
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 440LX Chipset.
agpgart: Maximum main memory to use for agp memory: 150M
agpgart: AGP aperture is 64M @ 0xf4000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
PCI: Enabling device 0000:00:07.2 (0004 -> 0005)
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
PCI: setting IRQ 9 as level-triggered
ACPI: PCI interrupt 0000:00:07.2[D] -> GSI 9 (level, low) -> IRQ 9
uhci_hcd 0000:00:07.2: Intel Corp. 82371AB/EB/MB PIIX4 USB
uhci_hcd 0000:00:07.2: irq 9, io base 0x1020
uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[B]eth0: Setting 3c5x9/3c5x9B half-duplex mode if_port: 0, sw_info: ffff
eth0: Setting Rx mode to 1 addresses.[/B]

I went throught this 3 times and I didn't found anything mentioning sound card (it is btw SB AWE32) I am not so much experienced with irqs so I could found only things which I bolded including no errors.

Also I'm not sure if appending that line (in grub) made any change.

---

### Post by nad on 2005-05-14
You could change the address in the boot line to 0x300, but, I'm afraid that this card is not playing nicely with the sound card. If you wish, you could download and use the 3com dos utility for configuring the firmware on the card. Other than forcing some irq options from the boot line or bios, my only other suggestion would be that you purchase a modern nic for $10-15 and avoid any further headache.

---

### Post by twinky on 2005-05-15
That computer will be just a server, so I'll put out that soundcard.   ;-)  Anyway I must say that I learned a lot and I would like to thank you for your kind help.

---

### Post by nad on 2005-05-15
You're welcome.

---

