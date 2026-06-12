---
title: "No wifi on Dell XPS laptop"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jerrynewt on 2008-10-25
I'm trying to get the wifi to work on a friend of mine's Dell XPS M1530 laptop (dual boot Vista and 8.10). Wifi works on vista but can't get the wifi light to come on in ubuntu. The owners manual says wifi is controlled with "Wifi Catcher Network Locator", which is enabled in Vista. There is a small button next to the on/off switch for the wifi, but nothing happens when I push it. I am also not showing an entry for wireless in network manager. Any ideas for a work around ?? Thanks for the help.

---

### Post by MrWES on 2008-10-25
Try hitting the Fn + F2 keys to turn on the wifi.

---

### Post by pytheas22 on 2008-10-25
If Network Manager doesn't recognize any wireless card, then you probably need to install a driver (in that case, toggling the wireless on/off isn't going to do anything until a driver is installed).  Please post the output of the following commands so that we can figure out which driver you need:
```

lspci -nn
lshw -C Network
uname -m
```

---

### Post by st33med on 2008-10-25
What wireless card do you have? Try:
```
lspci | grep Network
```

And post the results here.

---

### Post by jerrynewt on 2008-10-25
Sorry for the bit screw-up but my friends laptop has dual boot Vista and Ubuntu 8.04. I mistakenly said it was 8.10 -- sorry for the inconvenience.Here are the results that were asked for --
red@red-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
03:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
red@red-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:15:c5:86:7d:03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
red@red-laptop:~$ uname -m
i686
red@red-laptop:~$ lspci | grep Network
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

---

### Post by jerrynewt on 2008-10-26
Bump

---

### Post by pytheas22 on 2008-10-26
Your friend has a Broadcom 4328 card, which is newer and therefore lacks support out-of-the-box in Hardy (it would probably work in Intrepid).  You can still get it working, however; please take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=880218").  The instructions there should apply to your card (make sure your system is fully updated first or the instructions in that post won't work; hopefully you can use the ethernet connection to download the Ubuntu updates).  If that doesn't work, let us know and we can try some other things.

---

### Post by Teamgeist on 2008-10-26
Yeah the instructions given in this thread:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)  from Superm1 work just fine for this wireless card.

It will work out-of-the-box with Intrepid after installing the package provided under System--> Administration--> Hardware Drivers.

Maybe you want to install the RC of Intrepid, so your friend won't have to upgrade in a couple of days anyway.

You can download it here: [http://releases.ubuntu.com/releases/8.10/](http://releases.ubuntu.com/releases/8.10/)

---

