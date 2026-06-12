---
title: "Toshiba Satellite Install Problems"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by shawnc_nmb on 2010-08-28
Hello, I have been using Ubuntu for along time.  I have had my share of problems with installs many times before so I'm hoping theres some solutions to the problems I am having.  

I just purchased a Toshiba Satellite A655-S6070 the base specs are

lcpsi results
[PHP]
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
16:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
16:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
16:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
16:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
[/PHP]

Anyway, So far After a fresh install of Ubuntu 10.04, I am having the following problems

-- Wireless Networking --
I first compiled the Driver from Realteck and moved it to the folder it said but no wireless.

After that, I tryed using NDISWrapper but everytime I shutdown and turn back on I have to uninstall and reinstall The Driver to get wifi to work again.

-- Shutdown or ACPI Functions --
Everytime I shutdown or suspend or hibernate the system does not shutdown properly and I have to run Recovery Mode to fix whatever errors where there. Then I have to reboot it 2x to get it to boot.

Those are the major problems I remember at the moment, I have some minor problems that I've had before and I'll search out the results but some of them are

-- No Title Bar On Windows --
Have to Reload Window Manager Every Boot thats a problem I used to get with Fiesty I just can't remember the actual fix to it,  for now I'm just using th Compiz Icon to Reload Window Manager

-- No Video Output --
Video Player Didn't Play Videos, I had to set the gstreamer prefs to Xvo output if I remember correctly to fix that.



I read somewhere that the new 10.10 Alpha 3 version fixed alot of these problems but I couldn't get it to login after i burned the DVD donnu what happened with that.  

Anyway if anyone could shed some light on these problems it would help me greatly as I am a Web Developer and need my Laptop all the time,  After spending 1k on a nice laptop I'd really like to fix these problems since I refuse to use windows and haven't even tryed a windows computer in 5 years or more.

Thanks

Shawn C
[www.s-vizion.com](www.s-vizion.com)

---

### Post by anubhavrocks on 2010-08-29
Wait for 10.10 to come out.
Till then you can run Ubuntu in a VM.Atleast your productivity will not get hit.

---

### Post by shawnc_nmb on 2010-08-29
I was afraid of that,  10.10 doesn't come out til Oct right? Is there a way to install the Alpha release or am I Pretty much stuck with Windows for now?

---

### Post by anubhavrocks on 2010-08-29
Here's the release schedule
[https://wiki.ubuntu.com/MaverickReleaseSchedule](https://wiki.ubuntu.com/MaverickReleaseSchedule)

You can get the directions to install Alpha from the above.

I suggested that you use Ubuntu in a VM, exactly so that you are not stuck with Windows.

---

