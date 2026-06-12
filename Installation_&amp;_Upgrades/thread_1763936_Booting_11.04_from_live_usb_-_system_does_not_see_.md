---
title: "Booting 11.04 from live usb - system does not see hard drive"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by vtanase on 2011-05-21
Hello,

I have a dual boot machine with WinXP/Linux Mint on it. I am looking to erase both of them and put up Ubuntu 11.04.

I have chosen to go with a live USB install for this. The live USB boots fine and everything seems usable. However, when I tried to install it would tell me that I do not have 4GB available for the install which seemed a bit weird since I have a 160GB Maxtor HDD.

After digging around a bit I realized that the system does not see my hard drive. Running fdisk -l would only show the USB drive that I am booting from and not the main HDD.

I tried to have a look in /dev to see if my HDD is there and not mounted. But aside from sda which is the USB I did not find an sdb or hd entry.

Has anyone encountered a similar problem while trying to install Ubuntu 11.04? Can anyone provide some suggestions to be able to solve this?

Thanks in advance.
Vlad

P.S.: The HDD works fine, I can see it in BIOS and in the other 2 OS-es that I have installed.

---

### Post by lmarmisa on 2011-05-21
Welcome to the forums.

Please, open a terminal, type this command and post here the results:

```

sudo lshw -class storage -class disk

```

---

### Post by vtanase on 2011-05-21
This is the output I get:

```

ubuntu@ubuntu:~$ sudo lshw -class storage -class disk
  *-ide UNCLAIMED         
       description: IDE interface
       product: VIA Technologies, Inc.
       vendor: VIA Technologies, Inc.
       physical id: f
       bus info: pci@0000:00:0f.0
       version: 07
       width: 32 bits
       clock: 33MHz
       capabilities: ide pm cap_list
       configuration: latency=32
       resources: ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
  *-scsi
       physical id: 3
       bus info: usb@1:2
       logical name: scsi0
       capabilities: emulated scsi-host
       configuration: driver=usb-storage
     *-disk
          description: SCSI Disk
          product: Cruzer Micro
          vendor: SanDisk
          physical id: 0.0.0
          bus info: scsi@0:0.0.0
          logical name: /dev/sda
          version: 6.51
          serial: u
          size: 1909MiB (2002MB)
          capabilities: removable
        *-medium
             physical id: 0
             logical name: /dev/sda
             size: 1909MiB (2002MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=49ebc834

```

---

### Post by lmarmisa on 2011-05-21
> **vtanase said:**
> This is the output I get:

```

ubuntu@ubuntu:~$ sudo lshw -class storage -class disk
  *-ide [COLOR="Red"]UNCLAIMED[/COLOR]         
       description: IDE interface
       product: VIA Technologies, Inc.
       vendor: VIA Technologies, Inc.
       physical id: f
       bus info: pci@0000:00:0f.0
       version: 07
       width: 32 bits
       clock: 33MHz
       capabilities: ide pm cap_list
       configuration: latency=32
       resources: ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
  *-scsi
       physical id: 3
       bus info: usb@1:2
       logical name: scsi0
       capabilities: emulated scsi-host
       configuration: driver=usb-storage
     *-disk
          description: SCSI Disk
          product: Cruzer Micro
          vendor: SanDisk
          physical id: 0.0.0
          bus info: scsi@0:0.0.0
          logical name: /dev/sda
          version: 6.51
          serial: u
          size: 1909MiB (2002MB)
          capabilities: removable
        *-medium
             physical id: 0
             logical name: /dev/sda
             size: 1909MiB (2002MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=49ebc834

```

The Via Tech IDE/SATA controller of your motherboard is not supported by the Ubuntu 11.04 installer. This is the reason because your HDD is not detected.

---

### Post by vtanase on 2011-05-21
> **lmarmisa said:**
> The Via Tech IDE/SATA controller of your motherboard is not supported by the Ubuntu 11.04 installer. This is the reason because your HDD is not detected.

Thanks for your timely reply. This seems quite plausible. Is there anything I can do to be able to move on with the installation, or should I just give up on this and try again with the next version?

---

### Post by lmarmisa on 2011-05-21
> **vtanase said:**
> Thanks for your timely reply. This seems quite plausible. Is there anything I can do to be able to move on with the installation, or should I just give up on this and try again with the next version?

According to my experience, Ubuntu and Via Tech do not match very well. I got many problems with Ubuntu and a couple of Via Tech motherboards some time ago. Maybe the Ubuntu Alternate CD could give you a solution. I do not know.

---

### Post by wendelliam on 2011-09-25
I am having a similar problem. I boot from the USB installer and the only option I see is to install into a new partition on my 2TB HD. I have two other HDs in my system, including one with a partition I made for Ubuntu in Windows 7, but Ubuntu does not present these as install destination options.I ran the command you suggested above and got this output. Any help is much appreciated

```

ubuntu@ubuntu:~$ sudo lshw -class storage -class disk
PCI (sysfs)  
  *-ide UNCLAIMED         
       description: IDE interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 12
       width: 32 bits
       clock: 33MHz
       capabilities: ide pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:dc00(size=8) ioport:d880(size=4) ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=16) memory:f7eff800-f7efffff memory:f7ee0000-f7eeffff
  *-storage
       description: SATA controller
       product: JMB362/JMB363 Serial ATA Controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list
       configuration: driver=ahci latency=0
       resources: irq:18 memory:f7afe000-f7afffff
  *-ide
       description: IDE interface
       product: JMB362/JMB363 Serial ATA Controller
       vendor: JMicron Technology Corp.
       physical id: 0.1
       bus info: pci@0000:03:00.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: ide pm bus_master cap_list
       configuration: driver=pata_jmicron latency=0
       resources: irq:19 ioport:bc00(size=8) ioport:b880(size=4) ioport:b800(size=8) ioport:b480(size=4) ioport:b400(size=16)
  *-ide:0
       description: IDE interface
       product: 5 Series/3400 Series Chipset 4 port SATA IDE Controller
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       logical name: scsi0
       logical name: scsi1
       version: 06
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: driver=ata_piix latency=0
       resources: irq:21 ioport:8c00(size=8) ioport:8880(size=4) ioport:8800(size=8) ioport:8480(size=4) ioport:8400(size=16) ioport:8080(size=16)
     *-disk
          description: ATA Disk
          product: WDC WD20EARS-00M
          vendor: Western Digital
          physical id: 0
          bus info: scsi@0:0.0.0
          logical name: /dev/sda
          version: 51.0
          serial: WD-WMAZA1833553
          size: 1863GiB (2TB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 signature=fec4441d
     *-cdrom
          description: DVD-RAM writer
          product: iHAS424   B
          vendor: ATAPI
          physical id: 1
          bus info: scsi@1:0.0.0
          logical name: /dev/cdrom
          logical name: /dev/cdrw
          logical name: /dev/dvd
          logical name: /dev/dvdrw
          logical name: /dev/scd0
          logical name: /dev/sr0
          version: GL15
          capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
          configuration: ansiversion=5 status=nodisc
  *-ide:1
       description: IDE interface
       product: 5 Series/3400 Series Chipset 2 port SATA IDE Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 06
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list
       configuration: driver=ata_piix latency=0
       resources: irq:21 ioport:9c00(size=8) ioport:9880(size=4) ioport:9800(size=8) ioport:9480(size=4) ioport:9400(size=16) ioport:9080(size=16)
  *-scsi
       physical id: 5
       bus info: usb@1:1.3
       logical name: scsi6
       capabilities: emulated scsi-host
       configuration: driver=usb-storage
     *-disk
          description: SCSI Disk
          physical id: 0.0.0
          bus info: scsi@6:0.0.0
          logical name: /dev/sdb
          size: 14GiB (15GB)
          capabilities: partitioned partitioned:dos
          configuration: signature=c3072e18


```

---

