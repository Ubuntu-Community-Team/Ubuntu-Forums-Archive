---
title: "Cannot boot after installing (UEFI)"
date: 2015-01-21
forum: Installation &amp; Upgrades
---

### Post by mikl-dk on 2015-01-21
I installed Ubuntu 14.10 via USB and cannot boot afterwards. I have tried choosing both UEFI, UEFI/CSM (CSM being legacy) and only CSM.

Boot Repair gives this log:
[http://paste.ubuntu.com/9805117/](http://paste.ubuntu.com/9805117/)

I have tried having Boot Repair performing a repair but it did not help.

---

### Post by TheFu on 2015-01-21
> 
 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

Hard to boot if there isn't a boot loaded.

I'd try **sudo grub-install /dev/sda**
followed by 
**sudo update-grub**.

It isn't like this will do any harm.

---

### Post by fantab on 2015-01-21
OP has a UEFI with GPT so there won't be a boot loader in the MBR, thats legacy/csm now. :)
Boot files will be installed in ESP [EFI System Partition], formatted with FAT32 and a 'boot' flag.

There is nothing really in the bootinfo suggesting any issue, AFAIK.

Give us more details about your machine; what kind of graphics do you have?
It has to be either graphics related or

```

parted -l:

Model: ATA SAMSUNG MZMPC256 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End    Size    File system     Name  Flags
**1      1049kB  538MB  537MB   fat32                 boot, [COLOR=#800000]esp[/COLOR]**
2      538MB   252GB  252GB   ext4
3      252GB   256GB  3899MB  linux-swap(v1)
```

I am not sure if there should be an 'esp' flag on the fat32 partition. AFAIK there should only be a 'boot' flag.
Remove the 'esp' flag from the partition using [gparted]("http://www.dedoimedo.com/computers/gparted.html#mozTocId143113") from Live Ubuntu DVD/USB. It should be simple.
Reboot from HDD and tell us how it goes...

---

### Post by mikl-dk on 2015-01-21
EFI System Partition (ESP). And I cannot remove esp flag without also removing boot flag.

My laptop is a Samsung NP900X3C-A04SE. I have no problems booting from the USB stick.

---

### Post by mikl-dk on 2015-01-21
```

ubuntu@ubuntu:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c0d3]
	Kernel driver in use: ivb_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c0d3]
	Kernel driver in use: i915
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c0d3]
	Kernel driver in use: mei_me
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c0d3]
	Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
	Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
	Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 [8086:1e18] (rev c4)
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c0d3]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation HM75 Express Chipset LPC Controller [8086:1e5d] (rev 04)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c0d3]
	Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c0d3]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c0d3]
01:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
	Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
	Kernel driver in use: iwlwifi
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c0d3]
	Kernel driver in use: r8169
03:00.0 USB controller [0c03]: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller [1912:0015] (rev 02)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c0cd]
	Kernel driver in use: xhci_hcd

```

---

### Post by oldfred on 2015-01-21
I think Samsung is like HP & Sony, they only boot Windows  description.

Since you only have ubuntu you can just rename it so it has the Windows name. 
       **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

Or create /EFI/Boot/bootx64.efi where that file is really grub or shim and boot hard drive entry.

       **A:** Manually rename files efi boot files in efi partition

 **a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.

Other alternatives:
       [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019
[/URL]
 Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)

Standard details on command line creation of /EFI/Boot/bootx64.efi (you do not have the /EFI/Boot folder yet, others may.)
      
 From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
sudo mount /dev/sda1 /mnt
#only if not already existing, 
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip this command
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi 

     [URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

### Post by mikl-dk on 2015-01-21
That's brilliant! This stuff did the trick - thank heaps!!!

> **oldfred said:**
> 
```

 From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
sudo mount /dev/sda1 /mnt
#only if not already existing, 
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip this command
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi 

```


---

