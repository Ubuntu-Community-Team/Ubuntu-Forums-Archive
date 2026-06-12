---
title: "Ubuntu Install on CooFun N40 Mini Pc Fails To Find EMMC"
date: 2022-05-12
forum: Installation &amp; Upgrades
---

### Post by hollow5555 on 2022-05-12
I recently got a CooFun N40 (Celeron N4020, Gemini Lake chipset. Apparently this box is also known as the Besstar Tech GB1B) mini pc. I picked it up to run some tests on it because it's small, cheap, and should be just what I need to do a small project I have in mind. Unfortunately I can't seem to get any Linux installed on it. I would prefer to use Ubuntu but whenever I try to install (I've tried both 20.04 and 22.04 Desktop version) and have had a LOT of trouble with both.

The first problem I had was that it appeared to just hang on the splash screen. After some digging I found that if I changed "quiet nosplash" to "noacpi noapic irqpoll nosplash" then I could see it was doing stuff in the background, namely checking the files on the install media intermixed with periodic reports of:

```
[  339.312902] mmc0: Timeout waiting for hardware cmd interrupt.
[  339.312922] mmc0: sdhci: ============ SDHCI REGISTER DUMP ===========
[  339.312931] mmc0: sdhci: Sys addr:  0x00000000 | Version:  0x00001002
[  339.312941] mmc0: sdhci: Blk size:  0x00000000 | Blk cnt:  0x00000000
[  339.312949] mmc0: sdhci: Argument:  0x00000000 | Trn mode: 0x00000000
[  339.312957] mmc0: sdhci: Present:   0x1fff0000 | Host ctl: 0x00000000
[  339.312965] mmc0: sdhci: Power:     0x0000000b | Blk gap:  0x00000080
[  339.312973] mmc0: sdhci: Wake-up:   0x00000000 | Clock:    0x0000f447
[  339.312981] mmc0: sdhci: Timeout:   0x00000000 | Int stat: 0x00018000
[  339.312989] mmc0: sdhci: Int enab:  0x00ff0003 | Sig enab: 0x00ff0003
[  339.312997] mmc0: sdhci: ACmd stat: 0x00000000 | Slot int: 0x00000001
[  339.313005] mmc0: sdhci: Caps:      0x546ec881 | Caps_1:   0x80000807
[  339.313013] mmc0: sdhci: Cmd:       0x00000502 | Max curr: 0x00000000
[  339.313021] mmc0: sdhci: Resp[0]:   0x00000000 | Resp[1]:  0x00000000
[  339.313029] mmc0: sdhci: Resp[2]:   0x00000000 | Resp[3]:  0x00000000
[  339.313036] mmc0: sdhci: Host ctl2: 0x00000000
[  339.313044] mmc0: sdhci: ADMA Err:  0x00000000 | ADMA Ptr: 0x0000000000000000
[  339.313049] mmc0: sdhci: ============================================
```

The next thing I tried was to add fsck.mode=skip to the command line to skip the checking of the boot media and see if that moved it along any and it did, but when I got to the installer there was no target for install available.
At this point I ran lspci and lsusb with the following output

```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Gemini Lake Host Bridge (rev 06)
00:00.1 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Dynamic Platform and Thermal Framework Processor Participant (rev 06)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 605 (rev 06)
00:0e.0 Multimedia audio controller: Intel Corporation Device 3198 (rev 06)
00:0f.0 Communication controller: Intel Corporation Celeron/Pentium Silver Processor Trusted Execution Engine Interface (rev 06)
00:12.0 SATA controller: Intel Corporation Device 31e3 (rev 06)
00:13.0 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f6)
00:13.1 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f6)
00:13.2 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f6)
00:14.0 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f6)
00:14.1 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f6)
00:15.0 USB controller: Intel Corporation Device 31a8 (rev 06)
00:16.0 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO I2C Host Controller (rev 06)
00:16.3 Signal processing controller: Intel Corporation Device 31b2 (rev 06)
00:1c.0 SD Host controller: Intel Corporation Celeron/Pentium Silver Processor SDA Standard Compliant SD Host Controller (rev 06)
00:1f.0 ISA bridge: Intel Corporation Device 31e8 (rev 06)
00:1f.1 SMBus: Intel Corporation Celeron/Pentium Silver Processor Gaussian Mixture Model (rev 06)
01:00.0 Network controller: Intel Corporation Wireless 3165 (rev 79)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)

$ lsusb
Bus 002 Device 002: ID 18a5:0250 Verbatim, Ltd STORE N GO
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2a Intel Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 4037:2804  2.4G Composite Devic
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I also looked in dmesg for anything related to mmc0 and all I see, besides the repeated timeouts and register dumps, is this:

```
[    1.312395] mmc0: CQHCI version 5.10
[    1.504871] mmc0: SDHCI controller on PCI [0000:00:1c.0] using ADMA 64-bit
```

At this point I'm stuck. Does anyone have any suggestions?
Thanks in advance!

---

### Post by hollow5555 on 2022-05-12
I believe I found a solution/workaround. The installer for 18.04 works fine, so I installed 18.04, updated all of the packages, and then did an upgrade to 20.04. That seems to have worked fine, meaning the issue is most likely some incompatibility with the kernel drivers in the newer installers and this chipset/emmc. Odd, but it's up and running now!

---

