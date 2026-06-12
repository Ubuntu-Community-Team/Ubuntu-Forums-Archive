---
title: "New install of 22.04.3 doesn't recognize USB 3.0 ports?"
date: 2024-02-02
forum: Installation &amp; Upgrades
---

### Post by cruiserandmax on 2024-02-02
I just installed 22.04.3 LTS on an ASRock J5040-ITX and the OS does not see anything that I connect to the USB 3.0 ports on the machine. What's weird is I even installed the OS from a USB stick on the USB 3.0 port and everything installed fine. But now when logged in plugging the same USB thumb drive back into the USB 3.0 port results in nothing happening... If I plug the USB stick into one of the legacy USB 2.0 ports ubuntu sees it and mounts it fine... I can re-boot the machine off the USB stick connected to the USB 3.0 port fine, but when the machine is booted of the SATA SSD that the OS was just installed to it stops seeing anything connected to the 3.0 ports.. I simply don't know what to do?

---

### Post by cruiserandmax on 2024-02-02
And even more weird- according to the output of lspci there are hardware USB 3.0 ports, but it doesn't list anything that I can see for the USB 2.0 ports- and the USB 2.0 ports are currently the only ports that will mount a drive...!?

here is the output from lspci:

00:00.0 Host bridge: Intel Corporation Gemini Lake Host Bridge (rev 06)
00:00.1 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Dynamic Platform and Thermal Framework Processor Participant (rev 06)
00:02.0 VGA compatible controller: Intel Corporation GeminiLake [UHD Graphics 605] (rev 06)
00:0e.0 Audio device: Intel Corporation Celeron/Pentium Silver Processor High Definition Audio (rev 06)
00:0f.0 Communication controller: Intel Corporation Celeron/Pentium Silver Processor Trusted Execution Engine Interface (rev 06)
00:12.0 SATA controller: Intel Corporation Celeron/Pentium Silver Processor SATA Controller (rev 06)
00:13.0 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f6)
00:13.1 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f6)
00:13.2 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f6)
00:13.3 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f6)
00:15.0 USB controller: Intel Corporation Celeron/Pentium Silver Processor USB 3.0 xHCI Controller (rev 06)
00:1f.0 ISA bridge: Intel Corporation Celeron/Pentium Silver Processor LPC Controller (rev 06)
00:1f.1 SMBus: Intel Corporation Celeron/Pentium Silver Processor Gaussian Mixture Model (rev 06)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
04:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)

---

### Post by cruiserandmax on 2024-02-02
Ok, so a reboot seems to have solved it. I guess the initial re-boot after OS install from the stick on the 3.0 port had some issue. It's weird because I even pulled the stick out when it prompted me to before clicking restart.. 

Sorry for starting and finishing a thread so fast :/

---

### Post by ActionParsnip on 2024-02-02
No worries, please mark as solved

---

