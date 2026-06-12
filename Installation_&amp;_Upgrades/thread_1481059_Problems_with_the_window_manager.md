---
title: "Problems with the window manager"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by choallin on 2010-05-12
Hi guys!

I have following video card:

ATI Technologies Inc Mobility Radeon HD 3650

On my Toshiba laptop running Ubuntu 10.04. I have catalyst  installed. 

I didn't enable desktop effects.

I have major problems wiht switching between windows (it's not possible). The symbols for minimizing and maximizing  windows aren't there. Not on the left. Not on the right side.
Also, i have no border an any window i'm oppening.

What can I do to solve this problem? Do I need another driver for my graphikcard?

My lspci output below

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
04:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
04:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
04:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
04:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by dino99 on 2010-05-12
goto system admin hardware driver to see if yours is activated

the driver you need is : xserver-xorg-video-radeon

for the missing icons, into console: metacity --replace

---

### Post by choallin on 2010-05-12
Thx for your hint. Now i have the border. But its not working as it should. If i quit the terminal in which the metacity is running the border and of course the symbols are vanished. I have absolutly no idea what  i should to do run this permanently...
I have checked the driver, it is activated.

Also i have a different problem. If i boot the desktop is not displayed very often. This means i just see the background and no menu at all. Neither at the top nor at the bottom. With Ctl+Alt+Del i can reboot. Sometimes i get the desktop after rebooting. Maybe this two problems are linked somehow?

so long
choallin

---

