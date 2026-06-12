---
title: "SIL680 IDE card installation"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by john-woods on 2007-10-17
Hi everyone,

I am running Ubuntu 7.0.4 and just tried to expand my storage capacity by adding in an SIL680 IDE card to my system. My motherboard is an ASUS A7N266-VM if that's relevant.

My original set up consisted of:

Primary master/hda - 10GB system HD
Primary slave/hdb - 750GB HD
Secondary master/hdc - 400GB HD
Secondary slave/hdd - 400GB HD

I had no IDE ports free for my DVD drive, hence the purchase of the IDE card. So now the set up is something like this:

Primary master/hda - DVD drive
Primary slave/hdb - 10GB system HD
Secondary master/hdc - 750GB HD
IDE card primary master/hde? - 400GB HD
IDE card secondary master/hdg? - 400GB HD

This new card however, doesn't appear when I type lspci into a terminal: 

00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.3 RAM memory: nVidia Corporation Unknown device 01aa (rev b2)
00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller (rev c2)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
01:08.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:08.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:08.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
01:08.3 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)

So obviously the hard drives attached to the IDE card no longer mount.

Also, if I try to run the cfdisk command it tells me there is a fatal error, and if I try to run the fdisk command (even on hdb1, hdc1) it tells me it's unable to open the drive.

Finally, my fstab file looks like this:

# /etc/fstab: static file system information.
#
# [Device] [Mount Point] [File_system] [Options] [dump] [fsck order]

/dev/hdb1 /mnt/System ext3 defaults 0 0
/dev/hdc1 /mnt/HD1 reiserfs defaults 0 0
/dev/hde1 /mnt/HD2 reiserfs defaults 0 0
/dev/hdg1 /mnt/HD3 reiserfs defaults 0 0

I'd really appreciate any help as I was under the impression this card would just simply work when I installed it.

Thanks

---

