---
title: "Sony Vaio VPC-F11M1E/H Drivers Problem"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tomvaiou on 2010-03-23
Hi,

i have bought Sony Vaio VPC-F11M1E/H, and i have many problems with my devices.
It doesn't work my wireless card, i can't connect my Logitech M555b bluetooth mouse, and vga can't work properly.

My vga is nVidia 330M, and lspci gets this:

00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Arrandale PCI Express x16 Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a29 (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
02:00.0 Network controller: Intel Corporation Device 422c (rev 35)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
3f:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
3f:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)

I have ubuntu 9.10 and the kernel is: 2.6.31-20-generic

P.S.
The problem is that i am new in linux and i can't understand all that says an experienced user in linux.

Thanks

A moderator let move this to the proper category. Bad english :)

---

### Post by asiandub on 2010-03-28
same problem here, still trying to get "intel corporation device 422c" wireless to work...

did you have any success so far?

cheers,
jan

---

### Post by digitalpbk on 2010-04-02
Hi I have Sony Vaio VP CW with the same intel wireless card. Try this command on linux commandline prompt. Take terminal and run

```
sudo apt-get install linux-backport-modules-karmic
```

For more details see [Install Wifi Drivers on ubuntu sony vaio laptop]("http://digitalpbk.com/ubuntu/install-wireless-wifi-drivers-linux-karmic-9.1-sony-vaio-cw")

---

### Post by doctorprojector on 2010-04-10
> **digitalpbk said:**
> Hi I have Sony Vaio VP CW with the same intel wireless card. Try this command on linux commandline prompt. Take terminal and run

```
sudo apt-get install linux-backport-modules-karmic
```

For more details see [Install Wifi Drivers on ubuntu sony vaio laptop]("http://digitalpbk.com/ubuntu/install-wireless-wifi-drivers-linux-karmic-9.1-sony-vaio-cw")

It's actually "linux-backports-modules-karmic", and it worked for me too on a Sony VPCS11C5E laptop and Ubuntu 9.1 Karmic Koala. The wireless card is an Intel 422c.

Thank you.

doctorprojector

---

### Post by Darkav on 2010-04-10
> **doctorprojector said:**
> It's actually "linux-backports-modules-karmic", and it worked for me too on a Sony VPCS11C5E laptop and Ubuntu 9.1 Karmic Koala. The wireless card is an Intel 422c.

Thank you.

doctorprojector

On my VPCS11C5E the wifi worked with lucid lynx out-of-the-box (but i have problem with the WWAN).

---

