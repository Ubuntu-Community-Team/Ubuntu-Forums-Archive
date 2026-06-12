---
title: "Just installed Ubuntu 64 bit 12.04 (issues)"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by Grimace78 on 2012-06-08
I recently built a new desktop pc, partly for the performance and a lot for the learning experience. I decided to go with Ubuntu, and realized how far in over my head I was trying to get all the specialized drivers. 

List of components:
z68p-ds3 motherboard
intel i5 quadcore 2500K cpu
8 GB ram 1333
Encore PCI N300 wireless card
Epson Artison 730 printer/scanner

I was try not only to get my printer and wireless card working; more importantly I wanted to get the chipset drivers and Intel Rapid Storage Techknowlegy installed. After a little research I realized I will probably be an old man before I get all that put together. Help with this would be GREATLY appreciated!! I have heard that others have compliled packages that will work for my problem but cannot find them.

---

### Post by patrickceg on 2012-06-08
EDIT: Mods suggest moving to Hardware & Laptops or General Help...

(Forgive me I'm thinking general Linux debugging because I don't own that kind of printer or wireless card.)

Is that printer attached via USB or through the network? If it's through the network, plug in the USB cable while the printer is on just to see if you can get drivers for that printer.

I'm unfamiliar with that particular wireless card. Do you know what chipset is in that card? If not, open a Terminal and type the following command into it:
```
lspci
```That should dump a lot of output about your devices - copy-paste the entry containing information about your wireless card (or all the output if there's nothing secret installed on your computer).

For your chipset drivers, I'm running on a 2500K and P67 chipset and everything worked out of the box with no configuration required. Is there something specifically you want to install (e.g. motherboard RAID)?

Hope this helps

---

### Post by mastablasta on 2012-06-09
they have a .deb file for printer here: [http://www.openprinting.org/driver/epson-escpr/](http://www.openprinting.org/driver/epson-escpr/)
not sure if it works. maybe they also have somehting on debian site. usually if they have a tar.gz file you need to extract it first and then read the readme file.

another option is to try to add a printer in ubuntu prnters and see if Ubuntu finds the drivers by itself.

---

### Post by Grimace78 on 2012-06-09
> **patrickceg said:**
> EDIT: Mods suggest moving to Hardware & Laptops or General Help...

(Forgive me I'm thinking general Linux debugging because I don't own that kind of printer or wireless card.)

Is that printer attached via USB or through the network? If it's through the network, plug in the USB cable while the printer is on just to see if you can get drivers for that printer.

I'm unfamiliar with that particular wireless card. Do you know what chipset is in that card? If not, open a Terminal and type the following command into it:
```
lspci
```That should dump a lot of output about your devices - copy-paste the entry containing information about your wireless card (or all the output if there's nothing secret installed on your computer).

For your chipset drivers, I'm running on a 2500K and P67 chipset and everything worked out of the box with no configuration required. Is there something specifically you want to install (e.g. motherboard RAID)?

Hope this helps

> **mastablasta said:**
> they have a .deb file for printer here: [http://www.openprinting.org/driver/epson-escpr/](http://www.openprinting.org/driver/epson-escpr/)
not sure if it works. maybe they also have somehting on debian site. usually if they have a tar.gz file you need to extract it first and then read the readme file.

another option is to try to add a printer in ubuntu prnters and see if Ubuntu finds the drivers by itself.

Thanks for the replies. I'm so frustrated at this point I'm not sure what to do with it all but this is what I came up with.

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 Display controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Z68 Express Chipset Family LPC Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8190 802.11n Wireless LAN


grimace@grimace-Z68P-DS3:~$ sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04b8:087b Seiko Epson Corp. 
Bus 001 Device 004: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 005: ID 22b8:431c Motorola PCS 
Bus 002 Device 003: ID 154b:0044 PNY 
Bus 002 Device 004: ID 046d:c52e Logitech, Inc. 
Bus 001 Device 006: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 007: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 001 Device 008: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 001 Device 009: ID 0461:4d75 Primax Electronics, Ltd Rocketfish RF-FLBTAD Bluetooth Adapter

---

### Post by Grimace78 on 2012-06-11
Well, I got the printer to print, but still working on the scanning part. Here is the link for the printer driver.

[http://www.ubuntubuzz.com/2011/10/download-various-epson-printers-driver.html](http://www.ubuntubuzz.com/2011/10/download-various-epson-printers-driver.html)

---

### Post by Grimace78 on 2012-06-14
Bump?

---

### Post by darkod on 2012-06-14
So, what is exactly the issue right now, only the scanning?

You mentioned the wireless card and Intel Storage in your first post.

1. The lspci is showing the chipset of the wireless card as Realtek RTL8190. Did you check the Realtek website for drivers? They have linux versions, you need to check if there is one for your chipset/model.

2. Is the Intel Storage an issue? Why? If you are thinking of raid, and running only ubuntu, the linux software raid works much better than the bios fakeraid, so I would recommend running software raid. Usually no additional drivers would be needed as long as the disks are detected and working.

---

### Post by Grimace78 on 2012-06-14
> **darkod said:**
> So, what is exactly the issue right now, only the scanning?

You mentioned the wireless card and Intel Storage in your first post.

1. The lspci is showing the chipset of the wireless card as Realtek RTL8190. Did you check the Realtek website for drivers? They have linux versions, you need to check if there is one for your chipset/model.

2. Is the Intel Storage an issue? Why? If you are thinking of raid, and running only ubuntu, the linux software raid works much better than the bios fakeraid, so I would recommend running software raid. Usually no additional drivers would be needed as long as the disks are detected and working.

I was most concerned with the chipset drivers from intel, along with all the intel and nvidia graphics software ect. As soon as I updated my kernal to 3.4.1, a lot of those restricted drivers became available for some reason, and my system is obviously running better (it would freeze up a lot etc.). 

What threw me on the the wireless driver is that the label says Encore, so I appreciate you pointing that out. I am also, like you mentioned still having an issue with the rest of the functions of my all in one printer. Here is the package I downloaded. I think if I could get it installed then EVERTHING would actually work properly.

epson_artisan_730_full_printer_driver_linux

At this point I don't remember where I downloaded it from, but the site said to refer questions to the source (the site itself), and I couldn't find command line instructions for installation to save my life.

---

### Post by Grimace78 on 2012-06-14
Found a link in the file. I was really hoping someone could tell me how to install it after taking the time to hunt it down.

 [http://avasys.jp/english/linux_e/](http://avasys.jp/english/linux_e/)

> Package: epson-inkjet-printer-201112w
Version: 1.0.0-1lsb3.2
Architecture: amd64
Maintainer: Seiko Epson Corporation <linux-epson-inkjet@avasys.jp>
Installed-Size: 3276
Depends: lsb (>= 3.2)
Section: alien
Priority: extra
Description: Artisan 730 / Artisan 837 Series - Epson Inkjet Printer Driver
 This software is a filter program used with Common UNIX Printing
 System (CUPS) from the Linux. This can supply the high quality print
 with Seiko Epson Color Ink Jet Printers.
 .
 This printer driver is supporting the following printers.
 .
 Artisan 730
 Artisan 837
 Epson Stylus Photo TX730WD
 Epson Stylus Photo PX730WD
 Epson Stylus Photo PX830FWD
 .
 For detail list of supported printer, please refer to below site:
 [http://avasys.jp/english/linux_e/](http://avasys.jp/english/linux_e/)
 .
 (Converted from a rpm package by alien version 8.69.)

Edit: Link to help page. All I can find is trouble shooting, not installation instructions.
[http://avasys.jp/eng/linux_driver/faq/knowledge/softwares/](http://avasys.jp/eng/linux_driver/faq/knowledge/softwares/)

---

### Post by Grimace78 on 2012-06-15
It's like I've got a bunch of little elves fixing my computer while I'm away from it, lol. Scanner works fine now, and I didn't do anything to it to get it working that I'm aware of. All I have left for the most part is the driver for the n300 pci wireless card.

---

