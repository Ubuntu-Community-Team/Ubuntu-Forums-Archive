---
title: "Cannot detect  \dev\sda in installation menu"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by ScottyDawg on 2010-10-24
Hi 

I am trying to install ubuntu 10.10 on my system, i currently have window 7 installed on my system. I have two sata drives one 230gb and 1.5TB disks. windows 7 is installed on the 230gb drive. The plan is to dual boot the first disk with windows7 & Ubuntu 

 I have resized the partition within windows so that their is an available 128gb of unallocated space. I boot into Ubuntu using USB and select the option to install ubuntu i get to the section on where you want to install and select and specify a location but the only dev in the list is sdb which is the 1.5tb disk. but the boot loader does have the option for both sda and sdb 

so I did some further digging around and tried update-pciids and update-usbids these did download new updates but did not solve the issue.

I also read that changing the SATA mode in the BIOS can help but this stopped me from booting into windows 7 

Did a  sudo lspci -nnv  and have copied the controller information below.

02:00.0 SATA controller [0106]: JMicron Technology Corp. JMB361 AHCI/IDE [197b:2361] (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device [1043:824f]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fe9fe000 (32-bit, non-prefetchable) [size=8K]
    Expansion ROM at fe9e0000 [disabled] [size=64K]
    Capabilities: [68] Power Management version 2
    Capabilities: [50] Express Legacy Endpoint, MSI 01
    Kernel driver in use: ahci
    Kernel modules: ahci

02:00.1 IDE interface [0101]: JMicron Technology Corp. JMB361 AHCI/IDE [197b:2361] (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device [1043:824f]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at dc00 [size=8]
    I/O ports at d880 [size=4]
    I/O ports at d800 [size=8]
    I/O ports at d480 [size=4]
    I/O ports at d400 [size=16]
    Capabilities: [68] Power Management version 2
    Kernel driver in use: pata_jmicron
    Kernel modules: pata_jmicron

also did a ls -l /dev/disk/by-id/ and this returns 

lrwxrwxrwx 1 root root  9 2010-10-24 21:19 ata-ST31500341AS_9VS4ABCR -> ../../sdb
lrwxrwxrwx 1 root root  9 2010-10-24 21:18 ata-WDC_WD3200JS-00PDB0_WD-WCAPD2058742 -> ../../sda
lrwxrwxrwx 1 root root 10 2010-10-24 20:49 ata-WDC_WD3200JS-00PDB0_WD-WCAPD2058742-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-10-24 20:50 ata-WDC_WD3200JS-00PDB0_WD-WCAPD2058742-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 2010-10-24 21:19 scsi-SATA_ST31500341AS_9VS4ABCR -> ../../sdb
lrwxrwxrwx 1 root root  9 2010-10-24 21:18 scsi-SATA_WDC_WD3200JS-00_WD-WCAPD2058742 -> ../../sda
lrwxrwxrwx 1 root root 10 2010-10-24 20:49 scsi-SATA_WDC_WD3200JS-00_WD-WCAPD2058742-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-10-24 20:50 scsi-SATA_WDC_WD3200JS-00_WD-WCAPD2058742-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 2010-10-24 21:18 usb-Freecom_DataBar_USB2.0_907A14000028-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 2010-10-24 21:29 usb-Freecom_DataBar_USB2.0_907A14000028-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 2010-10-24 21:19 wwn-0x5000c50026daffdc -> ../../sdb

as you can see the devices are detected but for some reason it cannot detect during the installtion am i missing somthing obvious? any help i am really keen to install ubuntu but cannot remove windows 7 as i game a lot. 

thanks in advance 

scottyDAwg

---

