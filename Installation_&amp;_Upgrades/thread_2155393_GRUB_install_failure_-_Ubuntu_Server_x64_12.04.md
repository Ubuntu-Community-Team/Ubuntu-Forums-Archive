---
title: "GRUB install failure - Ubuntu Server x64 12.04"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by MarcusL on 2013-06-18
UPDATE #3: I have got GRUB to install... my bad since my experience with Ubuntu is very limited. I had to point the GRUB install to /dev/sdg manually then it worked... doh!
Thank you for all your help!

UPDATE #2:
I managed to get rid of the error by unplugging the USB CD ROM and disabling the Floppy from the boot sequence.

Now i am taken to BusyBox after the boot. I have tried all steps in [this post]("http://ubuntuforums.org/showthread.php?t=1561735") and [this post]("http://www.tuxtrix.com/2009/12/solving-busybox-black-screen-problem-in.html"), but to no avail. 

Any suggestions welcome. Insanity is setting in now after 8 hrs of this game!

M

************************************************************************
UPDATE:
I got the GRUB to install on /dev/sdg which is where it should go. Now on after post I get "[COLOR=#000000][FONT=DejaVu Sans]**error: fd0 read error" **[/FONT][/COLOR]per the info in [this thread]("https://bugzilla.redhat.com/show_bug.cgi?id=753643"). I have a P5K Deluxe mobo like the last post in the attached. 

I have disabled the floppy from the boot sequence in the BIOS, but now after the above error the system boots into BusyBox.

Prior to this, the box was running Ubuntu 11.04 with same config except it had 10 2TB Green drives and an LSI SAS3444E card instead of the adaptec 6405E (the LSI saw the drives as 2TB). 

Not sure where to go from here. Any help is appreciated.

*******************************************************************
Hi all,
I am installing Ubuntu 12.04 on a box I built. The installation sees all drives and allows me to partition OK, but when the GRUB attempts to install, I get a critical failure. Selecting the drive during the partitioning process works fine with all drives showing. The drive formats OK too, I have tried installing using the guided partition + LVM set up (default) and I allocate the whole drive to the process. The system creates 3 partitions, BOOT, SWAP & HOME.

Essentially the server is made up of:
ASUS p5K Deluxe mobo, latest BIOS
Adaptec 6405E SAS controller (set up as JBOD)
10x WD Black 4TB HDDs - 6 on onboard controllers, 4 on Adaptec
1x WD Blue 500GB IDE drive installed on IDE controller, set up in BIOS as first HDD Boot drive
USB DVD Player

I have booted with Try Ubuntu from the Desktop installation CD to run some of the diags below.

Here's the output of sudo lshw -short
```

H/W path            Device      Class       Description
=======================================================
                                system      P5K Deluxe (To Be Filled By O.E.M.)
/0                              bus         P5K Deluxe
/0/0                            memory      64KiB BIOS
/0/4                            processor   Intel(R) Core(TM)2 Extreme CPU Q6850
/0/4/5                          memory      128KiB L1 cache
/0/4/6                          memory      8MiB L2 cache
/0/3a                           memory      8GiB System Memory
/0/3a/0                         memory      2GiB DIMM DDR Synchronous 800 MHz (1
/0/3a/1                         memory      2GiB DIMM DDR Synchronous 800 MHz (1
/0/3a/2                         memory      2GiB DIMM DDR Synchronous 800 MHz (1
/0/3a/3                         memory      2GiB DIMM DDR Synchronous 800 MHz (1
/0/100                          bridge      82G33/G31/P35/P31 Express DRAM Contr
/0/100/1                        bridge      82G33/G31/P35/P31 Express PCI Expres
/0/100/1/0          scsi11      storage     Adaptec
/0/100/1/0/1.0.0    /dev/sdh    disk        3999GB WD4001FAEX-00MJR
/0/100/1/0/1.0.0/1  /dev/sdh1   volume      3724GiB Linux RAID partition
/0/100/1/0/1.1.0    /dev/sdi    disk        3999GB WD4001FAEX-00MJR
/0/100/1/0/1.1.0/1  /dev/sdi1   volume      3724GiB Linux RAID partition
/0/100/1/0/1.2.0    /dev/sdj    disk        3999GB WD4001FAEX-00MJR
/0/100/1/0/1.2.0/1  /dev/sdj1   volume      3724GiB Linux RAID partition
/0/100/1/0/1.3.0    /dev/sdk    disk        3999GB WD4001FAEX-00MJR
/0/100/1/0/1.3.0/1  /dev/sdk1   volume      3724GiB Linux RAID partition
/0/100/1a                       bus         82801I (ICH9 Family) USB UHCI Contro
/0/100/1a.1                     bus         82801I (ICH9 Family) USB UHCI Contro
/0/100/1a.2                     bus         82801I (ICH9 Family) USB UHCI Contro
/0/100/1a.7                     bus         82801I (ICH9 Family) USB2 EHCI Contr
/0/100/1b                       multimedia  82801I (ICH9 Family) HD Audio Contro
/0/100/1c                       bridge      82801I (ICH9 Family) PCI Express Por
/0/100/1c/0                     display     Redwood [Radeon HD 5670]
/0/100/1c/0.1                   multimedia  Redwood HDMI Audio [Radeon HD 5000 S
/0/100/1c.4                     bridge      82801I (ICH9 Family) PCI Express Por
/0/100/1c.4/0                   storage     JMB363 SATA/IDE Controller
/0/100/1c.4/0.1                 storage     JMB363 SATA/IDE Controller
/0/100/1c.5                     bridge      82801I (ICH9 Family) PCI Express Por
/0/100/1c.5/0       eth0        network     88E8056 PCI-E Gigabit Ethernet Contr
/0/100/1d                       bus         82801I (ICH9 Family) USB UHCI Contro
/0/100/1d.1                     bus         82801I (ICH9 Family) USB UHCI Contro
/0/100/1d.2                     bus         82801I (ICH9 Family) USB UHCI Contro
/0/100/1d.7                     bus         82801I (ICH9 Family) USB2 EHCI Contr
/0/100/1e                       bridge      82801 PCI Bridge
/0/100/1e/3                     bus         FW322/323
/0/100/1e/4         eth1        network     RTL-8110SC/8169SC Gigabit Ethernet
/0/100/1f                       bridge      82801IR (ICH9R) LPC Interface Contro
/0/100/1f.2                     storage     82801IR/IO/IH (ICH9R/DO/DH) 6 port S
/0/100/1f.3                     bus         82801I (ICH9 Family) SMBus Controlle
/0/1                scsi0       storage     
/0/1/0.0.0          /dev/sda    disk        4TB WDC WD4001FAEX-0
/0/1/0.0.0/1        /dev/sda1   volume      3726GiB Linux RAID partition
/0/2                scsi1       storage     
/0/2/0.0.0          /dev/sdb    disk        4TB WDC WD4001FAEX-0
/0/2/0.0.0/1        /dev/sdb1   volume      3726GiB Linux RAID partition
/0/3                scsi2       storage     
/0/3/0.0.0          /dev/sdc    disk        4TB WDC WD4001FAEX-0
/0/3/0.0.0/1        /dev/sdc1   volume      3726GiB Linux RAID partition
/0/5                scsi8       storage     
/0/5/0.0.0          /dev/cdrom  disk        DVD RW AD-7581S
/0/5/0.0.0/0        /dev/cdrom  disk        
/0/5/0.0.0/0/2                  volume      15EiB Windows FAT volume
/0/6                scsi3       storage     
/0/6/0.0.0          /dev/sdd    disk        4TB WDC WD4001FAEX-0
/0/6/0.0.0/1        /dev/sdd1   volume      3726GiB Linux RAID partition
/0/7                scsi4       storage     
/0/7/0.0.0          /dev/sde    disk        4TB WDC WD4001FAEX-0
/0/7/0.0.0/1        /dev/sde1   volume      3726GiB Linux RAID partition
/0/8                scsi5       storage     
/0/8/0.0.0          /dev/sdf    disk        4TB WDC WD4001FAEX-0
/0/8/0.0.0/1        /dev/sdf1   volume      3726GiB Linux RAID partition
/0/9                scsi9       storage     
/0/9/0.0.0          /dev/sdg    disk        500GB WDC WD5000AAKB-0
/0/9/0.0.0/1        /dev/sdg1   volume      243MiB Linux filesystem partition
/0/9/0.0.0/2        /dev/sdg2   volume      465GiB Extended partition
/0/9/0.0.0/2/5      /dev/sdg5   volume      465GiB Linux LVM Physical Volume par
/1                  wlan0       network     Wireless interface

```

Here's the output of sudo lshw -class disk -class storage

```

  *-storage               
       description: RAID bus controller
       product: Adaptec
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: scsi11
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: storage pm msi pciexpress msix bus_master cap_list rom emulated
       configuration: driver=aacraid latency=0
       resources: irq:16 memory:fe400000-fe7fffff memory:fe3ff800-fe3fffff memory:fe3ff400-fe3ff4ff memory:fe380000-fe3bffff
     *-disk:0
          description: SCSI Disk
          product: WD4001FAEX-00MJR
          vendor: WDC
          physical id: 1.0.0
          bus info: scsi@11:1.0.0
          logical name: /dev/sdh
          version: 01.0
          serial: WD-WCC4A0001418
          size: 3724GiB (3999GB)
          capabilities: gpt-1.00 partitioned partitioned:gpt
          configuration: ansiversion=5 guid=2ae26d92-d7e7-483b-b6a0-0909c53e1744
     *-disk:1
          description: SCSI Disk
          product: WD4001FAEX-00MJR
          vendor: WDC
          physical id: 1.1.0
          bus info: scsi@11:1.1.0
          logical name: /dev/sdi
          version: 01.0
          serial: WD-WCC130287432
          size: 3724GiB (3999GB)
          capabilities: gpt-1.00 partitioned partitioned:gpt
          configuration: ansiversion=5 guid=0ba5ede5-99da-4912-98bb-2f24bded42a7
     *-disk:2
          description: SCSI Disk
          product: WD4001FAEX-00MJR
          vendor: WDC
          physical id: 1.2.0
          bus info: scsi@11:1.2.0
          logical name: /dev/sdj
          version: 01.0
          serial: WD-WCC130291704
          size: 3724GiB (3999GB)
          capabilities: gpt-1.00 partitioned partitioned:gpt
          configuration: ansiversion=5 guid=74fa3b8b-0b58-4413-86da-c94be7bde81f
     *-disk:3
          description: SCSI Disk
          product: WD4001FAEX-00MJR
          vendor: WDC
          physical id: 1.3.0
          bus info: scsi@11:1.3.0
          logical name: /dev/sdk
          version: 01.0
          serial: WD-WCC130192331
          size: 3724GiB (3999GB)
          capabilities: gpt-1.00 partitioned partitioned:gpt
          configuration: ansiversion=5 guid=78622026-ef44-4439-ba78-04b31975ecbe
  *-storage
       description: SATA controller
       product: JMB363 SATA/IDE Controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list rom
       configuration: driver=ahci latency=0
       resources: irq:16 memory:fe9fe000-fe9fffff memory:f0000000-f000ffff
  *-ide
       description: IDE interface
       product: JMB363 SATA/IDE Controller
       vendor: JMicron Technology Corp.
       physical id: 0.1
       bus info: pci@0000:03:00.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: ide pm bus_master cap_list
       configuration: driver=pata_jmicron latency=0
       resources: irq:17 ioport:cc00(size=8) ioport:c880(size=4) ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=16)
  *-storage
       description: SATA controller
       product: 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode]
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: storage msi pm ahci_1.0 bus_master cap_list
       configuration: driver=ahci latency=0
       resources: irq:44 ioport:9c00(size=8) ioport:9880(size=4) ioport:9800(size=8) ioport:9480(size=4) ioport:9400(size=32) memory:fe2fe800-fe2fefff
  *-scsi:0
       physical id: 1
       logical name: scsi0
       capabilities: emulated
     *-disk
          description: ATA Disk
          product: WDC WD4001FAEX-0
          vendor: Western Digital
          physical id: 0.0.0
          bus info: scsi@0:0.0.0
          logical name: /dev/sda
          version: 01.0
          serial: WD-WCC4A0000874
          size: 3726GiB (4TB)
          capabilities: gpt-1.00 partitioned partitioned:gpt
          configuration: ansiversion=5 guid=95e7b10e-02c7-4da5-acb1-90d448f680de
  *-scsi:1
       physical id: 2
       logical name: scsi1
       capabilities: emulated
     *-disk
          description: ATA Disk
          product: WDC WD4001FAEX-0
          vendor: Western Digital
          physical id: 0.0.0
          bus info: scsi@1:0.0.0
          logical name: /dev/sdb
          version: 01.0
          serial: WD-WCC130226567
          size: 3726GiB (4TB)
          capabilities: gpt-1.00 partitioned partitioned:gpt
          configuration: ansiversion=5 guid=6116efe6-0aaa-42b1-b63f-c26a66fd3896
  *-scsi:2
       physical id: 3
       logical name: scsi2
       capabilities: emulated
     *-disk
          description: ATA Disk
          product: WDC WD4001FAEX-0
          vendor: Western Digital
          physical id: 0.0.0
          bus info: scsi@2:0.0.0
          logical name: /dev/sdc
          version: 01.0
          serial: WD-WCC130287307
          size: 3726GiB (4TB)
          capabilities: gpt-1.00 partitioned partitioned:gpt
          configuration: ansiversion=5 guid=37d60c3e-7143-40fe-8837-82b94645b1db
  *-scsi:3
       physical id: 5
       bus info: usb@1:6
       logical name: scsi8
       capabilities: emulated scsi-host
       configuration: driver=usb-storage
     *-cdrom
          description: DVD-RAM writer
          product: DVD RW AD-7581S
          vendor: Optiarc
          physical id: 0.0.0
          bus info: scsi@8:0.0.0
          logical name: /dev/cdrom
          logical name: /dev/cdrw
          logical name: /dev/dvd
          logical name: /dev/dvdrw
          logical name: /dev/sr0
          logical name: /cdrom
          version: 4H03
          capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
          configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
        *-medium
             physical id: 0
             logical name: /dev/cdrom
             logical name: /cdrom
             capabilities: partitioned partitioned:dos
             configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=405a5c85 state=mounted
  *-scsi:4
       physical id: 6
       logical name: scsi3
       capabilities: emulated
     *-disk
          description: ATA Disk
          product: WDC WD4001FAEX-0
          vendor: Western Digital
          physical id: 0.0.0
          bus info: scsi@3:0.0.0
          logical name: /dev/sdd
          version: 01.0
          serial: WD-WCC130291776
          size: 3726GiB (4TB)
          capabilities: gpt-1.00 partitioned partitioned:gpt
          configuration: ansiversion=5 guid=ba81c2f6-a128-4494-b152-a3a347491126
  *-scsi:5
       physical id: 7
       logical name: scsi4
       capabilities: emulated
     *-disk
          description: ATA Disk
          product: WDC WD4001FAEX-0
          vendor: Western Digital
          physical id: 0.0.0
          bus info: scsi@4:0.0.0
          logical name: /dev/sde
          version: 01.0
          serial: WD-WCC130216797
          size: 3726GiB (4TB)
          capabilities: gpt-1.00 partitioned partitioned:gpt
          configuration: ansiversion=5 guid=1a78f7b5-5aea-43f3-8c24-b5b3b98fe46c
  *-scsi:6
       physical id: 8
       logical name: scsi5
       capabilities: emulated
     *-disk
          description: ATA Disk
          product: WDC WD4001FAEX-0
          vendor: Western Digital
          physical id: 0.0.0
          bus info: scsi@5:0.0.0
          logical name: /dev/sdf
          version: 01.0
          serial: WD-WCC130287275
          size: 3726GiB (4TB)
          capabilities: gpt-1.00 partitioned partitioned:gpt
          configuration: ansiversion=5 guid=dac655a6-be68-42e6-9dde-4fe8ca1f20c1
  *-scsi:7
       physical id: 9
       logical name: scsi9
       capabilities: emulated
     *-disk
          description: ATA Disk
          product: WDC WD5000AAKB-0
          vendor: Western Digital
          physical id: 0.0.0
          bus info: scsi@9:0.0.0
          logical name: /dev/sdg
          version: 05.0
          serial: WD-WCASYF841013
          size: 465GiB (500GB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 signature=00057e85

```

Any suggestions are highly appreciated. I am stumped as to why this is not working (I am not a Ubuntu/Linux expert, by the way!).

---

### Post by oldfred on 2013-06-18
I do not know servers with RAID, but are you just booting sdg, your 500GB IDE drive as a separate system and then mounting the RAID.

Server install is not a live installer. Download Ubuntu desktop and add Boot-Repair or download the Boot-Repair liveCD version and post link it creates when you run BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

