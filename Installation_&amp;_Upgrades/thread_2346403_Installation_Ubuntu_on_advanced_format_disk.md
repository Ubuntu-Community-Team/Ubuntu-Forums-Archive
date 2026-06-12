---
title: "Installation Ubuntu on advanced format disk"
date: 2016-12-14
forum: Installation &amp; Upgrades
---

### Post by ilyakudevich on 2016-12-14
Hello!!
I have a problem with the installation of Ubuntu 14.04. I need to install Ubuntu on a server with Advanced Format disks (the size of 4K blocks). To install I use preseed.

Installation is successful. But the OS will not boot ... "Insert boot media in selected Boot device and press a key"
The BIOS boot have UEFI.
What I'm wrong? Please help

Preseed file that I use in the attachment

---

### Post by oldfred on 2016-12-14
That is an UEFI error.
Do you have secure boot on.
Or do you have UEFI set to boot in different mode than you installed. Install in UEFI mode may still have settings in UEFI to boot system in BIOS mode or vice-versa.

---

### Post by ilyakudevich on 2016-12-14
I made 4 different ways to the BIOS, but not successful... 
Maybe the case in the method of installation? I use pxe with the following parameters
===========================================
#!ipxe
dhcp
set base-url [http://install/ubuntu/images/netboot/ubuntu-installer/amd64](http://install/ubuntu/images/netboot/ubuntu-installer/amd64)
kernel ${base-url}/linux
initrd ${base-url}/initrd.gz
imgargs linux ks=http://install/conf/ubuntu-14-04.cfg.pre --- auto=true url=http://install/conf/preseed.cfg.md1.uefi.4k ipv6.disable=1
boot
===========================================
May br it needs another option to the kernel that indicates the UEFI mode?

---

### Post by oldfred on 2016-12-14
How you boot install media is then how it installs.
May be best to see details, but you have to use a live installer or desktop version. And then add Boot-Repair.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by ilyakudevich on 2016-12-14
for the creation of this report, you must have installed OS, in my case, the installation is successful but not loaded.

---

### Post by oldfred on 2016-12-14
You can use live installer from a desktop install.

UEFI or BIOS is controlled by how you boot install media. Once you start booting in one mode or the other you cannot switch as each mode writes data to drive differently.

Also drive needs to be gpt for UEFI. But you must have the ESP - efi system partition.
If only Ubuntu it can be gpt for BIOS boot. But you must have a bios_grub partition.

If BIOS boot then drive will be MBR(msdos) partitioned.

---

### Post by ilyakudevich on 2016-12-15
at the time of the command grub-install /dev/sda /dev/sdb 

in the log shows that the block size is not supported...

---

### Post by oldfred on 2016-12-15
Not sure how you are getting that error. 4096 is supported.
Only partition tools back about Windows 7 timeframe did not support the newer 4K drives.

Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

---

