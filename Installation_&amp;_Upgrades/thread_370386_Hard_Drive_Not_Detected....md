---
title: "Hard Drive Not Detected..."
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by trogex on 2007-02-25
I've attempted to install Ubuntu 6.10 here and when I get to detecting the hard drive and choosing/creating partitions, it doesn't detect the device. The hard drive is a 320GB Seagate (SATA 3GB, 7200RPM, 16MB Cache). It is currently partitioned into 4 partitions, one with my Windows XP installation, one intended for Ubuntu, etc.

Any reason why it's not detecting the drive?

---

### Post by Kateikyoushi on 2007-02-25
Which motherboard, SATA controller do you use ?

---

### Post by trogex on 2007-02-25
I'm using the ASUS M2R32-MVP, Jmicron360 SATA controller

---

### Post by amulchinock on 2007-02-26
> **trogex said:**
> I've attempted to install Ubuntu 6.10 here and when I get to detecting the hard drive and choosing/creating partitions, it doesn't detect the device. The hard drive is a 320GB Seagate (SATA 3GB, 7200RPM, 16MB Cache). It is currently partitioned into 4 partitions, one with my Windows XP installation, one intended for Ubuntu, etc.

Any reason why it's not detecting the drive?
I'm having the same problem; I Ubuntu won't pick up my hard drive.
There is no other operating system installed, so I can't go on the web to download new drivers .etc
Plus, to make matters worse; I have no idea what make my mother board or what drivers I am using.

HELP!

Thanks :)

---

### Post by ricflomag on 2007-03-01
Same problem here: Edgy LiveCD boots up all right, install process begins, but the disc partitioner says: No devices detected (and of course, the step before does not give me other choice than "manually edit partitions table").

Brand new DELL Inspiron 1501. Windows XP OEM installed and working.

#sudo lspci -vv
[...]
00:14.1 IDE interface: ATI Technologies Inc Unknown device 438c (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 01f5
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 217
        Region 0: I/O ports at <ignored>
        Region 1: I/O ports at <ignored>
        Region 2: I/O ports at <unassigned>
        Region 3: I/O ports at <unassigned>
        Region 4: I/O ports at 8420 [size=16]
        Capabilities: [70] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
[...]

The "device administrator" GUI program shows : 

Unknown (0x438c)
     -> IDE device (master)
          -> <the optical disc drive>

But nothing more below, where we would expect to see the hard drive...

Any help greatly appreciated ;)

---

### Post by ricflomag on 2007-03-01
Found a solution. On boot, I added :

pci=nomsi

to the kernel command line (press F6 to get it)

That's all. The drive is detected now.

---

