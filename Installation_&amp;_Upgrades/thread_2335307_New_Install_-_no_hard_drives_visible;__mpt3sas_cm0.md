---
title: "New Install - no hard drives visible;  mpt3sas_cm0: unable to map adapter memory!"
date: 2016-08-27
forum: Installation &amp; Upgrades
---

### Post by davejohnson2 on 2016-08-27
Hi - I'm trying to install Ubuntu on a new Dell t7910 workstation. It currently has Windows 7 on it, which boots fine (so I know both hard drives and the raid controller are working fine). However, when I boot Ubuntu 16.04 from a USB (or CD), I cannot see the hard drives. df -h, fdisk -l, and gparted all fail to show them. See output below.

Filesystem      Size  Used Avail Use% Mounted on
udev             63G     0   63G   0% /dev
tmpfs            13G   10M   13G   1% /run
/dev/sda1       7.9G  1.5G  6.5G  19% /cdrom
/dev/loop0      1.4G  1.4G     0 100% /rofs
/cow             63G  778M   63G   2% /
tmpfs            63G  340K   63G   1% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs            63G     0   63G   0% /sys/fs/cgroup
tmpfs            63G  340K   63G   1% /tmp
tmpfs            13G   80K   13G   1% /run/user/999

/dev/sda1 is the USB drive which I have booted from.

Configuration:

- dual hard drives behind a raid controller - a 12GB/s SAS3008 MPT SAS-3; one 512 MB SSD and one 2 TB HDD. 

- bios config: legacy (no UEFI), AHCI, Raid controller on (won't boot at all with out this)

- using an AVAGO MPT3BIOS-8.25 (which seems to work fine)

The relevant kern.log section is below:

Aug 27 01:34:35 ubuntu kernel: [    7.186048] ahci 0000:00:1f.2: version 3.0
Aug 27 01:34:35 ubuntu kernel: [    7.186420] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x1 impl SATA mode
Aug 27 01:34:35 ubuntu kernel: [    7.186422] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
Aug 27 01:34:35 ubuntu kernel: [    7.187021] mpt3sas version 12.100.00.00 loaded
Aug 27 01:34:35 ubuntu kernel: [    7.187722] scsi host1: ahci
Aug 27 01:34:35 ubuntu kernel: [    7.187853] mpt3sas_cm0: 64 BIT PCI BUS DMA ADDRESSING SUPPORTED, total mem (131953464 kB)
Aug 27 01:34:35 ubuntu kernel: [    7.187857] mpt3sas_cm0: unable to map adapter memory!  or resource not found
Aug 27 01:34:35 ubuntu kernel: [    7.187961] mpt3sas_cm0: failure at /build/linux-dcxD3m/linux-4.4.0/drivers/scsi/mpt3sas/mpt3sas_scsih.c:8800/_scsih_probe()!

I have tried booting from both a USB for install and a USB drive with 16.04 install on it and fully upgraded. Neither fix the boot error.

Finally - I have looked around for folks with similar problems are there are some notes about setting boot flags such as "load_mrsas=YES" and so on. I have tried changing these boot flags in a few different configurations, but to no avail.

Ubuntu does this this (or a very similar part) as supported hardware ([http://www.ubuntu.com/certification/catalog/component/pci/1028%3A1f46/1000%3A0097/](http://www.ubuntu.com/certification/catalog/component/pci/1028%3A1f46/1000%3A0097/))

I did try 14.04, but it has the same problem.

Any help is appreciated!

---

