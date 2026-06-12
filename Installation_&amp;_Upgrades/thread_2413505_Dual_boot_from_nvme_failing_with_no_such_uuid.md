---
title: "Dual boot from nvme failing with no such uuid"
date: 2019-02-26
forum: Installation &amp; Upgrades
---

### Post by b-launchpjd-x on 2019-02-26
I have an HP Z620 that has a SATA3 SSD /dev/sda and an MP500 NVMe in PCIe slot /dev/nvme0n1 with dual boot Windows7/10 and Ubuntu 18.04 Bionic.
Both SSD are 480GB and I've only recently realised that when I thought I was booting from the NVMe drive (by selecting those entries in grub) that it was in fact booting off sda. Last week I installed VMware on the sda drive which formatted the drive. I undid that and reinstalled Ubuntu 18.04 but I still can't boot from the NVMe partitions - I get no such device/uuid for each grub entry. sgdisk found corrupted partition table and I clonezilla'd after fixing the table to MBR.

This is the boot repair pastebin:
[http://paste.ubuntu.com/p/wvVj2d45zb/](http://paste.ubuntu.com/p/wvVj2d45zb/) 

Is there a way of making grub on sda boot the nvme partitions?

Thanks for your help

---

### Post by oldfred on 2019-02-26
Report does not show all the details on NVMe drives, yet.
 Post this:
       sudo parted /dev/nvme0n1 unit s print 
    
If MBR(msdos) then Windows is in BIOS/MBR boot mode, not UEFI/gpt.
Windows only boots in BIOS mode from MBR and only in UEFI mode from gpt.

Do not run any autofix from Boot-Repair, it will try to install grub to every drive.
But UEFI will only install to one drive, and BIOS grub will install to every drive, but if gpt will need a bios_grub partition for correct grub install.

---

### Post by b-launchpjd-x on 2019-03-19
Model: Force MP500 (nvme)
Disk /dev/nvme0n1: 937703088s
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start       End         Size        File system  Name                  Flags
 1      2048s       206847s     204800s     ntfs         Microsoft basic data  msftdata
 2      206848s     500115455s  499908608s  ntfs         Microsoft basic data  msftdata
 3      500115456s  937701375s  437585920s  ext4         Linux filesystem

---

### Post by oldfred on 2019-03-19
You are showing gpt partitioning on NVMe drive, but no ESP - efi system partition which is required for UEFI boot.
You do have an ESP on sda with just Ubuntu entries.

You are not showing in UEFI Windows boot entries. 
Is/Was Windows in the now 35 year old BIOS boot mode. Windows only boots in BIOS from MBR and only with UEFI from gpt partitioned drives.

If you want to boot from NVMe drive, you need to add an ESP and reinstall grub to use it, unless you have to convert back to the old MBR to boot Windows in BIOS mode.

---

