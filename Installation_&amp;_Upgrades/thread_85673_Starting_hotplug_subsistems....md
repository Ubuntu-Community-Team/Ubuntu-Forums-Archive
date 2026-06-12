---
title: "Starting hotplug subsistems..."
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by dtstyle on 2005-11-03
Hi everybody,

I have a problem with installing Ubuntu 5.1. 
PC configuration:
Processor: Intel Pentium 4 3.0 GHz 

Mainboard: Asus P5GPL LGA 775, Intel 915+ICH6, FSB 800 Mhz, Dual-ch DDR 400, PCI-E x 16, 8-ch audio, Gb lan, sata, usb 2.0, AI NOS, AI NET 2

Video: NVIDIA GeForce PCX 5300 PCI-express 128mb 

Hard Drive : Maxtor 160 GB, SATA, 8 mb cache, 7200 rpm

RAM: 1024 Mb Kingston Dual Kit 

CD/DVD/: DVD Double layer -LG

DVD: DVD - LG

Floppy: NEC.

So what happend. I started installing Ubuntu 5.1 and everyting was done. I partitioned my hard drive and give 5 GB for ubunto and 255 mb for swap.
And the rest ot the hard drive is NTFS and with Windows XP. After instalation finished I restart my computer and chose to boot Linux from Grub.
Its start loading and stop in **Starting hotplug subsistems**....
And now I can`t start ubunto on my pc. Do you know how I can fix this.

Thanks

---

### Post by towsonu2003 on 2005-11-03
try passing 

nohotplug

as a boot option to kernel. to do this, on the startup grub menu, edit the kernel line and add 

nohotplug

to the end of the line (the one that is the most long, I believe).

---

### Post by dtstyle on 2005-11-04
Thanks,

But I`m a new Linux user and I didn't understand how I have to do all this. 
I read on internet and saw similar problem with other person. The problem was USB-mouse he fixed this when unplug the mouse before start booting Linux...and everything is ok. I also have a usb-mouse. But I don't want to unplug USB mouse every time before booting my system. 
So please can you guide me how I can fix this. 

Thanks very much

---

