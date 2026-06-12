---
title: "Western digital Scorpio drive and karmic"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tom.swartz07 on 2009-10-16
Hi everyone

I'm trying to install karmic on my dual boot system, and it doesn't seem to recognize my hard drive. I have a 320 gig WD Scorpio blue series. Anyone know what driver from the live cd this uses?

EDIT:

Since the problem is solved, Im editing this post to serve as a guide.

The HDD was not recognized in the Live CD because of a problem with the BIOS. Normally a setting would be changed for the hard drive in ATA mode, but it was not there. After I installed the newest version of the BIOS, the Live CD worked fine.

Second problem was WiFi; If the drivers are not listed, and you cannot get online, insert the Live CD and enable it for use under System/Administration/Software Sources. There will be an option at the bottom of the first tab to use the Live CD for Installation purposes.

Lastly; on 2+ OS systems, (running Vista and Jaunty, in this case) you will need to make sure that your partitions have enough room to expand for another OS (Karmic, in this case). It is simply a matter of being able to move an extended partition out with gparted so that the new OS can fit.

Hope this helps! Thanks to everyone that posted here for all of the help and advice

---

### Post by tgalati4 on 2009-10-16
I dual boot with XP and Jaunty on an ibm t43p.  It's a fast drive.  Check the bios.

---

### Post by tom.swartz07 on 2009-10-16
> **tgalati4 said:**
> I dual boot with XP and Jaunty on an ibm t43p.  It's a fast drive.  Check the bios.

I'm sorry- I don't quite understand your reply. I'm literally sitting here with the 9.10 beta installer on the driver selection screen; is there a driver in this list that I am to use, or do I need to download an other one from WD's site?

---

### Post by CharlesA on 2009-10-16
It's not the drive that's the problem persay, it's the drive controller (PATA/SATA/RAID) on the mobo that needs a driver for the installer to see it.

What's yer mobo?

---

### Post by tom.swartz07 on 2009-10-16
For example: some drivers listed are;
3w-9xxx
3w-xxxx
buslogic
dac960
bpck
ch
eata
fit2
fit3
imm
qlogic_cs
scsi_tgt
umem

I'm afraid that if I randomly pick one, it'll brick my new drive.

---

### Post by rb0171610 on 2009-10-16
> **tom.swartz07 said:**
> Hi everyone

I'm trying to install karmic on my dual boot system, and it doesn't seem to recognize my hard drive. I have a 320 gig WD Scorpio blue series. Anyone know what driver from the live cd this uses?
[[IMG]https://www.wdc.com/global/images/products/img2/300/wdfScorpioBlue_BEVT.jpg[/IMG]]("javascript:openAnyWindow('/global/products/imageviewer.asp?model=wdfScorpioBlue_BEVT&filter=1534&currentimage=img2','image',440,505);")[IMG]https://www.wdc.com/global/images/products/img2/50/wdfScorpioBlue_BEVT.jpg[/IMG][IMG]https://www.wdc.com/global/images/products/img6/50/wdfScorpioBlue_BEVT.jpg[/IMG][IMG]https://www.wdc.com/global/images/products/img1/50/wdfScorpioBlue_BEVT.jpg[/IMG][IMG]https://www.wdc.com/global/images/products/img8/50/wdfScorpioBlue_BEVT.jpg[/IMG][IMG]https://www.wdc.com/global/images/products/img3/50/wdfScorpioBlue_BEVT.jpg[/IMG][IMG]https://www.wdc.com/global/images/products/img7/50/wdfScorpioBlue_BEVT.jpg[/IMG][[IMG]https://www.wdc.com/global/images/buttons/en/3DView_btn.gif[/IMG]]("javascript:openAnyWindow('../flash/index.asp?family=wdfScorpioBlue_BEVT','image',500,500);")
WD Scorpio Blue
Mobile Hard Drives
**320 GB, SATA 3 Gb/s, 8 MB Cache, 5400 RPM**

Big capacity for portable computing.

WD Scorpio Blue 2.5-inch drives offer high-performance, low power consumption and cool operation, making them ideal for notebooks and other portable devices. 
 Is this an internal hard drive? or external?

---

### Post by tom.swartz07 on 2009-10-16
> **CharlesA said:**
> It's not the drive that's the problem persay, it's the drive controller (PATA/SATA/RAID) on the mobo that needs a driver for the installer to see it.

What's yer mobo?


I'm not sure- how do I find out? What exactly is a mobo?

---

### Post by rb0171610 on 2009-10-16
> **tom.swartz07 said:**
> For example: some drivers listed are;
3w-9xxx
3w-xxxx
buslogic
dac960
bpck
ch
eata
fit2
fit3
imm
qlogic_cs
scsi_tgt
umem

I'm afraid that if I randomly pick one, it'll brick my new drive.
you can try all of those, they may not work.  You will not brick your drive.  The worst thing that will happen is that it will not be the one that will work for your drive.  The best thing that will happen is that it will allow you to see your drive.  Do not worry.

---

### Post by CharlesA on 2009-10-16
> **tom.swartz07 said:**
> I'm not sure- how do I find out? What exactly is a mobo?

I'm guessing it's a laptop, since you're probably using the mobile drive that Rob posted.

What brand of machine?

---

### Post by rb0171610 on 2009-10-16
> **tom.swartz07 said:**
> I'm not sure- how do I find out? What exactly is a mobo?
I think he is trying to say motherboard. In other words, he is asking you to check the bios to see if the device is actually enabled or at the least detected.  If the hard drive came with the computer or you had Windows previously, then it likely is by default.

---

### Post by P4man on 2009-10-16
is it not recognizing the harddrive, or not reading/mounting the partition?
Open a terminal and type 

```
sudo fdisk -l
```

doesn't it show up there?

If it doesnt, please post the output of "lspci -v".

---

### Post by rb0171610 on 2009-10-16
> **tom.swartz07 said:**
> I'm sorry- I don't quite understand your reply. I'm literally sitting here with the 9.10 beta installer on the driver selection screen; is there a driver in this list that I am to use, or do I need to download an other one from WD's site?
You might try this solution from the following thread:
[http://ubuntuforums.org/archive/index.php/t-507373.html](http://ubuntuforums.org/archive/index.php/t-507373.html)

July 31st, 2007, 12:28 AM
Go into your bios and go to Integrated Peripherals->Onchip Sata Device. Look at the OnChip
Sata Mode.
It is probably set to IDE by default and windows is happy to work with that mode. However
the latest Linux kernels prefer it to be set to the more advanced AHCI mode.
The trouble is that if you change it now, you will find Ubuntu boot works better but probably
Windows won't boot until you change it back again.
   onlyconnect
July 31st, 2007, 10:08 AM


Thanks, that appears to have fixed my RAID problem too.

---

### Post by tom.swartz07 on 2009-10-16
> **CharlesA said:**
> I'm guessing it's a laptop, since you're probably using the mobile drive that Rob posted.

What brand of machine?

Dell ispiron 1521- I just upgraded to that drive mentioned. I'll run through the list and see what works I guess? It the internal version- 320 gigs. It certainly is faster than the old one 

Yes the drive is detected by bios- I could boot to windows and jaunty no problem- that's why I find it so strange that it's "not detected"

---

### Post by rb0171610 on 2009-10-16
> **tom.swartz07 said:**
> Dell ispiron 1521- I just upgraded to that drive mentioned. I'll run through the list and see what works I guess? It the internal version- 320 gigs. It certainly is faster than the old one 

Yes the drive is detected by bios- I could boot to windows and jaunty no problem- that's why I find it so strange that it's "not detected"
I had a similar problem in the past, upgrading my Ubuntu and drive was not detected during installation.  I do not recall the exact solution in my scenario offhand.  Sorry.

---

### Post by tom.swartz07 on 2009-10-16
> **rb0171610 said:**
> I had a similar problem in the past, upgrading my Ubuntu and drive was not detected during installation.  I do not recall the exact solution in my scenario offhand.  Sorry.

Anyone know a workaround?

---

### Post by P4man on 2009-10-16
dont like repeating myself, but pls post output of

```
sudo fdisk -l
```

and

```
lspci -v
```

---

### Post by tom.swartz07 on 2009-10-16
> **P4man said:**
> dont like repeating myself, but pls post output of

```
sudo fdisk -l
```

and

```
lspci -v
```

My Bad- I didnt see your post....

```
tom@ubuntu-laptop:~$ sudo fdisk -l
[sudo] password for tom: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1315       11904    85064175    7  HPFS/NTFS
/dev/sda4           11905       29676   142753590    f  W95 Ext'd (LBA)
/dev/sda5           22653       22978     2618595   dd  Unknown
/dev/sda6           11905       22143    82244704+  83  Linux
/dev/sda7           22144       22652     4088511   82  Linux swap / Solaris

Partition table entries are not in disk order
tom@ubuntu-laptop:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fe900000-feafffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Memory behind bridge: fe800000-fe8fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe600000-fe7fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 6eb0 [size=8]
	I/O ports at 6eb8 [size=4]
	I/O ports at 6ec0 [size=8]
	I/O ports at 6ec8 [size=4]
	I/O ports at 6ee0 [size=16]
	Memory at fec01000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at ffb00000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at ffb01000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at ffb02000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at ffb03000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at ffb04000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
	Memory at ffa80000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
	Subsystem: Dell Device 01fc
	Flags: 66MHz, medium devsel
	I/O ports at 10c0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Dell Device 01fc
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	Memory behind bridge: fe500000-fe5fffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
	Subsystem: Dell Device 01fc
	Flags: bus master, fast devsel, latency 64, IRQ 19
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at ee00 [size=256]
	Memory at fea00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Device 01fc
	Flags: bus master, fast devsel, latency 64, IRQ 21
	Memory at fe5fe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: b44
	Kernel modules: b44

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: Dell Device 01fc
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at fe5fd800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
	Subsystem: Dell Device 01fc
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fe5fd400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Dell Device 01fc
	Flags: bus master, medium devsel, latency 64, IRQ 7
	Memory at fe5fd500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ricoh-mmc
	Kernel modules: ricoh_mmc

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Dell Device 01fc
	Flags: bus master, medium devsel, latency 64, IRQ 7
	Memory at fe5fd600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
	Subsystem: Dell Device 0007
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe8fc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb


```

---

### Post by P4man on 2009-10-16
clearly (and as I suspected) your harddisk is "detected", so scratch all the above suggestions.

Now Im not sure what the *real* problem is, are the partitions not mounted? Not visible in partition editor? What are you trying to achieve?

---

### Post by tom.swartz07 on 2009-10-16
> **P4man said:**
> clearly (and as I suspected) your harddisk is "detected", so scratch all the above suggestions.

Now Im not sure what the *real* problem is, are the partitions not mounted? Not visible in partition editor? What are you trying to achieve?

I'm trying to install karmic onto my system. I have jaunty, and I want to install side by side so that I could copy the files needed without having to cram up my external drive (which is nearly full already). After I install karmic, verify that everything is working, I'm going to delete the jaunty partition. It's simple in theory, but I cannot figure out why karmic will not "see" my hdd for the instalation.

---

### Post by tom.swartz07 on 2009-10-16
If it's any help, the hdd activity light is consistantly on when it gets to the step of "detecting hard drives"

---

### Post by CharlesA on 2009-10-16
> **tom.swartz07 said:**
> If it's any help, the hdd activity light is consistantly on when it gets to the step of "detecting hard drives"

Does the light go off after a while?

---

### Post by P4man on 2009-10-16
> **tom.swartz07 said:**
> If it's any help, the hdd activity light is consistantly on when it gets to the step of "detecting hard drives"

lets try and be clear;  are you talking about the ubiquiti (the OS installation program), gparted (partition editor) or the bootup process ?

If its in ubiquiti, try launching gparted from a terminal.

You could also try booting a jaunty live cd/stick if you still have one, and if that works, make it check the harddrive. Your partition table looks slightly weird to me (the extended partition looks different on my machines, and then the unknown partition?).

One way or another, the problem is not the harddisk as such, its the partitioning that seems to confuse karmic.

---

### Post by tom.swartz07 on 2009-10-16
> **CharlesA said:**
> Does the light go off after a while?

nope. not at all.

Its really strange. Ive never seen a problem like this before!
I tried all of the drivers listed and none of them helped. There were a few that allowed me to look at the drive, but it wouldnt load the partitions or anything. (not good)

---

### Post by tom.swartz07 on 2009-10-16
> **P4man said:**
> lets try and be clear;  are you talking about the ubiquiti (the OS installation program), gparted (partition editor) or the bootup process ?

If its in ubiquiti, try launching gparted from a terminal.

You could also try booting a jaunty live cd/stick if you still have one, and if that works, make it check the harddrive. Your partition table looks slightly weird to me (the extended partition looks different on my machines, and then the unknown partition?).

One way or another, the problem is not the harddisk as such, its the partitioning that seems to confuse karmic.

I specifically made the extended partition as you see so that I could install karmic on the drive. The limit of 4 primary partitions caught up with me finally, so I 'extended' the Extended partition for room; routine.

As far as where it gets caught up, this is what I do exactly;
[LIST]
[*]I downloaded the karmic beta x64 for my system
[*]burnt it to a disc.
[*]used gparted live cd to extend my partition for room.
[*]swapped gparted for karmic install disc
[*]boot to cd, hit enter for language, install on system
[*]enter past the keyboard, cancel the network config- (university needs flash for cisco clean access)
[*]name the computer 
[*]then it run into the problem with determining the hard drive
[/LIST]

There seems to be no rhyme or reason for the error, and I have verified the image with checksums, and run the built in disc checker.

Like I said before, I would like to keep my jaunty partition as intact as possible until the final release of karmic, so that I have a stable work system, after karmic is released, im perfectly fine with doing a clean install. Its just that I dont understand why it refuses to see my drive!

---

### Post by tom.swartz07 on 2009-10-16
How hard would it be to do a 'clean slate' install- wipe the partitions used for linux, and install them fresh for the new distro? Would the same error occur? 

There are no drivers listed on WD's website, nor are there any other mentions of this problem occurring here on the forums. 

I might have just gotten a fluke download of Karmic. Ill try the torrents.

---

### Post by P4man on 2009-10-16
so the fdisk output you posted was generated in jaunty?

Well, if Karmic isnt even booting from cd, then try checking the cd for errors (its an option in the first menu you get from the cd). A live cd doesn't even need to read to harddrive, and should boot regardless if can or cant read it, so its kinda weird... otoh, live cd's do mount a swap partition if they find any

But you really dont need any drivers or anything. Its either a faulty karmic disc, or a problem in the partition table (real or not) that makes karmic choke, perhaps trying to mount the swap partition.

---

### Post by tgalati4 on 2009-10-17
Burn a new karmic disc.  Checksum the disk with md5sum; compare with the repo.  Boot from the new cd.  Run in a terminal:

sudo cfdisk /dev/sda

Check and write down your partitions.   Write the partition table.   Reboot, run the installer and select the correct partition.  You should try ext4 for karmic--maybe that is what it is looking for.

If that doesn't work then wipe the linux and swap partitions and  install to free space.

You will need separate swap partitions for 32 bit and 64 bit.

---

### Post by tom.swartz07 on 2009-10-17
Great news and bad news-
I'm finally able to boot into the desktop on the live cd. BUT it still does not recognize the drive. 

I would post the output of the 2 previous commands, but I am unable to activate my restricted driver for my wireless card. What is the password to enable this? AKA the root password for karmic on live cd?

I'm so close to solving this I could almost taste it! Just a little more!

---

### Post by P4man on 2009-10-17
There is no password,just hit enter when it asks you one.

---

### Post by mdurham on 2009-10-17
> **tgalati4 said:**
> You will need separate swap partitions for 32 bit and 64 bit.

Why would that be?

---

### Post by forumache on 2009-10-17
> **mdurham said:**
> Why would that be?

I guess it will be necessary only if you hibernate one 32 bit Linux, then boot the 64 bit, it will see the resume info on swap partition and it will try to resume by loading the memory image from there => will not work (64 bit kernel with 32 bit process space). Same problem the other way round.

Other than that I see no reason for two swap partitions.

---

### Post by mdurham on 2009-10-17
> **forumache said:**
> I guess it will be necessary only if you hibernate one 32 bit Linux, then boot the 64 bit, it will see the resume info on swap partition and it will try to resume by loading the memory image from there => will not work (64 bit kernel with 32 bit process space). Same problem the other way round.

Other than that I see no reason for two swap partitions.

Hey, that's a clever thought, is it possible to hibernate and then reboot? I have no experience at all with hibernation.
Cheers, Mike

---

### Post by tom.swartz07 on 2009-10-17
K I think I may have been able to trace at least the possible cause of the HDD not showing in the live cd. When the live cd begins the preload- and normal messages about bootup appear (at least on my system, bits not cleared by bios, etc) there is another message that appears. 

```
ata1: exception Emask 0x40 SAct 0x0 SErr 0x400800 action 0x7 t4
ata1: SErr: {HostInt handshk }
```
it appears 5 times then says: " EH pending after 5 tries, giving up" then it finishes booting to the desktop. 

I should also note that just before each of the "tries" the disk activity light flashes but from that point on, it stays lit continuously. 

Anyone able to provide insight to this?
I'll post output of the terminal commands in a moment.

---

### Post by tom.swartz07 on 2009-10-17
Ok. 
Sudo fdisk -l returns absolutely no output
```


tom@ubuntu-laptop:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fe900000-feafffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Memory behind bridge: fe800000-fe8fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe600000-fe7fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 6eb0 [size=8]
	I/O ports at 6eb8 [size=4]
	I/O ports at 6ec0 [size=8]
	I/O ports at 6ec8 [size=4]
	I/O ports at 6ee0 [size=16]
	Memory at fec01000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at ffb00000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at ffb01000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at ffb02000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at ffb03000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at ffb04000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
	Memory at ffa80000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
	Subsystem: Dell Device 01fc
	Flags: 66MHz, medium devsel
	I/O ports at 10c0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Dell Device 01fc
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Dell Device 01fc
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	Memory behind bridge: fe500000-fe5fffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
	Subsystem: Dell Device 01fc
	Flags: bus master, fast devsel, latency 64, IRQ 19
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at ee00 [size=256]
	Memory at fea00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Device 01fc
	Flags: bus master, fast devsel, latency 64, IRQ 21
	Memory at fe5fe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: b44
	Kernel modules: b44

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: Dell Device 01fc
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at fe5fd800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
	Subsystem: Dell Device 01fc
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fe5fd400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Dell Device 01fc
	Flags: bus master, medium devsel, latency 64, IRQ 7
	Memory at fe5fd500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ricoh-mmc
	Kernel modules: ricoh_mmc

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Dell Device 01fc
	Flags: bus master, medium devsel, latency 64, IRQ 7
	Memory at fe5fd600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
	Subsystem: Dell Device 0007
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe8fc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb

```

---

### Post by b0b138 on 2009-10-17
Go into the bios. I'm not sure exactly what screen, but somewhere there's an option for the disks to be ahci or ata. Change it to ata if it's not already selected.

oh, forgot I had my friends 1720 laptop. The bios' should be very close.  On mine its under onboard devices - sata operation

---

### Post by tom.swartz07 on 2009-10-17
> **b0b138 said:**
> Go into the bios. I'm not sure exactly what screen, but somewhere there's an option for the disks to be ahci or ata. Change it to ata if it's not already selected.

oh, forgot I had my friends 1720 laptop. The bios' should be very close.  On mine its under onboard devices - sata operation

Thanks for the reply, but my bios has no such option. It lists the hdd under device info, but there are only options for "integrated nic, external USB, media cards and 1394 (FireWire) and module bay device" 

I have the factory default Dell bios revision a00 (5/16/07)

this is really starting to bother me.

---

### Post by tom.swartz07 on 2009-10-17
Ok,

Im abandoning the idea of using the install cd to get Karmic onto my harddrive.

Is there another installation method that I could use, besides the Live CD?

---

### Post by b0b138 on 2009-10-18
> **tom.swartz07 said:**
> I have the factory default Dell bios revision a00 (5/16/07)

Ok....assuming you looked through every part of the bios for sata operation, I would next suggest updating the bios.  Dell shows  version A06 2/18/08 as the most current for the 1521.

---

### Post by tom.swartz07 on 2009-10-18
From the download and installation instructions from Dell...
> Run the BIOS update utility from Windows environment


Double click the Icon on your desktop labeled 1521_A06.EXE.
The Dell BIOS Flash window appears


Click the Continue button.
The message Pressing OK will close all applications, shut down Windows, Flash the BIOS, then reboot. appears.


Click the OK button.
The system will restart and the BIOS Flash will be completed

Is it really that easy?
There has to be a catch...

---

### Post by b0b138 on 2009-10-18
lol  yup that easy.

---

### Post by tom.swartz07 on 2009-10-18
THAT DID IT! The live cd now recognizes the hdd. Trying the install now.

---

### Post by tom.swartz07 on 2009-10-18
Awesome. It installed! Ok- one last problem and thread is solved- on the live Cd, it allowed me to use the restricted driver for my wireless card, now after installation of bios and karmic, the wireless isn't working. The wifi light isn't even lit, toggling switch doesn't help either. I'll look on dells site for wireless driver maybe?

---

### Post by b0b138 on 2009-10-18
> **tom.swartz07 said:**
> THAT DID IT! The live cd now recognizes the hdd. Trying the install now.

awesome!!

check the bios. the update might have wireless off by default

---

### Post by tom.swartz07 on 2009-10-18
> **b0b138 said:**
> awesome!!

check the bios. the update might have wireless off by default

Nope- I looked. It works with Jaunty and Vista, though..
Peculiar...

Ill reboot back into it, get lspci and see if its recognized.

---

### Post by b0b138 on 2009-10-18
oops...nevermind. The bios is fine if it worked on the live cd. :rolleyes: Did you install the restriced driver once karmic was installed as the driver won't carry over from the live session?

---

### Post by tom.swartz07 on 2009-10-18
> **b0b138 said:**
> oops...nevermind. The bios is fine if it worked on the live cd. :rolleyes: Did you install the restriced driver once karmic was installed as the driver won't carry over from the live session?

When I launched the live cd in previous sessions, yes, i installed it, but this most recent time i did not install it.
Does that cause it to not carry over? How do i fix that?

---

### Post by b0b138 on 2009-10-18
Once karmic is installed and you boot to it (not the cd) you'll have to install restriced drivers again.

---

### Post by tom.swartz07 on 2009-10-18
That's the problem- there are no drivers listed. It says "There are no rectricted drivers in use on you'd system", yet the drivers are needed for the live cd and (obviously) on the hdd

---

### Post by NCLI on 2009-10-18
The restricted drivers are on the live cd, and in the repos. The reason why it showed up in your live session and not in the fully installed Karmic is that the Live CD will not even consider looking in the repos, and just installs the driver from the cd.

To install a restricted driver after installing karmic, you have to options:

A) Connect your computer to the internet with a cable, then run "sudo apt-get update && sudo apt-get upgrade". Finally, go to Restriced Drivers again. It should be listed there now.

B) Insert the Live CD, and change the settings in Software Sources to use the CD as a repo.

---

### Post by tom.swartz07 on 2009-10-18
> **NCLI said:**
> The restricted drivers are on the live cd, and in the repos. The reason why it showed up in your live session and not in the fully installed Karmic is that the Live CD will not even consider looking in the repos, and just installs the driver from the cd.

To install a restricted driver after installing karmic, you have to options:

A) Connect your computer to the internet with a cable, then run "sudo apt-get update && sudo apt-get upgrade". Finally, go to Restriced Drivers again. It should be listed there now.

B) Insert the Live CD, and change the settings in Software Sources to use the CD as a repo.

Ok, ive poked around, but connecting via Ethernet will not work. How do I use plan b? 
Admin/software sources/ then click the "installable from CDROM" listed there?

EDIT: nevermind- that's what did it

---

### Post by tom.swartz07 on 2009-10-18
It now lists the drivers, but the installer crashes each time I try. :'( the first time I tried, it went into kernel panic; I had to
hard reboot. Now it crashes each time I try to install the driver. 
what could I try now?

---

### Post by tom.swartz07 on 2009-10-18
Bump. I'm only on my iPhone for Internet or communicating here. Any help would be greatly appreciated.

---

### Post by b0b138 on 2009-10-18
If it were me I'd reinstall and see what happens. Select install from the boot menu of the cd

---

### Post by tom.swartz07 on 2009-10-18
> **b0b138 said:**
> If it were me I'd reinstall and see what happens. Select install from the boot menu of the cd

After a reinstall, everything is up and working perfectly.
Thanks to everyone that helped along the way! I really appreciate your help!

Ill edit the first post to become a guide for troubleshooting.

---

