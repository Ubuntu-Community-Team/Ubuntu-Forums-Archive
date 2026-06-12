---
title: "Ubuntu 10.10 installation: Can't see HD partitions"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by Snowflame on 2010-10-14
Pretty much as the title says.  I am attempting an amd64 install on a new computer that has two 1 TB Hard Drives, with Windows 7 on one of them.  When booting from a Ubuntu 10.10 CD to perform the installation, it won't let me proceed because the "2.4 GB free" condition is not met.

Terminal ->
ubuntu@ubuntu:~$ fdisk -l 
ubuntu@ubuntu:~$

    Yeah, nothing.  GParted and Disk Utility both see absolutely nothing as well.  I've tried this with several variations.  Notably, at first I had the full 1 TB drive seen as "unallocated" by Windows; after the first failures, I hand-partioned this in Windows (since fsck didn't seem to do anything in Ubuntu), but it didn't matter, as Ubuntu still saw no hard drives.  I even shrank the C partition slightly, thinking perhaps that 1 hard drive was misbehaving, but it didn't matter.  

I'm at a loss as for what to do with just the CD available when it can't even acknowledge the hard drives.  The only thing I can think of is this might be some bizarre bug in interfacing with the Motherboard so that Windows 7 can interface with it but not Ubuntu?  This is a GA-X58A-UD3R.  I looked in the setup BIOS options but didn't see anything particularly leap out as dangerous.

  Any help would be greatly appreciated.  Thanks.

---

### Post by Rubi1200 on 2010-10-14
Try running this command and see if you get further:

```
parted /dev/sda print
```
Post back with what it says.

Also, see here:
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by Snowflame on 2010-10-14
Thanks for your reply. 

I should have mentioned this before, but I also ls 'd the /dev directory.  There weren't any hda# or sda# entries in it.  I'm off to work right now but will double-check this is still true when I get back, but with no /dev/sda I doubt that command will tell us much useful. 

Re the picture in your link, GParted, when I brought it up, didn't see the "unallocated" space, but merely saw nothing at all.

---

### Post by dino99 on 2010-10-14
you might prepare your partitions with partedmagic (boot on it) before installation, then install with the "alternate" iso to select manual installation. when formatting, take note of the partitions's names (/dev/sd?) to install on it later.

Create 3 partitions:
- / : root, bootable, ext4 format, about 12 gb
- swap: about 2 gb
- /home : ext4, unlimited space (to store your data)

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by srs5694 on 2010-10-14
A few ideas:


[list]
[*]Check your BIOS for AHCI options. Changing them might get the drives recognized. OTOH, this might then cause Windows to flake out.
[*]Try juggling the drive cables, so that the hard disk plugs into a different SATA port on the motherboard. (Try all of them.) This might work because some motherboards use more than one hard disk controller, and sometimes one works better than the other. Again, though, Windows might flake out.
[*]Try another distribution or an emergency disc, like [System Rescue CD](http://www.sysresccd.org) or [PartedMagic.](http://partedmagic.com/) Trying two or three is worthwhile. This will provide data on whether the problem is unique to Ubuntu or present in all (or at least several) Linux distributions. If the former, you're more likely to find a solution, or at least be able to install some other distribution.
[*]Boot the installer into live CD mode and open a Terminal window. Type "dmesg | less" and scan the entries for anything related to hard disks, SATA, or SCSI. Post excerpts if you need help interpreting the entries.
[*]Type "lspci", locate the entries for the disk controllers (probably identified as SATA and/or IDE), and post them here.
[*]You could try buying a plug-in SATA controller and using it instead of the controller built into the motherboard. This last-ditch approach may be necessary if the motherboard is new enough that it's just not yet well supported in Linux.
[/list]

---

### Post by Mark Phelps on 2010-10-14
Did you do "sudo fdisk -l" ?? Unless you're running as root in the terminal (you would have a # prompt if you were), you need to do the "sudo" in from of the fdisk command for it to work.

---

### Post by Snowflame on 2010-10-14
Thanks again for the replies.
Rubi1200: On second glance /dev/sda does exist.  Did I just miss it before?  That said, still no luck.
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Error opening /dev/sda: No medium found                            
Retry/Cancel?                                       

Mark Phelps: Yes, I tried it with both sudo and without sudo before, no difference.

srs5694:
Here's the relevant results of lspci:
[FONT=Courier New]
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 IDE interface: Marvell Technology Group Ltd. Device 91a3 (rev 11)
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
03:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
05:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
05:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
06:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
06:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)[/FONT]

As for dmesg, here's the relevant parts I could find:

[FONT=Courier New][    3.213706] ata_piix 0000:00:1f.2: version 2.13
[    3.213720] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.213723] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    3.213751] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.213820] scsi0 : ata_piix
[    3.213866] scsi1 : ata_piix
[    3.214248] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    3.214253] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    3.214268] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.214271] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    3.214294] ata_piix 0000:00:1f.5: setting latency timer to 64
[    3.214326] scsi2 : ata_piix
[    3.214358] scsi3 : ata_piix
[    3.214733] ata3: SATA max UDMA/133 cmd 0xf600 ctl 0xf500 bmdma 0xf200 irq 19
[    3.214736] ata4: SATA max UDMA/133 cmd 0xf400 ctl 0xf300 bmdma 0xf208 irq 19
[    3.214769] pata_acpi 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.214784] pata_acpi 0000:01:00.0: setting latency timer to 64
[    3.214791] pata_acpi 0000:01:00.0: PCI INT A disabled
[    3.214805] pata_acpi 0000:05:00.1: enabling device (0000 -> 0001)
[    3.214809]   alloc irq_desc for 18 on node -1
[    3.214810]   alloc kstat_irqs on node -1
[    3.214814] pata_acpi 0000:05:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    3.214831] pata_acpi 0000:05:00.1: setting latency timer to 64
[    3.214838] pata_acpi 0000:05:00.1: PCI INT B disabled
[    3.214851] pata_acpi 0000:06:00.1: enabling device (0000 -> 0001)
[    3.214854] pata_acpi 0000:06:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    3.214868] pata_acpi 0000:06:00.1: setting latency timer to 64
[    3.214876] pata_acpi 0000:06:00.1: PCI INT B disabled
[    3.215029] Fixed MDIO Bus: probed
[    3.215046] PPP generic driver version 2.4.2
[/FONT]

(snip)
[FONT=Courier New]
[    3.718733] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.738831] ata3.00: ATAPI: ATAPI   iHAS124   B, AL08, max UDMA/100
[    3.778664] ata3.00: configured for UDMA/100
[    3.918903] ata1.00: SATA link down (SStatus 0 SControl 300)
[    3.918916] ata1.01: SATA link down (SStatus 0 SControl 300)
[    3.929634] ata2.00: SATA link down (SStatus 0 SControl 300)
[    3.929646] ata2.01: SATA link down (SStatus 0 SControl 300)
[    3.931105] scsi 2:0:0:0: CD-ROM            ATAPI    iHAS124   B      AL08 PQ: 0 ANSI: 5
[/FONT]
(snip)
SATA link is down but Linux supports AHCI so this shouldn't be a problem...  in theory.

[FONT=Courier New]
[    4.008300] [drm] Initialized drm 1.1.0 20060810
[    4.030529] ahci 0000:05:00.0: version 3.0
[    4.030541] ahci 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.048324] ahci 0000:05:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    4.048329] ahci 0000:05:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    4.048336] ahci 0000:05:00.0: setting latency timer to 64
[    4.048654] scsi9 : ahci
[    4.048851] scsi10 : ahci
[    4.048859] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    4.048964] ata9: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe100 irq 17
[    4.048968] ata10: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe180 irq 17
[    4.048989] ahci 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.068254] ahci 0000:06:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    4.068259] ahci 0000:06:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    4.068266] ahci 0000:06:00.0: setting latency timer to 64
[    4.068491] scsi11 : ahci
[    4.068632] scsi12 : ahci
[    4.068730] ata11: SATA max UDMA/133 abar m8192@0xfbcfe000 port 0xfbcfe100 irq 19
[    4.068734] ata12: SATA max UDMA/133 abar m8192@0xfbcfe000 port 0xfbcfe180 irq 19
[    4.259352] usbcore: registered new interface driver hiddev
[    4.273589] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input2
[    4.273648] generic-usb 0003:046D:C31C.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Keyboard] on usb-0000:00:1a.0-1/input0
[    4.320381] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/input/input3
[    4.320473] generic-usb 0003:046D:C31C.0002: input,hidraw1: USB HID v1.10 Device [Logitech USB Keyboard] on usb-0000:00:1a.0-1/input1
[    4.320485] usbcore: registered new interface driver usbhid
[    4.320486] usbhid: USB HID core driver
[    4.396656] ata9: SATA link down (SStatus 0 SControl 300)
[    4.396690] ata10: SATA link down (SStatus 0 SControl 300)
[    4.416593] ata11: SATA link down (SStatus 0 SControl 300)
[    4.428468] ata12: SATA link down (SStatus 0 SControl 300)
[/FONT]

Anyway, this is more a "post the results while they're in memory" post.  I have a PartedMagic boot CD I'm going to try next, and also triple-check the AHCI options in the BIOS.  (It would suck to have to make a BIOS change every time I wanted to boot into Linux, though, if that ends up being required to get this going.  Maybe if I changed one hard drive to work one way and the Windows the way it already does...?)

---

### Post by Snowflame on 2010-10-14
Nope, PartedMagic saw nothing from that boot CD, either.  fdisk -l was similarly helpless.  

Here are my BIOS settings, which I guess probably are at fault here, but I'd be incredibly nervous to change them:  

ICH SATA Control Mode: IDE (rather than RAID or AHCI) 
SATA Port0-3 Native Mode: Disabled (rather than Legacy) 
eSATA Controller: Enabled 
eSATA Ctrl Mode: IDE (rather than AHCI or RAID) 
GSATA 6_7/IDE Controller: Enabled 
GSATA 6_7/IDE Ctrl Mode: IDE (rather than AHCI) 
SATA3 Firmware Selection: Auto 
SATA3 RAID Mode Control: Auto (not using RAID anyway...) 
GSATA 8_9/IDE Controller: Enabled 
GSATA 8_9/IDE Ctrl Mode: IDE (rather than AHCI)  

On second thought, that SATA link failed in the dmesg might well be at fault if it's not doing some kind of "fallback" to another protocol properly.  I guess I'll fiddle some more.

Also, fun fact.  Your posts come out utterly terrible if you don't turn off NoScript here!  Glad to see that everyone doesn't have to insert their br's manually here after all...

Further edit: Switching SATA Port0-3 Native mode didn't make a difference.  One other BIOS feature of note: in the list of hard drives, the Channel 2 Master is ATAPI iHAS124 B.  The Channel 6 Master and Channel 6 Slave are the actual hard drives.  There isn't some crazy bug where Linux ignores hard drives slotted above a certain channel, I hope?  Then again that was part of srs5694's suggestion, to try plugging into other ports on the motherboard.  Ugh.

Edit the next: Good news!  Maybe!  Switching all the IDE options to AHCI means that Ubuntu was finally able to see the hard drives!  Now to not actually install Ubuntu yet and reboot into Windows 7 first, to make sure it hasn't rebelled.   Although.  Even if this works, I'm down for filing a bug - Ubuntu DEFINITELY should work with IDE, as it did just fine when I installed 8.10 awhile back, so there's some kind of wacky motherboard compatibility bug afoot here.

Next edit: Man, Windows hates this.   Crash->StartupRepair-> "I have no idea what's wrong."  Ack ack ack.  Unless there's some automated way to switch BIOS settings in Grub, which I doubt...  or this bug gets fixed.

---

### Post by RayVad on 2011-01-07
Hi Snowflame,

Did you manage to solve this problem?

Regards,
Ray

---

### Post by Snowflame on 2011-01-07
I "solved" the problem the bad way: I switched the modes of my hard drives to AHCI and reinstalled Windows 7, then installed Ubuntu.

If you have the same motherboard, then that's confirmation that this is the common thread, so definitely file a bug on this.

---

