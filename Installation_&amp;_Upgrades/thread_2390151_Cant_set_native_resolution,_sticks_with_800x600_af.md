---
title: "Cant set native resolution, sticks with 800x600 after harddisk change"
date: 2018-04-26
forum: Installation &amp; Upgrades
---

### Post by adewilt on 2018-04-26
Hi there,

i've been searching for weeks now, but can't find a solution on any forum.

I have an old laptop, a Samsung EEE PC 1000H using Lubuntu. I always had the native resolution which is 1024x600. 
A few weeks ago a swapped the harddisk to SSD and installed a new Lubuntu. Now the only resolution I can choose is 800x600.
I did manage to lower the DPI so I can use it a bit better, but I would really like to understand how to get back to the proper resolution.

xandr -q shows:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600       75.00* 

The gui 'monitor settings' also only shows 800x600 to choose from.

Extra info:

Uname -a = 4.13.0-38-generic #43~16.04.1-Ubuntu SMP Wed Mar 14 17:46:42 UTC 2018 i686 i686 i686 GNU/Linux

lshw -short:
H/W path         Device     Class          Description
======================================================
                            system         1000H (90OAM0HB83311J3IE12CQ)
/0                          bus            1000H
/0/0                        memory         64KiB BIOS
/0/4                        processor      Intel(R) Atom(TM) CPU N270   @ 1.60GH
/0/4/5                      memory         24KiB L1 cache
/0/4/6                      memory         512KiB L2 cache
/0/4/1.1                    processor      Logical CPU
/0/4/1.2                    processor      Logical CPU
/0/18                       memory         2GiB System Memory
/0/18/0                     memory         2GiB DIMM SDRAM Synchronous
/0/100                      bridge         Mobile 945GSE Express Memory Controll
/0/100/2                    display        Mobile 945GSE Express Integrated Grap
/0/100/2.1                  display        Mobile 945GM/GMS/GME, 943/940GML Expr
/0/100/1b                   multimedia     NM10/ICH7 Family High Definition Audi
/0/100/1c                   bridge         NM10/ICH7 Family PCI Express Port 1
/0/100/1c.1                 bridge         NM10/ICH7 Family PCI Express Port 2
/0/100/1c.1/0    enp3s0     network        AR8121/AR8113/AR8114 Gigabit or Fast 
/0/100/1c.3                 bridge         NM10/ICH7 Family PCI Express Port 4
/0/100/1c.3/0    wlp1s0     network        RT2790 Wireless 802.11n 1T/2R PCIe
/0/100/1d                   bus            NM10/ICH7 Family USB UHCI Controller 
/0/100/1d/1      usb2       bus            UHCI Host Controller
/0/100/1d.1                 bus            NM10/ICH7 Family USB UHCI Controller 
/0/100/1d.1/1    usb3       bus            UHCI Host Controller
/0/100/1d.2                 bus            NM10/ICH7 Family USB UHCI Controller 
/0/100/1d.2/1    usb4       bus            UHCI Host Controller
/0/100/1d.3                 bus            NM10/ICH7 Family USB UHCI Controller 
/0/100/1d.3/1    usb5       bus            UHCI Host Controller
/0/100/1d.3/1/1             communication  BT-253
/0/100/1d.7                 bus            NM10/ICH7 Family USB2 EHCI Controller
/0/100/1d.7/1    usb1       bus            EHCI Host Controller
/0/100/1d.7/1/8             multimedia     USB 2.0 Camera
/0/100/1e                   bridge         82801 Mobile PCI Bridge
/0/100/1f                   bridge         82801GBM (ICH7-M) LPC Interface Bridg
/0/100/1f.2                 storage        82801GBM/GHM (ICH7-M Family) SATA Con
/0/1             scsi0      storage        
/0/1/0.0.0       /dev/sda   disk           250GB Samsung SSD 850
/0/1/0.0.0/1     /dev/sda1  volume         230GiB EXT4 volume
/0/1/0.0.0/2     /dev/sda2  volume         2038MiB Extended partition
/0/1/0.0.0/2/5   /dev/sda5  volume         2038MiB Linux swap / Solaris partitio




Any help would be really appreciated.

kr,

Andreas

---

### Post by mörgæs on 2018-04-26
Hi, welcome to the fora.

18.04 solves a number of problems for Atom processors. When Lubuntu 18.04 is released in a day or two I suggest that you do a fresh install of this one.

---

### Post by adewilt on 2018-04-26
Thank you for your prompt reply Mörgæs. Does this mean a dist-upgrade would not work?

kr,

Andreas

---

### Post by mörgæs on 2018-04-26
It might but I have often seen upgrades trash a system. 
You can try the upgrade but if it fails I suggest that you do the fresh install anyway.

---

