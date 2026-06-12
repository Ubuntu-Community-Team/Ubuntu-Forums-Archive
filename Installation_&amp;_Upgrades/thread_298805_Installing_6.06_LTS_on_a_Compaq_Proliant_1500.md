---
title: "Installing 6.06 LTS on a Compaq Proliant 1500"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by Smoothas on 2006-11-13
Hello,
I'm a Unix newbie and have been trying to install Ubuntu 6.06 on a Compaq proliant 1500.
I've trawled thought the threads and found some information about getting the unti ready for Ubuntu installation, and have followed those.
I've put the CD into the tray ( I requested the CD to be sent to me, rather that downloading the ISO )and the screen apears asking if I want to boot or goto the menu system.
I click ENTER to start the install, and I then get a message ( after an inital Lunix check) saying ACPI: UNABLE TO LOCATE RSDP.
There then apears some more code on the screen ( the last of it being KERNEL_THREAD_HELPER+0x5/0x10 ), and I then get a second "error" message saying <0> KERNAL PANIC - NOT SYNCING: ATTEMPED TO KILL INIT!, and a flashing cursor on the line below untill tuen the power off and on again.

I've tried noapic nolapic and the BOOT: prompt, but I get told that it cannot load noapic ( this happens with any "command" that I type here , except for the one to load using Expert mode ( Which I am FAR from ). This gives me the same "error" messages.
](*,) 

Any help gratefully received

Regards
Gerald

---

### Post by Smoothas on 2006-11-15
I've found out that RSDP = Root System Description Pointer (ACPI) , but I still don't know what that means :confused: , or why it woul dbe unable to locate it.

Any Ideas Anyone?

---

### Post by Smoothas on 2006-11-17
*** Update ***

I've downloaded the Server version and burned the ISO to disc.
I tried a normal boot, with the same error messages.
I then tried it with the command :_

Boot: install acpi=off

and the ACPI: UNABLE TO LOCATE RSDP message is not Displayed :D , however, the 0> KERNAL PANIC - NOT SYNCING: ATTEMPED TO KILL INIT! still is :( , any idea on how I can get passed this anyone ?

Thanks

---

### Post by Smoothas on 2006-11-17
***UPDATE***

I've installed a graphics card ( as I saw that the KERNAL error can be solved with a new graphics card ), but not joy.
Did get a different boot screen thought and managed to run memtest ( with no errors that I could see ).

I'm not sure if these post are actually getting to the thread, but I will keep updating it until I give up or get it to work ( depending on what happens first ) just incase anyone else has the same problems in the future.

---

### Post by sgrossma on 2006-12-18
Smoothas - I have a Proliant 4500 quad processor pentium 2 with 1 GB RAM and a SCSI RAID array.  I experience the same message and failure when I try to install 6.06 LTS.  I've tried a variety of parameters on the install, but the kernel panic still happens.  I was hopeful that turning off the ACPI options would help, so I've used pci=noacpi, noapic, nolapic, acpi=off and others, but still a failure.

Anybody out there yet been successful with this type of install on an old Compaq?

---

### Post by sgrossma on 2006-12-20
I tried some stuff yesterday and may have made a small amount of progress.  After reading the cpqlinux pages on the cpqarray driver [http://www.cpqlinux.com/lindrivers.html]("http://www.cpqlinux.com/lindrivers.html"), I tried booting with 
    "linux smart2=0x6000 mem=1024M"
I get a different kernel panic:
   Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown - block(1,0)

I also tried booting with
   "linux eisa=0x6000 mem=1024M"
and
   "linux smart2=0x6000 mem=1024M root=/dev/ida/c0d0p6"
but the results are similar, except that the unknown block changes to (0,0) rather than (0,1).

---

### Post by ghettobilly on 2006-12-30
its a problem thats easily fixed add mem=exactmap mem=640K@0 mem=143M@1M
to the boot prompt replace 143 with the amount of memory your system has -1M (example 256 would be 255) the error is from the linux only seeing 16M. here is a dmesg from my proliant 1500 running redhat 9 dual p5-166 compaq smart array 3200 with 17 9.1 scsi raid 5

cat /var/log/dmesg
Linux version 2.4.20-31.9smp (bhcompile@daffy.perf.redhat.com) (gcc version 3.2.2 20030222 (Red Hat Linux 3.2.2-5)) #1 SMP Tue Apr 13 17:10:42 EDT 2004
BIOS-provided physical RAM map:
 BIOS-88: 0000000000000000 - 000000000009f000 (usable)
 BIOS-88: 0000000000100000 - 0000000001000000 (usable)
user-defined physical RAM map:
 user: 0000000000000000 - 00000000000a0000 (usable)
 user: 0000000000100000 - 0000000009000000 (usable)
144MB LOWMEM available.
found SMP MP-table at 000f4ff0
hm, page 000f4000 reserved twice.
hm, page 000f5000 reserved twice.
hm, page 000f2000 reserved twice.
hm, page 000f3000 reserved twice.
On node 0 totalpages: 36864
zone(0): 4096 pages.
zone(1): 32768 pages.
zone(2): 0 pages.
Intel MultiProcessor Specification v1.1
    Virtual Wire compatibility mode.
OEM ID: COMPAQ   Product ID: PROLIANT     APIC at: 0xFEE00000
Processor #0 Pentium(tm) APIC version 16
Processor #1 Pentium(tm) APIC version 16
I/O APIC #2 Version 17 at 0xFEC00000.
I/O APIC #3 Version 17 at 0xFEC01000.
Enabling APIC mode: Flat.       Using 2 I/O APICs
Processors: 2
Kernel command line: auto BOOT_IMAGE=2.4.20-31.9smp ro BOOT_FILE=/boot/vmlinuz-2.4.20-31.9smp mem=exactmap mem=640K@0 mem=143M@1M root=LABEL=/
Initializing CPU#0
Detected 167.021 MHz processor.
Console: colour VGA+ 80x25
Calibrating delay loop... 332.59 BogoMIPS
Memory: 140500k/147456k available (1354k kernel code, 5420k reserved, 1066k data, 140k init, 0k highmem)
Dentry cache hash table entries: 32768 (order: 6, 262144 bytes)
Inode cache hash table entries: 16384 (order: 5, 131072 bytes)
Mount cache hash table entries: 512 (order: 0, 4096 bytes)
Buffer-cache hash table entries: 8192 (order: 3, 32768 bytes)
Page-cache hash table entries: 65536 (order: 6, 262144 bytes)
Intel Pentium with F0 0F bug - workaround enabled.
CPU:     After generic, caps: 000003bf 00000000 00000000 00000000
CPU:             Common caps: 000003bf 00000000 00000000 00000000
Checking 'hlt' instruction... OK.
POSIX conformance testing by UNIFIX
mtrr: v1.40 (20010327) Richard Gooch (rgooch@atnf.csiro.au)
mtrr: detected mtrr type: none
CPU:     After generic, caps: 000003bf 00000000 00000000 00000000
CPU:             Common caps: 000003bf 00000000 00000000 00000000
CPU0: Intel Pentium 75 - 200 stepping 0c
per-CPU timeslice cutoff: 159.91 usecs.
task migration cache decay timeout: 10 msecs.
enabled ExtINT on CPU#0
ESR value before enabling vector: 00000000
ESR value after enabling vector: 00000000
Booting processor 1/1 eip 2000
Initializing CPU#1
masked ExtINT on CPU#1
ESR value before enabling vector: 00000000
ESR value after enabling vector: 00000000
Calibrating delay loop... 333.41 BogoMIPS
CPU:     After generic, caps: 000003bf 00000000 00000000 00000000
CPU:             Common caps: 000003bf 00000000 00000000 00000000
CPU1: Intel Pentium 75 - 200 stepping 0c
Total of 2 processors activated (666.00 BogoMIPS).
ENABLING IO-APIC IRQs
Setting 2 in the phys_id_present_map
...changing IO-APIC physical APIC ID to 2 ... ok.
Setting 3 in the phys_id_present_map
...changing IO-APIC physical APIC ID to 3 ... ok.
init IO_APIC IRQs
 IO-APIC (apicid-pin) 2-0, 2-5, 2-14, 3-0, 3-8, 3-9, 3-10, 3-11, 3-12, 3-14, 3-15, 3-16, 3-17, 3-18, 3-19, 3-20, 3-21, 3-22, 3-23, 3-24, 3-25, 3-26, 3-27 not connected.
..TIMER: vector=0x31 pin1=2 pin2=-1
number of MP IRQ sources: 27.
number of IO-APIC #2 registers: 16.
number of IO-APIC #3 registers: 28.
testing the IO APIC.......................

IO APIC #2......
.... register #00: 02000000
.......    : physical APIC id: 02
.... register #01: 000F0011
.......     : max redirection entries: 000F
.......     : PRQ implemented: 0
.......     : IO APIC version: 0011
.... register #02: 00000000
.......     : arbitration: 00
.... IRQ redirection table:
 NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
 00 000 00  1    0    0   0   0    0    0    00
 01 0FF 0F  0    0    0   0   0    1    1    39
 02 0FF 0F  0    0    0   0   0    1    1    31
 03 0FF 0F  0    0    0   0   0    1    1    41
 04 0FF 0F  0    0    0   0   0    1    1    49
 05 000 00  1    0    0   0   0    0    0    00
 06 0FF 0F  0    0    0   0   0    1    1    51
 07 0FF 0F  0    0    0   0   0    1    1    59
 08 0FF 0F  0    0    0   0   0    1    1    61
 09 0FF 0F  1    1    0   0   0    1    1    69
 0a 0FF 0F  0    0    0   0   0    1    1    71
 0b 0FF 0F  0    0    0   0   0    1    1    79
 0c 0FF 0F  0    0    0   0   0    1    1    81
 0d 0FF 0F  0    0    0   0   0    1    1    89
 0e 000 00  1    0    0   0   0    0    0    00
 0f 0FF 0F  0    0    0   0   0    1    1    91

IO APIC #3......
.... register #00: 03000000
.......    : physical APIC id: 03
.... register #01: 001B0011
.......     : max redirection entries: 001B
.......     : PRQ implemented: 0
.......     : IO APIC version: 0011
.... register #02: 0D000000
.......     : arbitration: 0D
.... IRQ redirection table:
 NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
 00 000 00  1    0    0   0   0    0    0    00
 01 0FF 0F  1    1    0   1   0    1    1    99
 02 0FF 0F  1    1    0   1   0    1    1    A1
 03 0FF 0F  1    1    0   1   0    1    1    A9
 04 0FF 0F  1    1    0   1   0    1    1    B1
 05 0FF 0F  1    1    0   1   0    1    1    B9
 06 0FF 0F  1    1    0   1   0    1    1    C1
 07 0FF 0F  1    1    0   1   0    1    1    C9
 08 000 00  1    0    0   0   0    0    0    00
 09 000 00  1    0    0   0   0    0    0    00
 0a 000 00  1    0    0   0   0    0    0    00
 0b 000 00  1    0    0   0   0    0    0    00
 0c 000 00  1    0    0   0   0    0    0    00
 0d 0FF 0F  1    1    0   1   0    1    1    D1
 0e 000 00  1    0    0   0   0    0    0    00
 0f 000 00  1    0    0   0   0    0    0    00
 10 000 00  1    0    0   0   0    0    0    00
 11 000 00  1    0    0   0   0    0    0    00
 12 000 00  1    0    0   0   0    0    0    00
 13 000 00  1    0    0   0   0    0    0    00
 14 000 00  1    0    0   0   0    0    0    00
 15 000 00  1    0    0   0   0    0    0    00
 16 000 00  1    0    0   0   0    0    0    00
 17 000 00  1    0    0   0   0    0    0    00
 18 000 00  1    0    0   0   0    0    0    00
 19 000 00  0    0    0   0   0    0    6    FF
 1a 001 01  0    0    0   0   0    0    6    FF
 1b 001 01  0    0    0   0   0    0    5    FF
IRQ to pin mappings:
IRQ0 -> 0:2
IRQ1 -> 0:1
IRQ3 -> 0:3
IRQ4 -> 0:4
IRQ6 -> 0:6
IRQ7 -> 0:7
IRQ8 -> 0:8
IRQ9 -> 0:9
IRQ10 -> 0:10
IRQ11 -> 0:11
IRQ12 -> 0:12
IRQ13 -> 0:13
IRQ15 -> 0:15
IRQ17 -> 1:1
IRQ18 -> 1:2
IRQ19 -> 1:3
IRQ20 -> 1:4
IRQ21 -> 1:5
IRQ22 -> 1:6
IRQ23 -> 1:7
IRQ29 -> 1:13
.................................... done.
Using local APIC timer interrupts.
calibrating APIC timer ...
..... CPU clock speed is 167.0161 MHz.
..... host bus clock speed is 66.8062 MHz.
cpu: 0, clocks: 668062, slice: 222687
CPU0<T0:668048,T1:445360,D:1,S:222687,C:668062>
cpu: 1, clocks: 668062, slice: 222687
CPU1<T0:668048,T1:222672,D:2,S:222687,C:668062>
checking TSC synchronization across CPUs: passed.
Starting migration thread for cpu 0
smp_num_cpus: 2.
Starting migration thread for cpu 1
PCI: PCI BIOS revision 2.10 entry at 0xf005e, last bus=1
PCI: Using configuration type 1
PCI: Probing PCI hardware
PCI: device 00:00.0 has unknown header type 7f, ignoring.
PCI->APIC IRQ transform: (B0,I10,P0) -> 18
PCI->APIC IRQ transform: (B0,I12,P0) -> 22
PCI BIOS passed nonexistent PCI bus 1!
PCI: using PPB(B0,I14,P0) to get irq 29
PCI->APIC IRQ transform: (B1,I0,P0) -> 29
PCI: Device 00:78 not found by BIOS
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Linux NET4.0 for Linux 2.4
Based upon Swansea University Computer Society NET3.039
Initializing RT netlink socket
apm: BIOS not found.
Starting kswapd
VFS: Disk quotas vdquot_6.5.1
pty: 512 Unix98 ptys configured
Serial driver version 5.05c (2001-07-08) with MANY_PORTS MULTIPORT SHARE_IRQ SERIAL_PCI ISAPNP enabled
ttyS0 at 0x03f8 (irq = 4) is a 16550A
ttyS1 at 0x02f8 (irq = 3) is a 16550A
Real Time Clock Driver v1.10e
Floppy drive(s): fd0 is 1.44M
FDC 0 is a National Semiconductor PC87306
NET4: Frame Diverter 0.46
RAMDISK driver initialized: 16 RAM disks of 4096K size 1024 blocksize
Uniform Multi-Platform E-IDE driver Revision: 7.00beta3-.2.4
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ide-floppy driver 0.99.newide
ide-floppy driver 0.99.newide
md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
md: Autodetecting RAID arrays.
md: autorun ...
md: ... autorun DONE.
NET4: Linux TCP/IP 1.0 for NET4.0
IP Protocols: ICMP, UDP, TCP, IGMP
IP: routing cache hash table of 1024 buckets, 8Kbytes
TCP: Hash tables configured (established 16384 bind 16384)
Linux IP multicast router 0.06 plus PIM-SM
NET4: Unix domain sockets 1.0/SMP for Linux NET4.0.
RAMDISK: Compressed image found at block 0
Freeing initrd memory: 251k freed
VFS: Mounted root (ext2 filesystem).
SCSI subsystem driver Revision: 1.00
Compaq SMART2 Driver (v 2.4.25)
cpqarray: Device 0xae10 has been found at bus 1 dev 0 func 0
cpqarray: Finding drives on ida0 (Smart Array 3200)
cpqarray ida/c0d0: blksz=512 nr_blks=284350500
blk: queue c0400bc0, I/O limit 4095Mb (mask 0xffffffff)
Partition check:
 ida/c0d0: p1 p2 p3 p4 < p5 >
ncr53c8xx: at PCI bus 0, device 10, function 0
ncr53c8xx: 53c825 detected 
ncr53c825-0: rev 0x2 on pci bus 0 device 10 function 0 irq 18
ncr53c825-0: ID 7, Fast-10, Parity Checking
scsi0 : ncr53c8xx-3.4.3b-20010512
  Vendor: COMPAQ    Model: CD-ROM CR-503BCQ  Rev: 1.1i
  Type:   CD-ROM                             ANSI SCSI revision: 02
Journalled Block Device driver loaded
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Freeing unused kernel memory: 140k freed
EXT3 FS 2.4-0.9.19, 19 August 2002 on ida0(72,5), internal journal
Adding Swap: 265064k swap-space (priority -1)

---

### Post by sgrossma on 2007-06-15
Finally got back to this project.  booting with 
*install mem=exactmap mem=640K@0 mem=1023M@1M* 
doesn't get an error, but it doesn't do anything else, either.  It uncompresses everything, and then it says
*Uncompressing Linux... Ok, booting the kernel.*
and it stops there.  No error, no boot, no progress.

Any thoughts?

---

### Post by greyphi on 2007-09-05
While I don't have quite the same hardware setup, I have found a little trick to configure the smart controller.
Use dsl-knoppix 50meg live cd (kernel 2.4 seems to handle the proliant servers quite well) and enable apt-get as per the intro screen.

wget [http://24.64.108.198/home/hpacucli_7.20-17_i386.deb](http://24.64.108.198/home/hpacucli_7.20-17_i386.deb)

dpkg -i hpacucli_7.20-17_i386.deb

then just type "hpacucli" to start the command prompt for the array. (It's clunky but it works)
I read the help files and had the Raid 5 setup in a few minutes.
Then run your system configuration utility to make sure your smart controller is the first boot device.
At that point I was able to install deb-etch with no hassles

---

