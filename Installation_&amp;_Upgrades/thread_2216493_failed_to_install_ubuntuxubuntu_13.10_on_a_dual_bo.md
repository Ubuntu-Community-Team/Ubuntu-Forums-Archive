---
title: "failed to install ubuntu/xubuntu 13.10 on a dual boot machine, Compaq Presario 2516"
date: 2014-04-12
forum: Installation &amp; Upgrades
---

### Post by paulo_candeias on 2014-04-12
Preamble:
I am a long time user of computers but a complete newbie in what concerns ubuntu and dual boot machines...

Actions taken:
I successfully installed ubuntu 12.04.4 LTS on an old laptop ([http://www.cnet.com/products/compaq-presario-2516ea-15-p4-win-xp-home-512-mb-ram-40-gb-hdd-series/](http://www.cnet.com/products/compaq-presario-2516ea-15-p4-win-xp-home-512-mb-ram-40-gb-hdd-series/)), turning it into a dual boot machine alongside windows xp. It turned out that ubuntu is too demanding for this machine and so I decided to install the xubuntu desktop. The machine now runs more smoothly although with some lag still.

Issues found:
Wondering if installing xubuntu 13.10 directly on the machine instead of the xubuntu desktop on top of ubuntu 12.04.4 LTS would mean a better overall performance, I prepared a LiveUSB and then the problems started. I used many diferent tools (Universal USB Installer and Unetbootin in windows, and also created a startup disk directly in ubuntu). The result was always the same: I ended up with a BusyBox v1.20.2 (ubuntu 1:1.20.0-8.1ubuntu1) black screen and an initramfs prompt.

What I know:
I executed blkid and found only one disk, the hardrive, with three partitions: /dev/sda1 (ntfs), /dev/sda5 (swap) and /dev/sda6 (ext4). The LiveUSB is missing, I think that something like /dev/sdb1 should appear in the list. If I try to mount /dev/sdb1 I get the following error message:

Can't read '/etc/fstab': no such file or directory

If I do exit I end up with a long error message. I even tried with other variants of ubuntu (lubuntu was one of them) but to no avail.

What I do not know:
I spent several days looking for a solution all over the internet but could not find one. I think that busybox and initramfs are not to blame but I do not know what the solution is. I was hoping that maybe someone would know.

---

### Post by mörgæs on 2014-04-12
Hi, welcome to the fora.

> **paulo_candeias said:**
> 
I ended up with a BusyBox v1.20.2 (ubuntu 1:1.20.0-8.1ubuntu1) black screen and an initramfs prompt.

When? Attempting to boot from CD/USB or hard disk?

---

### Post by paulo_candeias on 2014-04-12
Hi,

I was trying to install from a LiveUSB like I did in the first time when I installed Ubuntu 12.04.4 LTS. One additional thing, I was not able to install originally Ubuntu 13.10 (only 12.04), maybe because of the same reason I can not do it now, but I did not know that at that time.

---

### Post by mörgæs on 2014-04-12
Please run (using any version of Buntu)
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by paulo_candeias on 2014-04-12
Hi,

I inserted the LiveUSB before running the command. Here goes the output (the labels are in Portuguese):

```

computer
    descrição: Notebook
    produto: Presario 2500            F.fxxx
    fabricante: Hewlett-Packard
    versão: KF.F.13  0
    serial: [REMOVED]
    largura: 32 bits
    configuração: administrator_password=enabled boot=oem-specific chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=[REMOVED]
  *-core
       descrição: Motherboard
       ID físico: 0
     *-firmware
          descrição: BIOS
          fabricante: Phoenix Technologies Ltd.
          ID físico: 0
          versão: KF.F.13
          date: 02/27/2004
          tamanho: 109KiB
          capacidade: 448KiB
          capacidades: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom pcmciaboot edd int13floppynec int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp
     *-cpu
          descrição: CPU
          produto: Intel(R) Pentium(R) 4 CPU 2.53GHz
          fabricante: Intel Corp.
          ID físico: 4
          informações do barramento: cpu@0
          versão: 15.2.7
          slot: WMT478/NWD
          tamanho: 2533MHz
          capacidade: 2533MHz
          largura: 32 bits
          capacidades: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuração: id=0
        *-cache:0
             descrição: L2 cache
             ID físico: 8
             slot: L2 Cache
             tamanho: 8KiB
             capacidade: 1MiB
             capacidades: burst internal write-back
        *-cache:1
             descrição: Cache L2
             ID físico: 0
             tamanho: 512KiB
     *-memory
          descrição: Memória do sistema
          ID físico: 1c
          slot: Placa do sistema ou placa-mãe
          tamanho: 512MiB
          capacidade: 1GiB
        *-bank:0
             descrição: DIMM DRAM Síncrono
             ID físico: 0
             slot: J400
             tamanho: 256MiB
             largura: 64 bits
        *-bank:1
             descrição: DIMM DRAM Síncrono
             ID físico: 1
             slot: J401
             tamanho: 256MiB
             largura: 64 bits
     *-pci
          descrição: Host bridge
          produto: RS200 Host Bridge
          fabricante: Hynix Semiconductor (Hyundai Electronics)
          ID físico: 100
          informações do barramento: pci@0000:00:00.0
          versão: 02
          largura: 32 bits
          clock: 66MHz
          configuração: driver=agpgart-ati latency=64
          recursos: irq:0 memória:d4000000-d7ffffff memória:d000b000-d000bfff
        *-pci
             descrição: PCI bridge
             produto: RS200/RS250 AGP Bridge
             fabricante: Hynix Semiconductor (Hyundai Electronics)
             ID físico: 1
             informações do barramento: pci@0000:00:01.0
             versão: 00
             largura: 32 bits
             clock: 66MHz
             capacidades: pci normal_decode bus_master
             recursos: porta de E/S:9000(tamanho=4096) memória:d0300000-d03fffff memória:d8000000-dfffffff
           *-display
                descrição: VGA compatible controller
                produto: RS200M [Radeon IGP 330M/340M/345M/350M]
                fabricante: Hynix Semiconductor (Hyundai Electronics)
                ID físico: 5
                informações do barramento: pci@0000:01:05.0
                versão: 00
                largura: 32 bits
                clock: 66MHz
                capacidades: agp agp-2.0 pm vga_controller bus_master cap_list rom
                configuração: driver=radeon latency=66 mingnt=8
                recursos: irq:10 memória:d8000000-dfffffff porta de E/S:9000(tamanho=256) memória:d0300000-d030ffff memória:d0320000-d033ffff
        *-usb:0
             descrição: USB controller
             produto: USB 1.1 Controller
             fabricante: ULi Electronics Inc.
             ID físico: 2
             informações do barramento: pci@0000:00:02.0
             versão: 03
             largura: 32 bits
             clock: 33MHz
             capacidades: pm ohci bus_master cap_list
             configuração: driver=ohci-pci latency=64 maxlatency=80
             recursos: irq:10 memória:d0000000-d0000fff
        *-multimedia
             descrição: Multimedia audio controller
             produto: M5451 PCI AC-Link Controller Audio Device
             fabricante: ULi Electronics Inc.
             ID físico: 6
             informações do barramento: pci@0000:00:06.0
             versão: 02
             largura: 32 bits
             clock: 33MHz
             capacidades: pm bus_master cap_list
             configuração: driver=snd_ali5451 latency=64 maxlatency=24 mingnt=2
             recursos: irq:5 porta de E/S:1000(tamanho=256) memória:d0001000-d0001fff
        *-isa
             descrição: ISA bridge
             produto: M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
             fabricante: ULi Electronics Inc.
             ID físico: 7
             informações do barramento: pci@0000:00:07.0
             versão: 00
             largura: 32 bits
             clock: 33MHz
             capacidades: isa pm bus_master cap_list
             configuração: latency=0
        *-communication DISPONÍVEL
             descrição: Modem
             produto: M5457 AC'97 Modem Controller
             fabricante: ULi Electronics Inc.
             ID físico: 8
             informações do barramento: pci@0000:00:08.0
             versão: 00
             largura: 32 bits
             clock: 33MHz
             capacidades: pm generic cap_list
             configuração: latency=64
             recursos: memória:d0002000-d0002fff porta de E/S:1400(tamanho=256)
        *-pcmcia
             descrição: CardBus bridge
             produto: OZ601/6912/711E0 CardBus/SmartCardBus Controller
             fabricante: O2 Micro, Inc.
             ID físico: a
             informações do barramento: pci@0000:00:0a.0
             versão: 00
             largura: 32 bits
             clock: 33MHz
             capacidades: pcmcia bus_master cap_list
             configuração: driver=yenta_cardbus latency=176 maxlatency=5
             recursos: irq:11 memória:d0003000-d0003fff porta de E/S:1800(tamanho=256) porta de E/S:1c00(tamanho=256) memória:2c000000-2fffffff memória:30000000-33ffffff
        *-firewire
             descrição: FireWire (IEEE 1394)
             produto: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
             fabricante: Texas Instruments
             ID físico: c
             informações do barramento: pci@0000:00:0c.0
             versão: 00
             largura: 32 bits
             clock: 33MHz
             capacidades: pm ohci bus_master cap_list
             configuração: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
             recursos: irq:10 memória:d0008000-d00087ff memória:d0004000-d0007fff
        *-usb:1
             descrição: USB controller
             produto: USB 1.1 Controller
             fabricante: ULi Electronics Inc.
             ID físico: f
             informações do barramento: pci@0000:00:0f.0
             versão: 03
             largura: 32 bits
             clock: 33MHz
             capacidades: pm ohci bus_master cap_list
             configuração: driver=ohci-pci latency=64 maxlatency=80
             recursos: irq:10 memória:d0009000-d0009fff
        *-ide
             descrição: IDE interface
             produto: M5229 IDE
             fabricante: ULi Electronics Inc.
             ID físico: 10
             informações do barramento: pci@0000:00:10.0
             versão: c4
             largura: 32 bits
             clock: 33MHz
             capacidades: ide pm bus_master cap_list
             configuração: driver=pata_ali latency=32 maxlatency=4 mingnt=2
             recursos: irq:0 porta de E/S:1f0(tamanho=8) porta de E/S:3f6 porta de E/S:170(tamanho=8) porta de E/S:376 porta de E/S:2000(tamanho=16)
        *-bridge DISPONÍVEL
             descrição: Bridge
             produto: M7101 Power Management Controller [PMU]
             fabricante: ULi Electronics Inc.
             ID físico: 11
             informações do barramento: pci@0000:00:11.0
             versão: 00
             largura: 32 bits
             clock: 33MHz
             capacidades: bridge pm
             configuração: latency=0
        *-network
             descrição: Ethernet interface
             produto: DP83815 (MacPhyter) Ethernet Controller
             fabricante: National Semiconductor Corporation
             ID físico: 12
             informações do barramento: pci@0000:00:12.0
             nome lógico: eth0
             versão: 00
             serial: [REMOVED]
             tamanho: 10Mbit/s
             capacidade: 100Mbit/s
             largura: 32 bits
             clock: 33MHz
             capacidades: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuração: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=10Mbit/s
             recursos: irq:10 porta de E/S:2400(tamanho=256) memória:d000a000-d000afff memória:34000000-3400ffff
     *-network
          descrição: Interface sem fio
          produto: RT2500 Wireless 802.11bg
          fabricante: Ralink corp.
          ID físico: 1
          informações do barramento: pci@0000:02:00.0
          nome lógico: wlan0
          versão: 01
          serial: [REMOVED]
          largura: 32 bits
          clock: 33MHz
          capacidades: pm bus_master cap_list ethernet physical wireless
          configuração: broadcast=yes driver=rt2500pci driverversion=3.11.0-19-generic firmware=N/A ip=[REMOVED] latency=64 link=yes multicast=yes wireless=IEEE 802.11bg
          recursos: irq:11 memória:30000000-30001fff
     *-scsi:0
          ID físico: 2
          nome lógico: scsi0
          capacidades: emulated
        *-disk
             descrição: ATA Disk
             produto: IC25N040ATCS04-0
             fabricante: Hitachi
             ID físico: 0.0.0
             informações do barramento: scsi@0:0.0.0
             nome lógico: /dev/sda
             versão: CA4O
             serial: [REMOVED]
             tamanho: 37GiB (40GB)
             capacidades: partitioned partitioned:dos
             configuração: ansiversion=5 signature=2c922c91
           *-volume:0
                descrição: Windows NTFS volume
                ID físico: 1
                informações do barramento: scsi@0:0.0.0,1
                nome lógico: /dev/sda1
                versão: 3.1
                serial: [REMOVED]
                tamanho: 27GiB
                capacidade: 27GiB
                capacidades: primary bootable ntfs initialized
                configuração: clustersize=4096 created=2001-12-31 23:22:45 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                descrição: Extended partition
                ID físico: 2
                informações do barramento: scsi@0:0.0.0,2
                nome lógico: /dev/sda2
                tamanho: 9591MiB
                capacidade: 9591MiB
                capacidades: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   descrição: Linux swap / Solaris partition
                   ID físico: 5
                   nome lógico: /dev/sda5
                   capacidade: 446MiB
                   capacidades: nofs
              *-logicalvolume:1
                   descrição: Linux filesystem partition
                   ID físico: 6
                   nome lógico: /dev/sda6
                   nome lógico: /
                   capacidade: 9145MiB
                   configuração: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          ID físico: 3
          nome lógico: scsi1
          capacidades: emulated
        *-cdrom
             descrição: DVD reader
             produto: DVD-ROM SD-R2312
             fabricante: TOSHIBA
             ID físico: 0.0.0
             informações do barramento: scsi@1:0.0.0
             nome lógico: /dev/cdrom
             nome lógico: /dev/cdrw
             nome lógico: /dev/dvd
             nome lógico: /dev/sr0
             versão: 1905
             capacidades: removable audio cd-r cd-rw dvd
             configuração: ansiversion=5 status=nodisc
     *-scsi:2
          ID físico: 5
          informações do barramento: usb@2:1
          nome lógico: scsi2
          capacidades: emulated scsi-host
          configuração: driver=usb-storage
        *-disk
             descrição: SCSI Disk
             ID físico: 0.0.0
             informações do barramento: scsi@2:0.0.0
             nome lógico: /dev/sdb
             tamanho: 1940MiB (2034MB)
             capacidades: partitioned partitioned:dos
             configuração: signature=0002c339
           *-volume
                descrição: Windows FAT volume
                fabricante: SYSLINUX
                ID físico: 1
                informações do barramento: scsi@2:0.0.0,1
                nome lógico: /dev/sdb1
                versão: FAT32
                serial: [REMOVED]
                tamanho: 1939MiB
                capacidade: 1939MiB
                capacidades: primary bootable fat initialized
                configuração: FATs=2 filesystem=fat
  *-remoteaccess DISPONÍVEL
       fabricante: Intel
       ID físico: 1
       capacidades: inbound

```

---

### Post by mörgæs on 2014-04-13
You are low on RAM, but apart from this it all looks fine. 
From a live boot, are you able to remove the old Ubuntu partitions with Gparted?

---

### Post by paulo_candeias on 2014-04-13
Hi,

Well, the problem is exactly that, with the LiveUSB I can not get past the busybox/initramfs duo. The USB drive is not visible and I can not mount it.

---

### Post by mörgæs on 2014-04-13
Are you able to install using the [alternate Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by paulo_candeias on 2014-04-16
Hi,

yesterday I finally had the time to experiment with both Xubuntu 12.04.4 LTS and 13.10 on a LiveUSB (using RUFUS-1.4.6 in Win8.1). With the first one I am able to start successfully the laptop and use it (although very slow, I assume that is because I am running it from a 1.1 USB port). With the second one I end up with the BusyBox/initramfs prompt and a message saying that it is "unable to find a medium containing a live file system". Why is it that 12.04.4 LTS can boot but 13.10 cannot?

---

### Post by mörgæs on 2014-04-16
As I mentioned you are low on RAM, and you will probably get the best results using a text-based installer like the alternate ISO.

---

### Post by paulo_candeias on 2014-05-02
Hi,

here goes a summary of my actions towards installing ubuntu on my old Compaq Presario 2516 (dual boot) using an USB drive created in a Windows8.1 machine:

Ubuntu 13.10 - ended up with the busybox/initramfs issue, ubuntu not installed
Xubuntu 13.10 - ended up with the busybox/initramfs issue, ubuntu not installed
Ubuntu 12.04.4 LTS - installed successfully but computer was very, very slow
Xubuntu 12.04.4 LTS - installed successfully, computer responded quite satisfactorily
Lubuntu 14.04.0 LTS - installed successfully, computer responding fast (most of the times)

From the point of view of installing ubuntu (any version) on my old laptop, I would say that the issue is solved. Thanks [COLOR=#000000]mörgæs [/COLOR]for the suggestion of installing Lubuntu and for the links to install other applications.

From the point of view of my initial question, I would say that the issue is not solved. My observations lead me to the conclusion that the LTS versions install ok but the intermediate ones (like 13.10 and others from what I searched in the internet) have something in their installer that remains to be fixed.

---

