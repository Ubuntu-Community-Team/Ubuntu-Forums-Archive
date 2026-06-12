---
title: "help with ndiswrapper on 12.04"
date: 2013-06-17
forum: Installation &amp; Upgrades
---

### Post by moosejc on 2013-06-17
Hello,

I have a computer running Ubuntu 12.04 (64bit), and I am having trouble installing the drivers for my USB wireless adapter (Netgear WNA3100).

I ran into the "Fatal ndiswrapper module not found" error, and I have compiled ndiswrapper 1.58 from source, and did a "sudo modprobe ndiswrapper". This got rid of the "module not found" error, but it is still not working.

Running ndiswrapper -l gives me:

```
bcmwlhigh6 : driver installed
	device (0846:9020) present

```

So, that makes me think it should be working, but running lspci gives me....

```

00:00.0 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: NVIDIA Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: NVIDIA Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:07.0 Audio device: NVIDIA Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 SATA controller: NVIDIA Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:14.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 FireWire (IEEE 1394): LSI Corporation FW322/323 (rev 70)
02:00.0 VGA compatible controller: NVIDIA Corporation C78 [GeForce 9100] (rev a2)
05:00.0 Communication controller: LSI Corporation Device 0630 (rev 01)
```

And, yes, I have installed ndiswrapper-dkms, and the ndiswrapper-util1.9 (or whatever that one is).

I have tried everything from these pages:

[http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found](http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found)
[http://steveyoung.wordpress.com/2013/02/14/getting-the-netgear-usb-adapter-wna3100-to-work-with-ubuntu-12-04/](http://steveyoung.wordpress.com/2013/02/14/getting-the-netgear-usb-adapter-wna3100-to-work-with-ubuntu-12-04/)
[http://ubuntuforums.org/showthread.php?p=11970543](http://ubuntuforums.org/showthread.php?p=11970543)

and, a few other pages that didn't offer additional information from those three.

I am using the file bcmwlhigh6.inf (which, according to ndiswrapper website should work on my computer)

I have tried everything I could google, or find in the forums. Could somebody give me an idea as to how to proceed? How can I determine what the exact problem is? What may I have overlooked?

Thank you guys in advance for helping me out.

---

