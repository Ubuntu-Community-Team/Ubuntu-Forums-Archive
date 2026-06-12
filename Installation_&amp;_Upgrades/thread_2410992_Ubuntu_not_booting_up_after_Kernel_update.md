---
title: "Ubuntu not booting up after Kernel update"
date: 2019-01-23
forum: Installation &amp; Upgrades
---

### Post by fer1805 on 2019-01-23
Hi community,

I am new to Ubuntu and to linux . I searched on this forum and other forums before posting this question. Some similar questions use very technical linux language in the replies, which I don't quite understand. 

I have ubuntu 18.10, it came with kernel 4.18.0.10.11 (wifi works, touchscreen doesn't work), ubuntu self updated to 4.18.0.13.14, I noticed an improvement on performance (runs smoother, apps seem to open faster), but wifi stopped working, and touchscreen issue not fixed. I uninstalled 4.18.0.13.14 and currently using 4.18.0.10.11.

I tried updating to 4.20.3 using ukuu, but it is not booting up and the following error comes up when it is trying to boot up:
"
error: /boot/vmlinuz-4.20.3-042003-generoc has invalid signature
error: you need to load the kernel first.

Press any key to continue..._
"

I have tried enabling / disabling secure boot on bios with no luck.

I would like to update to newer kernels to see if the touchscreen issue is fixed, plus improving performance while keeping the wifi working. Any newer kernel tried using ukuu gives me the same error. I have also tried manual update with the same results.

Any suggestions or help will be appreciated. Thank you in advance.

Hardware details as follows:

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) I/O Memory Management Unit
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Stoney [Radeon R2/R3/R4/R5 Graphics] (rev d9)
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 15b3
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Host Bridge
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Host Bridge
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1578
00:09.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 157d
00:09.2 Audio device: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Audio Controller
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 20)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 4b)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 49)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 4b)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b5
01:00.0 Non-Volatile memory controller: Toshiba America Info Systems Device 0116
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter

---

