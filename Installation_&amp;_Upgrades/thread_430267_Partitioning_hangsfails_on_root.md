---
title: "Partitioning hangs/fails on root"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by lael on 2007-05-02
On a Dell Laptop E1705, SATA hard drive (100GB 5400 rpm)
When I run through the installation wizard, I setup my options as a "Guided - use entire disk"
it shows "SCSI1 (0,0,0) (sda) - 98.5 GB ATA FUJITSU MHV2100B"

The install fails on "Creating ext3 file system for / in partition #1 of SCSI1 (0,0..."

It eventually comes up with a error dialog titled "Failed to create a file system" saying "The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed."

The only thing that seems strange to me is that its labeling the disk as a SCSI drive - its SATA  - Is this correct?

I had this drive running Windows XP MCE just before trying to install.  This happens with both Edgy and Feisty.

Its probably something simple like I need to set a boot flag- I see that the Hard drive light is on all the time after it fails. any ideas?

Edgy is working great on my old Inspiron 5150,  Can anyone give some pointers on what to look into?

---

### Post by lael on 2007-05-02
lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7800 (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

Thank you

---

### Post by Mrs Harris on 2007-05-02
I did a couple of things and finally managed to get an install to complete (though I can't boot at present!!!)

I first went into System -> Preferences -> <some sort of menu item about removable meedia) and unchecked the auto mounting of removable drives etc.  For some reason my SATA drives were seen as removeable.

I also then used gparted to format my drives before the install... if you search I'm sure you'll find something simiilar with Xubuntu I think.

Hope this helps

---

### Post by lael on 2007-05-03
Thanks for the tip Mr Harris, But no beans :-(

Has anyone else successfully installed Ubuntu on a Dell E1705?
Do I need to boot with a certain set of kernel flags?  

As I said earlier, my HD light stays on constantly after it fails, How do I tell what program caused it?

Thanks in advance!

---

### Post by ssawatzky on 2007-07-08
What worked for me to overcome the error "failed to create a file system" was to disable the automatic mounting of removable drives. What I believe may have been happening for me was when a new partition was created, it was mounted, and this stopped the partitioner from working. 

Sam

---

