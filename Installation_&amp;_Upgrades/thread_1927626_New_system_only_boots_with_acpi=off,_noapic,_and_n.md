---
title: "New system only boots with acpi=off, noapic, and nolapic"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by raxman on 2012-02-18
Hi,

I'm trying to install Ubuntu 11.10 on a new system I built.  I am trying to do this from USB.  I have installed Ubuntu many times in the past this way.  However, on this system I can only get Ubuntu to boot with the follow three options: acpi=off, noapic, and nolapic.  It only works with all three.

Here are the stats on my system:
OCZ 120 GB Vertex 3 SATA III 6.0 Gb-s 2.5-Inch Solid State Drive 
EVGA GeForce GTX 590 Classified 3072 MB PCI Express 2.0 
ASUS LPCIe 3.0 and UEFI BIOS P8Z68-V PRO/GEN3
Samsung Blu-Ray Combo Internal 12XReadable and DVD-Writable Drive with Lightscribe SH-B123L/BSBP
Intel Core i7-2600K 3.4 GHz 8 MB Cache Socket LGA1155 Processor
Corsair Vengeance Blue 16 GB PC3-12800 1600mHz DDR3 240-Pin SDRAM Dual Channel

Windows7 works fine.  I have tried Kubuntu and Mint as well but they all need the same options.  I attached a picture of the point at which it stops.  I only have a SSD drive, not HDD.  Don't know if that matters.  I tried disconnecting the drive to see I could boot and it made not difference.

Any helping at getting this system to boot would be greatly appreciated.  I don't want to develop in Windows since I have been using Scientific Linux at work for years.

---

### Post by misterbk on 2012-02-21
Several people are saying this is solved by disabling the onboard ASMedia SATA controller in your BIOS.

This is the controller that provides the third 6GB/s SATA port.  (The Intel chipset only provides two.) Think of it as being like the more familiar SiliconImage controllers.

This may be entirely based on one Newegg review.  I've yet to see someone who started out with this problem, and received this suggestion, report back whether it worked.  (At least not having satisfied me that they disabled it correctly. They seemed somewhat confused as to what the ASMedia SATA was.)

[EDIT:]  I just noticed you have the -V and not the -M.  That suggestion was for the -M.  I'm not able to tell if the -V version had an ASMEDIA Sata controller, so this might not apply.  (But might be worth a look.)

Be warned that ASMedia is also the name of a controller providing extra USB ports on that board.  (I just can't tell if it has the ASMedia SATA controller too.)

---

### Post by YannBuntu on 2012-02-21
> **raxman said:**
> I can only get Ubuntu to boot with the follow three options: acpi=off, noapic, and nolapic.

These options can easily be added to GRUB2 later, so that's not a big deal.

> **raxman said:**
> UEFI BIOS

This can bring problems if you don't take care. Please could you follow [this tutorial]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") and indicate here the result?

---

