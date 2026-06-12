---
title: "Linux Mint Cinnamon 64 bit | NO WIFI | Acer Aspire 4750G"
date: 2018-10-07
forum: MINT
---

### Post by nierh on 2018-10-07
Hi guys! Totally noob in Linux, and I'm sorry... I have installed 3 different versions of Linux and Windows 7 in the past 24 hours only ending up in the same reason that I keep looking for a good version to start again. I give up! I need help! I have no problem in the windows installation but all in the three Linux version. I can't switch on WIFI?!

I have installed Ubuntu 18.4 ~ Zorin ~ and now finally Mint Cinnamon x64

There's a button on the screen that I am supposed to slide to turn on and I can't slide it? I did 7 hours worth of troubleshooting reading around these pages and some other Linux community forums only ending up in the same result.... No WIFI... Anyone can help? No physical switch around my laptop, Fn=F3(signal logo) only switches on bluetooth and airplane mode but no wifi. Is there anything else I can do? :(

```
oem@Mint-Aspire-4750:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev a1)
03:00.0 Network controller: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Broadcom Limited NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
04:00.1 SD Host controller: Broadcom Limited BCM57765/57785 SDXC/MMC Card Reader (rev 10)
04:00.2 System peripheral: Broadcom Limited BCM57765/57785 MS Card Reader (rev 10)
04:00.3 System peripheral: Broadcom Limited BCM57765/57785 xD-Picture Card Reader (rev 10)
05:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
oem@Mint-Aspire-4750:~$
```

```
oem@Mint-Aspire-4750:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
oem@Mint-Aspire-4750:~$
```

---

### Post by deadflowr on 2018-10-07
*Thread moved to **MINT***

---

