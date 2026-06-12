---
title: "Trying to install Ubuntu 12.10 for a month!"
date: 2013-03-28
forum: Installation &amp; Upgrades
---

### Post by miLl3niUm on 2013-03-28
Hello community, I am trying to install the latest Ubuntu OS on my PC (64bit) and I'm having 2 serious issues:

Note: I'm writing all these with what I remember only, as it have been some time since my latest attempt! (sorry - bad memory)

1. I use Nvidia GT 240 gfx card, which I read out that there is a general issue with Nvidia cards. I remember that I've boot using nomodeset but I didn't manage to install the drivers after lots of attempts!

2. Ubuntu failed to recognize my network card, and in result it was much harder for me to get anything fixed. How am I supposed to install them? If I'm right it would not recognize any eth0 device.

I am sorry for the lack of info, but that's all I can remember.

---

### Post by ahallubuntu on 2013-03-28
~

---

### Post by TOMBSTONEV2 on 2013-03-28
+1 for installing ubuntu 12.04 and getting the network drivers working. 12.04 seems to cause people less installation grief. Are you able to plug the good ole ethernet cord in? If you can get internet through these means that is a start and better than no internet. 

lspci-nn

 post the output please.

---

### Post by miLl3niUm on 2013-03-28
What do I miss with Ubuntu 12.04? Is there anything important?

---

### Post by TOMBSTONEV2 on 2013-03-28
Check [this]("http://askubuntu.com/questions/202860/what-are-the-major-differences-between-ubuntu-12-04-and-12-10-in-terms-of-securi") out:

The major difference is stability. 12.04LTS is regarded as more stable. I also believe that some of the "new features" may not be on it. But I had both versions and didn't really notice a difference aside from way less problems with 12.04LTS.

---

### Post by miLl3niUm on 2013-03-29
> **TOMBSTONEV2 said:**
> +1 for installing ubuntu 12.04 and getting the network drivers working. 12.04 seems to cause people less installation grief. Are you able to plug the good ole ethernet cord in? If you can get internet through these means that is a start and better than no internet. 

lspci-nn

 post the output please.
Is this what you are looking for?
> 
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d131] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
**00:19.0 Ethernet controller [0200]: Intel Corporation 82578DC Gigabit Network Connection [8086:10f0] (rev 05)**
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1c.6 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 [8086:3b4e] (rev 05)
00:1c.7 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 [8086:3b50] (rev 05)
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b02] (rev 05)
00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller [8086:3b20] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.5 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller [8086:3b26] (rev 05)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT215 [GeForce GT 240] [10de:0ca3] (rev a2)
01:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be4] (rev a1)
06:03.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] [104c:8023]
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers [8086:2c51] (rev 04)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2c81] (rev 04)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2c90] (rev 04)
3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2c91] (rev 04)
3f:03.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller [8086:2c98] (rev 04)
3f:03.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder [8086:2c99] (rev 04)
3f:03.4 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Test Registers [8086:2c9c] (rev 04)
3f:04.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers [8086:2ca0] (rev 04)
3f:04.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers [8086:2ca1] (rev 04)
3f:04.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers [8086:2ca2] (rev 04)
3f:04.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers [8086:2ca3] (rev 04)
3f:05.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers [8086:2ca8] (rev 04)
3f:05.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers [8086:2ca9] (rev 04)
3f:05.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers [8086:2caa] (rev 04)
3f:05.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers [8086:2cab] (rev 04)


---

### Post by TOMBSTONEV2 on 2013-03-31
Sort of, that is your ethernet connection. So if you plug the ethernet cord in you get internet right? Ok so now you are right I am not seeing a wireless internet adapter. Do you by anychance happen to know what your wireless network controller is?

---

### Post by Jay_E on 2013-03-31
hi there
in the past, I  problems with missing firmware.
Please see if this can be ruled out.
check the logs and look for error messages.

You can use "more" to scan the logs.
cd /var/log
sudo more syslog

it isn't clear if you can't get wireless or hardwire(eth0) internet.
missing firmware is common to both.
 you can get firmware package on another machine, put on usb, walk over the usb and install IF you can't get eth0 to work.
see sticky notes about logs...
have fun, 
Jay

---

### Post by Jay_E on 2013-03-31
I should have added.

IF it is wireless driver you are talking about,
see
[http://wiki.debian.org/WiFi](http://wiki.debian.org/WiFi)

and

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Then, do search of firmware packages and see what  might apply.
aptitude search firmware

have fun,
Jay

---

