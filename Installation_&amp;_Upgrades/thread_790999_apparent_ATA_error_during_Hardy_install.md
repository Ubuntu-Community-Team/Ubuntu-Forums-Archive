---
title: "apparent ATA error during Hardy install"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by ekarni on 2008-05-11
I'm experiencing what appears to be an ATA error when attempting to do a clean install of Hardy from the alternate CD (i386 architecture):

```
[  ##.######] ata4.00: status { DRDY }
[  ##.######] ata4: port is slow to respond, please be patient (Status 0xd0)
[  ##.######] ata4: soft resetting link
[  ##.######] ata4.00: configured for UDMA/66
[  ##.######] ata4: EH complete
[  ##.######] ata4.00: execption Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  ##.######] ata4.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[  ##.######]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[  ##.######]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emast 0x4 (timeo
ut)
[  ##.######] ata4.00: status {DRDY} 
...
```


My first installation attempt was for just a command line system.  This popped up at the end of that.  I then tried to do a standard desktop install from the alternate CD, and this message appeared almost immediately.  In both cases, these messages looped for longer than I cared to wait (at least 10 minutes).  I've been running Ubuntu since Breezy on this box and never had a similar error appear before...

The system:
Western Digital PATA HDD
Athlon 3000 CPU, MSI motherboard
Toshiba DVD-RW drive
NVidia 5700 graphics card
all about 3 years old

Snipped output from lshw:
```
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=VIA_IDE latency=32 module=via82cxxx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD1200JB-00GVA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 08.02D08
                   serial: WD-WCALA1688746
                   size: 111GB
                   capacity: 111GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 188MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 111GB
                      capacity: 111GB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume:0
                         description: Linux filesystem partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 14GB
                    *-logicalvolume:1
                         description: Linux swap / Solaris partition
                         physical id: 6
                         logical name: /dev/hda6
                         capacity: 1906MB
                         capabilities: nofs
                    *-logicalvolume:2
                         description: Linux filesystem partition
                         physical id: 7
                         logical name: /dev/hda7
                         capacity: 4769MB
                    *-logicalvolume:3
                         description: Linux filesystem partition
                         physical id: 8
                         logical name: /dev/hda8
                         capacity: 90GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD writer
                   product: LITE-ON DVDRW SOHW-1673S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: JS02
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: status=nodisc

```

After the install failed I reloaded Gutsy and am rolling with that, but would like to get Hardy going if possible.  Any idea what the problem and workaround might be?

Thanks!

---

### Post by RJARRRPCGP on 2008-05-11
You should:

1. Replace the CMOS battery. (Because it may be bad with it being about 4 years old or not that far)

2. Clear the CMOS and reload the defaults.

---

### Post by saru411 on 2008-05-14
I'm having the same error on

Asus P5w - Dh
4 Gb Mushkin Redline
4x 320 Gb raid 10 on 3ware 9590se controller
E6600 C2D
7600GT Nvidia 256 MB

I can get my system to boot fine but it takes forever. This is not a cmos battery issue. It has something to do with the new kernel not liking something on our mother boards and I believe it to be ACPI related. I am still searching for the answer and will post again if I find it.

Update: [http://ubuntuforums.org/showthread.php?t=770284&highlight=ata4.00](http://ubuntuforums.org/showthread.php?t=770284&highlight=ata4.00)

supposedly if you add irqpoll and noprobe=ata4 to grub the issue shall be resolved

---

### Post by Pumalite on 2008-05-14
Try some boot parameters (to be tried one by one or in different combinations until you hit the right one):
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=791

---

### Post by ekarni on 2008-05-15
Thanks for the ideas, but no luck so far.  I've tried the following boot option (combinations):
[LIST=1]
[*]noprobe=ata4
[*]irqpoll=off
[*]acpi=ht
[*]pci=noacpi
[*]acpi=norirq
[*]irqpoll noprobe=ata4
[*]acpi=off pci=noacpi noapic nolapic
[*]acpi=off pci=noacpi noapic=1 nolapic=1 irqpoll=off
[*]ide=nodma
[*]all_generic_ide
[*]ide=nodma all_generic_ide
[/LIST] 

How about a dist-upgrade from my current minimal Gutsy installation, then setting the Gutsy 2.6.22-14 kernel as default in grub?

---

### Post by Pumalite on 2008-05-15
Install a different distro to see if you are incompatible with Linux in general, or Ubuntu in particular.

---

### Post by ekarni on 2008-05-18
Installed Debian 4.0r3 (Etch) today, and it's working fine (2.6.18 kernel).  Think I'm going to stick with that, since I'm really looking for a stable long-term install, and Hardy isn't it at this point.  From my point of view this thread is closed, but if anyone does encounter this problem and finds a solution, feel free to link to the solution for the benefit of other users...

---

