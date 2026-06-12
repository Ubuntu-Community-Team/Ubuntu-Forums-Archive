---
title: "disk logical name changes on reboot"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by 4ms on 2008-02-20
hello team,

on reboot the logical volumes on most of my disks changed.  This had happened earlier when virtual machines went haywire and so I had checked.

the root system disk (internal sata 160Gb) was sda and now it's sde

the esata 750 Gb seagate disks were sdb, sdc, sdd, sde and now they are sda,  sdb, sdc, sdd

the usb disks remained at sdf and sdg

the esata disks are all added to a vmware machine, so this is a problem.

I had rebooted several times and the logical names were the same - particularly, the esata disks had all been added to the vm and remained at sdb-sde through reboots.

before the last reboot I added the two wd 500Gb USB disks to a different virtual machine.

after reboot, they had changed.

below is the output of lshw - first is the current output and below is the earlier output.

I appreciate any help or mitigation ideas.  Is there a way to lock the dev to a particular disk device.  I recall this can be done with network adapters in /etc/iftab, for instance.

much thanks,
joseph

root@dabuntu:/home/wadmin# lshw -C disk
  *-disk                  
       description: SCSI Disk
       product: 5000AAKS Externa
       vendor: WD
       physical id: 0.0.0
       bus info: scsi@8:0.0.0
       logical name: /dev/sdf
       version: 101a
       serial: WD-WCAPW0363325
       size: 465GB
       configuration: ansiversion=4
  *-disk
       description: SCSI Disk
       product: 5000AAKS Externa
       vendor: WD
       physical id: 0.0.0
       bus info: scsi@11:0.0.0
       logical name: /dev/sdg
       version: 101a
       serial: WD-WCAPW0762959
       size: 465GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4
  *-disk:0
       description: SCSI Disk
       product: Seagate FreeAgen
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.AF
       serial: 5QD2DZXD
       size: 698GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:1
       description: SCSI Disk
       product: Seagate FreeAgen
       vendor: ATA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 3.AF
       serial: 5QD2QJQ2
       size: 698GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:2
       description: SCSI Disk
       product: Seagate FreeAgen
       vendor: ATA
       physical id: 2
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: 3.AF
       serial: 5QD12E0F
       size: 698GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:3
       description: SCSI Disk
       product: Seagate FreeAgen
       vendor: ATA
       physical id: 3
       bus info: scsi@3:0.0.0
       logical name: /dev/sdd
       version: 3.AF
       serial: 5QD2HCEL
       size: 698GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: DVD reader
       product: CDRWDVD TS-H492C
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: DE02
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: WDC WD1600JS-75N
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@9:0.0.0
       logical name: /dev/sde
       version: 10.0
       serial: WD-WCANM5764161
       size: 149GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5


=== earlier lshw

 *-disk
       description: SCSI Disk
       product: 5000AAKS Externa
       vendor: WD
       physical id: 0.0.0
       bus info: scsi@10:0.0.0
       logical name: /dev/sdf
       version: 101a
       serial: WD-WCAPW0363325
       size: 465GB
       configuration: ansiversion=4
  *-disk
       description: SCSI Disk
       product: 5000AAKS Externa
       vendor: WD
       physical id: 0.0.0
       bus info: scsi@11:0.0.0
       logical name: /dev/sdg
       version: 101a
       serial: WD-WCAPW0762959
       size: 465GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4
  *-disk:0
       description: SCSI Disk
       product: Seagate FreeAgen
       vendor: ATA
       physical id: 0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
       version: 3.AF
       serial: 5QD2DZXD
       size: 698GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:1
       description: SCSI Disk
       product: Seagate FreeAgen
       vendor: ATA
       physical id: 1
       bus info: scsi@7:0.0.0
       logical name: /dev/sdc
       version: 3.AF
       serial: 5QD2QJQ2
       size: 698GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:2
       description: SCSI Disk
       product: Seagate FreeAgen
       vendor: ATA
       physical id: 2
       bus info: scsi@8:0.0.0
       logical name: /dev/sdd
       version: 3.AF
       serial: 5QD12E0F
       size: 698GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:3
       description: SCSI Disk
       product: Seagate FreeAgen
       vendor: ATA
       physical id: 3
       bus info: scsi@9:0.0.0
       logical name: /dev/sde
       version: 3.AF
       serial: 5QD2HCEL
       size: 698GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: DVD reader
       product: CDRWDVD TS-H492C
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: DE02
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: WDC WD1600JS-75N
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 10.0
       serial: WD-WCANM5764161
       size: 149GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5

---

### Post by dcstar on 2008-02-20
> **4ms said:**
> hello team,

on reboot the logical volumes on most of my disks changed.  This had happened earlier when virtual machines went haywire and so I had checked.

the root system disk (internal sata 160Gb) was sda and now it's sde

the esata 750 Gb seagate disks were sdb, sdc, sdd, sde and now they are sda,  sdb, sdc, sdd
.........

If you label the partitions on your disks then they will always be mounted by the label names (by Ubuntu, at least), otherwise UUIDs are the only things "guaranteed" to be unique.

Designation allocations can change with different kernels, different modules, updates etc. so you cannot assume that they will be constant.

It may also be possible the way your motherboard allocates resources such as IRQs will change things as the kernel probes probably go in some set order.

---

### Post by 4ms on 2008-02-20
David,

thank you very much for the quick reply.

If there is no solution, then at least I have an answer.

Is it possible to label the raw disks rather than partitions to have this behavior?  I mount all four of the esata and both of the usb directly as raw disks into vm's.

Man this is troublesome.  I rebooted today and the internal sata (wd 160Gb) became sda again - and just for grins I rebooted again and it's back at sde...

to mitigate I have to delete and re-add all of the esata disks in the vm.  I'll reboot again, maybe it's every other time instead of random...

Any other thoughts appreciated.

again, much thanks,
joseph

---

### Post by 4ms on 2008-02-20
team, quick update

I rebooted & cycled power several times and the internal sata (ubuntu root - wd160) stayed as sde.

So at least it looks like it mostly stays the same.

I would still very much appreciate any advice on how to ensure that assigned luns are persistent or other mitigation thoughts.

thanks again,
joseph

---

### Post by 4ms on 2008-02-21
Also, 

Today I found an earlier thread that I did not see when I was searching.
I outlines a similar issue at:
:Hard Disk Order"
[http://ubuntuforums.org/showthread.php?p=4377113](http://ubuntuforums.org/showthread.php?p=4377113)

joseph

---

