---
title: "SSD drive not detected at installation"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by TonyV on 2010-05-15
Hey all, I'm dead in the water here and can't finish installing Ubuntu 10.04.  I have a Corsair Nova 128 GB solid state drive, [[COLOR="Blue"]the 128 GB model of this series[/COLOR]](http://www.corsair.com/products/ssd_nova/default.aspx), to be precise.  I have [[COLOR="Blue"]an ASUS P5N-T Deluxe motherboard[/COLOR]](http://www.asus.com/product.aspx?P_ID=64sh5AD8oYUq7Cp3&content=specifications).  It has a six xSATA 3 Gb/s ports NVIDIA MediaShield RAID controlelr on it.  In Disk Utility, it shows up as nVidia Corporation MCP55 SATA Controller, using the sata_nv driver.  I have the 128 GB drive plugged into one of these ports.  I have disabled RAID completely in the BIOS.

When I boot the Live CD and run GParted, the drive shows up fine.  I've got a 70.81 GiB NTFS partition (Windows 7), a 4.00 GiB swap partition, and a 44.43 GiB ext4 partition, onto which I had planned to install Ubuntu 10.04.  I created the swap and ext4 partitions earlier, but at one point, that was unpartitioned space.

The problem is that when I run the Install app to install Ubuntu 10.04 on my SSD, when I get to step 4 of 8 (Prepare partitions), exactly zero drives show up.  A while ago, I had a couple of Seagate 1.5 TB mirrored drives plugged into two of the ports, and they showed up fine, but no 128 GB SSD.  In trying to troubleshoot this problem, I unplugged those and just left the SSD, and zero drives showed up.  I disabled RAID in the BIOS, and it still doesn't show up.  I moved the SSD from the port it was plugged into and plugged it into one of the ports that one of the 1.5 TB drives was plugged into.  It still doesn't show up.

Nuts and bolts of it:  Seagate 1.5 TB drive plugged into port: no problem.  Corsair Nova 128 GB SSD plugged into port: doesn't show up.  But again, *only* in the Install utility.  In Disk Utility under SATA Host Adapter/MCP55 SATA Controller, I see 128 GB Solid-State Disk/ATA Corsair CSSD-V128GB2 listed plain as day.  In GParted, I see a 119.24 GiB /dev/sda device with the partitions I've created on it plain as day.  I can pull up a terminal and mount /dev/sda3 /mnt/ssd without any problem and access files on it.  But for whatever reasons, the Install program *and only the Install program* can't see it.

I'm dead in the water.  Obviously, I can't use Ubuntu if I can't install it.  What can I do to get this disk drive detected?

I'm at my wit's end.  Here is the output from an lspci command:

> 00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
01:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:02.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
04:00.0 VGA compatible controller: ATI Technologies Inc Device 6898
04:00.1 Audio device: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series]
05:06.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
05:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)


Any help would be appreciated!

---

### Post by darkod on 2010-05-15
Strange... I know it's a long shot, and that you have disabled RAID in the BIOS, but it doesn't hurt checking the disk for metadata remains.

From live mode, try:
sudo dmraid -r -E /dev/sda

If it asks you if you want to remove raid settings, that was you problem and after removing them the installer should see the disk. This usually happens because of raid metadata because even after you disable raid, the disk will have settings traces on it if it was used in raid by you or earlier.

If it's not that, I have no idea right now. Since Gparted can see it, obviously it's correctly recognized by BIOS and working.

---

### Post by TonyV on 2010-05-15
> **darkod said:**
> Strange... I know it's a long shot, and that you have disabled RAID in the BIOS, but it doesn't hurt checking the disk for metadata remains.

From live mode, try:
sudo dmraid -r -E /dev/sda

If it asks you if you want to remove raid settings, that was you problem and after removing them the installer should see the disk. This usually happens because of raid metadata because even after you disable raid, the disk will have settings traces on it if it was used in raid by you or earlier.

If it's not that, I have no idea right now. Since Gparted can see it, obviously it's correctly recognized by BIOS and working.

DUDE!  You are my new pop culture hero.  I ran the command, and voila!  Disk showed up!  I'm installing now, thanks a ton!

---

