---
title: "cdrom and burner problems"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by morlaa on 2005-05-08
hi

i have strange problems with my cd/drives
on my i386 i have one cdrom-drive and a cd-burner
both are recognised as /dev/hd[bd]

i can mount data-cds

but i can not listen to audio-cds or copy them
cdplay sais : nodisk
i did put the dma =on in hdparm.conf but it did not help 

and i can not burn anything
gnomebaker, cdrecord, burn, cdrdao nothing worked
cdrecord dev=ATA: scanbus probes /dev/hda for some time: 
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.

and then exits.

dmesg sais:    

scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 6.2.36
scsi: unknown opcode 0x01

ide0: BM-DMA at 0xb800-0xb807, BIOS settings: hda:DMA, hdb:DMA
ide1: BM-DMA at 0xb808-0xb80f, BIOS settings: hdc:DMA, hdd:DMA
hdb: TEAC CD-W552D, ATAPI CD/DVD-ROM drive
hdc: Maxtor 53073U6, ATA DISK drive
hdd: 54X CD-ROM, ATAPI CD/DVD-ROM drive
hdb: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
hdd: ATAPI 52X CD-ROM drive, 128kB Cache

hdb: lost interrupt

 thanx for your advice

morlaa

---

