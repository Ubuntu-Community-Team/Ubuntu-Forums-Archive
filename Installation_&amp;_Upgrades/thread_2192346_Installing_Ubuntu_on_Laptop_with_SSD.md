---
title: "Installing Ubuntu on Laptop with SSD"
date: 2013-12-07
forum: Installation &amp; Upgrades
---

### Post by marinahov95 on 2013-12-07
I originally had a Windows 8 operating system from which I tried to  switch to Linux via USB installation. My computer's hard-drive became  completely wiped out and the only thing that it would boot from was the  Ubuntu USB I had previously created. When I turn on my computer, it  gives me the options of Installing Ubuntu or Trying Ubuntu. I Installed  Ubuntu and restarted my computer. My computer  works well until I shut it down or take out the USB. Then, my hard-drive  is once again wiped out and the only thing I can do is plug in the USB  and use it with the USB inside the computer, having to Try or Install ubuntu all over. I've attempted this several  times, with different flash drives but nothing changes. 
 
I'm using the Ubuntu 12.04 LTS 64 bit desktop
 
My computer Model is Samsung ativ book 9 Lite model NP915S3G
 
I've attempted to go through the steps the ubuntu help by the Boot Repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair))  then rebooted my computer. My computer still didn't boot to the OS but  now, every time I follow those same steps and reboot my computer it  brings me back to this same account.
The URL I receive from Boot-Repair is [http://paste.ubuntu.com/6535423](http://paste.ubuntu.com/6535423). It tells me to make BIOS boot on sda1/EFI/ubuntu/shimx64.efi but i don't really know how to do that.
 
Secure boot is disabled
The OS selection is on CSM and UEFI OS 
AHCI mode control is manual
AHCI mode is disabled
Fast BIOS mode is off
PXE OPROM is off
My system has a Solid State Drive (SSD) 
 
My BIOS Version is P03RBV but i can't seem to find the UEFI version
The only options i have for boot option priorities are UEFI:USB Flash MemoryPMAp and "disabled"

---

### Post by fantab on 2013-12-07
What do you mean when you say, "Then, my hard-drive  is once again wiped out"? I wonder how is that possible.
Do you have both HDD and SSD? or just SSD?
```
parted -l:

Model: ATA SAMSUNG MZMTD128 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
[COLOR=#b22222]**Partition Table: gpt**[/COLOR]

Number  Start   End     Size    File system     Name  Flags
1      1049kB  99.6MB  98.6MB  fat32                 boot
2      99.6MB  124GB   124GB   ext4
3      124GB   128GB   3698MB  linux-swap(v1)
```

As you can see in 'red' above, you have GPT partition table. Ubuntu can boot from GPT in 'Legacy/CSM' mode but you will need a 5Mb /boot partition.
You already have the FAT32 EFI partition, so it will be better if you enable UEFI boot in UEFI and disable 'Legacy/CSM'.
Also you will have to install Ubuntu in EFI mode only: [See HERE]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode") to know the difference...

If AHCI is disabled then what mode is it set to? AHCI is what it should be. Set the mode to AHCI.

For now, change the boot mode to 'UEFI' or 'EFI' and Enable AHCI. Boot Ubuntu and tell us what happens...

---

### Post by oldfred on 2013-12-07
When Boot-Repair dumps the UEFI memory it shows several boot orders, I do not know what all are. I guess one may be secure boot, UEFI , and CSM?
But you do show ubuntu as boot option.

> BootOrder: 0001,0017,0018,0000
Boot0000* Windows Boot Manager	Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...0................
Boot0001* ubuntu	HD(1,800,2f000,85f5b0a1-aa08-40d8-b339-954702b70031)File(EFIubuntushimx64.efi)
Boot0017* UEFI:  USB Flash MemoryPMAP	ACPI(a0341d0,0)PCI(10,0)USB(3,0)HD(1,2,e88d7e,000f402e)..BO
Boot0018*  USB Flash MemoryPMAP	BIOS(5,0,00)..BO

UEFI remembers settings, so even though Windows is erased from efi partition it still is in UEFI memory.

---

