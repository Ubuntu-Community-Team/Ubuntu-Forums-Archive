---
title: "SATA disks gone after upgrade to 15.10."
date: 2016-03-08
forum: Installation &amp; Upgrades
---

### Post by ibbles on 2016-03-08
I used to have a Kubuntu installation that I upgraded to 15.10. After the upgrade I can no longer see any SATA disks in any Linux version I have tried. They show up just fine in BIOS. The SATA controller is set to AHCI (not IDE/RAID) in BIOS.

The regular installation cannot boot and gives an error message related to the root device and then an initramfs/busybox prompt. Error message is similar to the screen capture in [http://askubuntu.com/questions/15515/disk-by-uuid-not-detected-initramfs-boot-failure](http://askubuntu.com/questions/15515/disk-by-uuid-not-detected-initramfs-boot-failure). None of my hard drives are listed in /dev/disk/ from the initramfs prompt.

Tried reinstalling the system using an USB stick. Tried with both 15.10 and 14.04. Both versions fail because the installer cannot find enough free space anywhere.

Booting into a live instance of either 15.04 or 14.04 gives the following session. I have two USB drives connected, one is the 14.04 live USB and the other is a BIOS update that I tried to install. Don't have Windows so that didn't work.

```

$ cat /etc/issue
Ubuntu 14.04.4 LTS \n \l


$ ll /dev/disk/by-id
total 0
drwxr-xr-x 2 root root 160 Mar  8 21:40 ./
drwxr-xr-x 6 root root 120 Mar  8 21:37 ../
lrwxrwxrwx 1 root root   9 Mar  8 22:03 usb-Generic-_SD_MMC_20090815198100000-0:0 -> ../../sdd
lrwxrwxrwx 1 root root  10 Mar  8 21:40 usb-Generic-_SD_MMC_20090815198100000-0:0-part1 -> ../../sdd1
lrwxrwxrwx 1 root root   9 Mar  8 21:38 usb-Generic_Ultra_HS-SD_MMC_T11000014682-0:0 -> ../../sdc
lrwxrwxrwx 1 root root   9 Mar  8 21:38 usb-Generic_Ultra_HS-SD_MMC_T12000087797-0:0 -> ../../sdb
lrwxrwxrwx 1 root root   9 Mar  8 22:03 usb-Prolific_Technology_Inc._USB_Mass_Storage_Device -> ../../sda
lrwxrwxrwx 1 root root  10 Mar  8 21:38 usb-Prolific_Technology_Inc._USB_Mass_Storage_Device-part1 -> ../../sda1


$ sudo lshw -C disk
  *-disk                  
       description: SCSI Disk
       product: Flash Voyager
       vendor: Corsair
       physical id: 0.0.0
       bus info: scsi@8:0.0.0
       logical name: /dev/sda
       version: 1.00
       serial: 7
       size: 992MiB (1040MB)
       capabilities: removable
       configuration: sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sda
          size: 992MiB (1040MB)
          capabilities: partitioned partitioned:dos
          configuration: signature=000d684e
  *-disk
       description: SCSI Disk
       product: Ultra HS-SD/MMC
       vendor: Generic
       physical id: 0.0.0
       bus info: scsi@9:0.0.0
       logical name: /dev/sdb
       version: 1.90
       capabilities: removable
       configuration: sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk
       description: SCSI Disk
       product: Ultra HS-SD/MMC
       vendor: Generic
       physical id: 0.0.0
       bus info: scsi@10:0.0.0
       logical name: /dev/sdc
       version: 1.90
       capabilities: removable
       configuration: sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdc
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@11:0.0.0
       logical name: /dev/sdd
       size: 7577MiB (7945MB)
       capabilities: partitioned partitioned:dos
       configuration: sectorsize=512 signature=925e478a


$ dmesg | grep SATA
[    4.242864] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0xe2 impl SATA mode
[    4.245177] ata2: SATA max UDMA/133 abar m2048@0xfe30d000 port 0xfe30d180 irq 40
[    4.245183] ata6: SATA max UDMA/133 abar m2048@0xfe30d000 port 0xfe30d380 irq 44
[    4.245185] ata7: SATA max UDMA/133 abar m2048@0xfe30d000 port 0xfe30d400 irq 45
[    4.245187] ata8: SATA max UDMA/133 abar m2048@0xfe30d000 port 0xfe30d480 irq 46
[    4.567634] ata6: SATA link down (SStatus 0 SControl 300)
[    4.739579] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.739604] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.743565] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   10.230307] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   10.230328] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   10.234307] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   20.228027] ata2: limiting SATA link speed to 1.5 Gbps
[   20.228048] ata7: limiting SATA link speed to 1.5 Gbps
[   20.232023] ata8: limiting SATA link speed to 1.5 Gbps
[   20.719907] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   20.719933] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   20.723906] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   51.204935] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   51.204955] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   51.208932] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 310)


$ sudo fdisk -l

Disk /dev/sda: 1040 MB, 1040187392 bytes
32 heads, 62 sectors/track, 1024 cylinders, total 2031616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d684e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          62     2031615     1015777    c  W95 FAT32 (LBA)

Disk /dev/sdd: 7945 MB, 7945060352 bytes
238 heads, 40 sectors/track, 1630 cylinders, total 15517696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x925e478a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048    15517695     7757824    b  W95 FAT32

```



What can I do to get my disks and a proper installation back? Living from a live USB with 29MB free space is not optimal.

---

### Post by oldfred on 2016-03-08
Unplug all but live installer and run Summary Report.
        Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by ibbles on 2016-03-09
I unplugged the extra USB stick and then followed the Summary Report instructions. [http://paste.ubuntu.com/15333302/](http://paste.ubuntu.com/15333302/)

The report mentions a sdb device with the note "Devices which don't seem to have a corresponding hard drive". Could be the (empty) memory card reader in my monitor.

All internal hard drive are still connected:
   - Intel SSD 120 GB
   - WDC or Samsung 300 GB
   - Samsung or WDC 1TB

Don't remember which of WDC/Samsung was the 1TB/300GB.

---

### Post by oldfred on 2016-03-09
Report shows none of your drives?
Sometimes one drive may fail, or connector come loose/defective. But all drives is very strange.
Does UEFI/BIOS show drives. It has to correctly report drives to operating system for operating system to see them.

---

### Post by ibbles on 2016-03-09
> **oldfred said:**
> 
Does UEFI/BIOS show drives. It has to correctly report drives to operating system for operating system to see them.


Yes, all drives are shown both on the POST screen and in UEFI/BIOS. I can set boot priority and such.

When I boot without the live USB I get my regular grub menu and then the Kubuntu 15.10 splash screen with the dots: [http://lh5.ggpht.com/_wNH6h6C1mY0/S9q4A3y_GXI/AAAAAAAAAqU/CU4I9u0V_r0/s400/plymouth4.png](http://lh5.ggpht.com/_wNH6h6C1mY0/S9q4A3y_GXI/AAAAAAAAAqU/CU4I9u0V_r0/s400/plymouth4.png).
But after some time (10-15 seconds perhaps) the splash screen disappears, the "gave up waiting for root device" is shown and I'm dropped to the initramfs prompt.

So the disks are there, it's just that some low-level part of Linux can't see them.

I have heard about secure boot and that it should be turned off, but I have not been able to find a way to do that in my BIOS/UEFI. And there were no issues until I  upgraded to 15.10 two days ago.

Perhaps a BIOS reset will help? Or an older or newer version of Ubuntu?

Something else I'm getting now but didn't before are messages similar to
```
 AMD-Vi: Event logged [IO_PAGE_FAULT   ... <stuff> ... 
```
while booting the live USB. Not sure if they also appear when trying to boot from the installation. Will check when I get back home.

---

### Post by oldfred on 2016-03-09
Gigabyte motherboard withIOMMU issues?
       Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by ibbles on 2016-03-09
Getting various suggestions from those threads. Some say that iommu should be enabled in BIOS and other say that it should be disabled. Some say that the boot option should be iommu=pt and other that it should be iommu=soft.

I have no iommu setting in BIOS so not much to do there. Tried with both "pt" and "soft" for the iommu boot option and with "soft" I got my disks back, both using the live USB and the old installation. I guess that a quick edit of /etc/default/grub to make the "soft" permanent is all that remains before this thread can be marked as solved.

I have one final question though. If I make a fresh install from the USB with the "soft" option set when starting the installer, will that setting carry over to the installed instance?

---

### Post by goofprog on 2016-03-09
[SIZE=5][FONT=arial black]"[/FONT][/SIZE]
$ ll /dev/disk/by-id
total 0
drwxr-xr-x 2 root root 160 Mar  8 21:40 ./
drwxr-xr-x 6 root root 120 Mar  8 21:37 ../
lrwxrwxrwx 1 root root   9 Mar  8 22:03 usb-Generic-_SD_MMC_20090815198100000-0:0 -> ../../sdd
lrwxrwxrwx 1 root root  10 Mar  8 21:40 usb-Generic-_SD_MMC_20090815198100000-0:0-part1 -> ../../sdd1
lrwxrwxrwx 1 root root   9 Mar  8 21:38 usb-Generic_Ultra_HS-SD_MMC_T11000014682-0:0 -> ../../sdc
lrwxrwxrwx 1 root root   9 Mar  8 21:38 usb-Generic_Ultra_HS-SD_MMC_T12000087797-0:0 -> ../../sdb
lrwxrwxrwx 1 root root   9 Mar  8 22:03 usb-Prolific_Technology_Inc._USB_Mass_Storage_Device -> ../../sda
lrwxrwxrwx 1 root root  10 Mar  8 21:38 usb-Prolific_Technology_Inc._USB_Mass_Storage_Device-part1 -> ../../sda1
[FONT=arial black][/FONT][SIZE=5][FONT=arial black]"[/FONT][/SIZE]
Excuse my ignorance, MMC disks are not SSD drives.  Those are used as new modern day floppies. A secure disk is not always a solid state disk.

---

### Post by ibbles on 2016-03-11
> **ibbles said:**
> 
I have one final question though. If I make a fresh install from the USB with the "soft" option set when starting the installer, will that setting carry over to the installed instance?


It did not, but that's ok. I got everything working anyway.

A quick summary for future reference:

[LIST=1]
[*]DIstUpgrade to 15.10.
[*]AMD-Vi IO_PAGE_FAULT messages during boot.
[*]All three disks gone after reboot when upgrade finished.
[*]Dropped to initramfs/BusyBox prompt with a "gave up waiting for root device" message.
[*]No disk listed in /dev/disk/ or other disk-inspection tools.
[*]Created live USB sticks with various versions of Ubuntu, new and old.
[*]Each fail to find any disks.
[*]On try/install menu in live USB, pressed tab to edit install command.
[*]Added "iommu=soft" just before the "---"
[*]Installer now sees disks, install Xubuntu 15.10.
[*]Reboot without live USB when done.
[*]AMD-Vi messages back.
[*]Disks gone, back at initramfs/BusyBox prompt.
[*]Boot with live USB again.
[*]Add "iommu=soft" to the try menu item.
[*]Follow instructions at [http://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd](http://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd)
[LIST=1]
[*]sudo mount /dev/sda1 /mnt
[*]sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
[*]sudo chroot /mnt
[*]Add iommu=soft to /etc/default/grub as per [http://ubuntuforums.org/showthread.php?t=2111223&page=4](http://ubuntuforums.org/showthread.php?t=2111223&page=4)
[*]sudo update-grub
[/LIST]

[*]Shutdown, remove USB, boot.
[*]IT'S ALIVE!
[/LIST]

---

