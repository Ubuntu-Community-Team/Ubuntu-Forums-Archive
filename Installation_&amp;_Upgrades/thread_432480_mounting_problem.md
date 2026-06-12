---
title: "mounting problem"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by krischeu on 2007-05-04
Dear NG,

how can i mount my 2 harddisk?
I see the following in the output of dmesg. My controller is rr174x - HighPoint sata raid. 4 Channels. The 2 Harddisks are attached at channel 0 and 1. Channel 2 and 3 are free.


[42949384.760000] rr174x: module license 'Proprietary' taints kernel.
[42949384.770000] rr174x:2: RocketRAID 174x controller driver v1.02 (May  2 2007 16:50:59)
[42949384.770000] ACPI: PCI Interrupt 0000:05:0e.0[A] -> GSI 16 (level, low) -> IRQ 185
[42949384.770000] rr174x:2: adapter at PCI 5:14:0, IRQ 185
[42949384.850000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[42949384.860000] intel8x0_measure_ac97_clock: measured 60290 usecs
[42949384.860000] intel8x0: clocking to 48000
[42949384.860000] ACPI: PCI Interrupt 0000:05:0c.0[A] -> GSI 19 (level, low) -> IRQ 193
[42949385.340000] rr174x:2: start channel [0,0]
[42949385.340000] rr174x:2: start channel [0,1]
[42949385.340000] usbcore: registered new driver hiddev
[42949385.360000] input: Logitech USB Optical Mouse as /class/input/input2
[42949385.360000] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.1-1
[42949385.360000] usbcore: registered new driver usbhid
[42949385.360000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[42949385.380000] ts: Compaq touchscreen protocol output
[42949385.730000] rr174x:2: channel [0,0] started successfully
[42949385.850000] rr174x:2: channel [0,1] started successfully

---

### Post by Paracetamol on 2007-07-15
Hi!

I suggest trying mount /dev/sdX1 /mnt

X depends on your system. If you have no other SATA or SCSI-disks, you should try "a" instead of "X".
If you have 1 other SATA or SCSI-disk => "b" , 2 => "c"  ... and so on ;-)

By the way: I'm one step behind you...after building the driver (version 1.02 on ubuntu 7.04) and modprobe I got a segmentation fault...

Maybe someone can help!?

Greetings

Paracetamol

---

### Post by TizzyD on 2007-07-16
Same segfault here.  During the build, seems that there's just no joy.  Looking to see what's really up.  Some initial investigation says the board is really fake RAID, so we should just be able to load the disks as two independent drives.  Hope to get there soon.

I'm not happy thinking I will have to appy Cox's patch and build a new OS version so that I could swap over the sata_mv, but if that's what it takes.

---

### Post by SwollenTiki on 2007-09-20
krischeu, how did you get the rr174x driver to work in Ubuntu?  I have a RocketRAID 1740 card that I've been trying to figure out how to get it to work with no luck.  I've done numerous google searches and nothing works.  I'm trying to compile the driver from source, but I get an error and it's not like any other errors people have been getting when they do the same.  

Here is what happens.  If any one can offer any information I would greatly appreciate it.

make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/tiki/rr174x-linux-src-v1.03/product/rr174x/linux/.build/os_linux.o
  CC [M]  /home/tiki/rr174x-linux-src-v1.03/product/rr174x/linux/.build/osm_linux.o
  CC [M]  /home/tiki/rr174x-linux-src-v1.03/product/rr174x/linux/.build/div64.o
  CC [M]  /home/tiki/rr174x-linux-src-v1.03/product/rr174x/linux/.build/hptinfo.o
  CC [M]  /home/tiki/rr174x-linux-src-v1.03/product/rr174x/linux/.build/config.o
  LD [M]  /home/tiki/rr174x-linux-src-v1.03/product/rr174x/linux/.build/rr174x.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/tiki/rr174x-linux-src-v1.03/product/rr174x/linux/.build/.him_rr1740.o.cmd for /home/tiki/rr174x-linux-src-v1.03/product/rr174x/linux/.build/him_rr1740.o
  LD [M]  /home/tiki/rr174x-linux-src-v1.03/product/rr174x/linux/.build/rr174x.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'

---

### Post by SwollenTiki on 2007-09-20
Nevermind, I found my problem and it's working now.

---

### Post by ThaBorg on 2008-04-19
> **SwollenTiki said:**
> Nevermind, I found my problem and it's working now.

Ik have the exact same problem. How did you manage to compile the driver?

---

