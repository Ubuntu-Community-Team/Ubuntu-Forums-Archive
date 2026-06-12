---
title: "Bootable usb stops at Syslinux....."
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by Prolixed on 2013-02-10
Hey everyone, I am trying to boot from a Ubuntu usb but every time it freezes at the screen "Syslinux [info about it] [blinking cursor]" I cannot type and I have tried different usbs and have tried different programs for creating a usb. I cannot use a disk because my laptop dose not have a disk drive. Maybe you guys can help? Thanks.

Laptop:
  ```
 Operating System: Windows 7 Professional 64-bit
System Manufacturer: Sony Corporation
       System Model: SVT131190X
               BIOS: InsydeH2O Version 03.71.51R0220E4
          Processor: Intel(R) Core(TM) i7-3517U CPU @ 1.90GHz (4 CPUs), ~1.9GHz
             Memory: 8192MB RAM
```

Syslinux File:
```
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --


```

---

