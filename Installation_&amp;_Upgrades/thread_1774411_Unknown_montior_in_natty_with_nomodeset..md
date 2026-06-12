---
title: "Unknown montior in natty with nomodeset."
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by Mr_VeRiTy on 2011-06-03
Hi, I'm trying to upgrade my sister to natty, but it wont boot properly unless I use nomodeset. It didn't need this in maverick, and she doesn't need any proprietary drivers, as she only has onboard laptop graphics (intel mobile 4 series I think..) So when I boot it into the LiveCD the resolution is wrong, so I go into system > preferences > monitors but it wont let me change the resolution as the monitor is listed as "Unknown" I also tried LinuxMint 11 (Katya) but it was the same (it is based on ubuntu anyways so it's not surprising.)

Does anybody know what's wrong.

---

### Post by Mr_VeRiTy on 2011-06-04
**bump**

---

### Post by Mr_VeRiTy on 2011-06-20
Anybody know a way to fix this?

---

### Post by Toz on 2011-06-20
Have a look at: [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution") - specifically the section on adding undetected resolutions. 

Post back the output of:```
xrandr
```what you've tried and what the results were.

---

### Post by Mr_VeRiTy on 2011-06-20
> **Toz said:**
> Have a look at: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) - specifically the section on adding undetected resolutions. 

Post back the output of:```
xrandr
```what you've tried and what the results were.
I can't access my sisters box right now, will try later, but so far I've tried using an external monitor, which changed nothing, and editing the xorg.conf usually results in failure for me so that's all I've tried. 

I had a similar problem on linux mint 11 on a different PC which had a Nvidia graphics card, and using nvidia-settings to change the resolution worked, would this work on her laptop (even though it has Intel graphics?)

Edit: Also, whilst trying to fix the other PC I mentioned, I tried to set an undetected resolution as it said on the page, but it didn't work, I think the error I got was "Mode does not exist."

---

### Post by Toz on 2011-06-20
> I had a similar problem on linux mint 11 on a different PC which had a Nvidia graphics card, and using nvidia-settings to change the resolution worked, would this work on her laptop (even though it has Intel graphics?)No, it won't work with the intel card.

> Edit: Also, whilst trying to fix the other PC I mentioned, I tried to set an undetected resolution as it said on the page, but it didn't work, I think the error I got was "Mode does not exist."Can you post back the command you used and the error message?

Maybe you could also reply with some system specs. Try running the following command and post back the results:```
lspci -vnn
```and post back the contents of **/var/log/Xorg.0.log**

---

### Post by Mr_VeRiTy on 2011-06-20
> **Toz said:**
> No, it won't work with the intel card.

Can you post back the command you used and the error message?

Maybe you could also reply with some system specs. Try running the following command and post back the results:```
lspci -vnn
```and post back the contents of **/var/log/Xorg.0.log**
(Bearing in mind, this is from the PC on which nvidia-settings fixed the problem for me.)

From the history command I can see 
```
xrandr -s "1440"x"900"
    3  xrandr
    4  xrandr --addmode S-video 1440x900
    5  lspci | grep VGA
    6  cvt 1440 900 60
    7  xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
    8  xrandr --addmode S-video 1440x900

```and then some time later 
```

   37  fbset --test 1440 900
   38  fbset --test -g 1440 900 1440 900
   39  fbset --test -g 1440 900 1440 900 32
   40  sudo fbset --test -g 1440 900 1440 900 32
   41  sudo fbset --test -g 1440 900 1440 900 32
   42  man fbset
   43  man fbset
   44  fbset --help
   45  sudo apt-get install fbset
   46  man fbset
   47  fbset --test 1440 900
   48  fbset --test 1440 900
   49  fbset --test 1440 900
   50  fbset --test -g 1440 900 1440 900 32
   51  sudo fbset --test -g 1440 900 1440 900 32
   52  sudo fbset  -g 1440 900 1440 900 32
   53  sudo fbset -g 1440 900 1440 900 32

```A lot of those commnds didn't work due to incorrect syntax. I can't give the output of those commands, (without re-doing them all) as this was weeks ago..

the output of lspci -vnn was 
```
00:00.0 Host bridge [0600]: ATI Technologies Inc RX780/RX790 Chipset Host Bridge [1002:5957]
    Subsystem: ATI Technologies Inc RX780/RX790 Chipset Host Bridge [1002:5957]
    Flags: bus master, 66MHz, medium devsel, latency 0
    Memory at <ignored> (64-bit, non-prefetchable)
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [9c] HyperTransport: #1a

00:02.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A) [1002:5978] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fc000000-fe9fffff
    Prefetchable memory behind bridge: 00000000d4000000-00000000dfffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: ATI Technologies Inc Device [1002:5957]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:09.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E) [1002:597e] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: ATI Technologies Inc Device [1002:5957]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0a.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F) [1002:597f] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: fbf00000-fbffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: ATI Technologies Inc Device [1002:5957]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 46
    I/O ports at a000 [size=8]
    I/O ports at 9000 [size=4]
    I/O ports at 8000 [size=8]
    I/O ports at 7000 [size=4]
    I/O ports at 6000 [size=16]
    Memory at fbdfa000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] MSI: Enable+ Count=1/4 Maskable- 64bit+
    Capabilities: [70] SATA HBA v1.0
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fbdf3000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at fbdfa400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fbdf8000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at fbdfa800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
    Flags: 66MHz, medium devsel
    Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface [0101]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40) (prog-if 8a [Master SecP PriP])
    Subsystem: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ff00 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fbdf4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
    Subsystem: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=64

00:14.5 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399] (prog-if 10 [OHCI])
    Subsystem: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fbdf9000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:15.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a0] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Prefetchable memory behind bridge: 00000000d3f00000-00000000d3ffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: ATI Technologies Inc Device [1002:0000]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.1 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a1] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fbe00000-fbefffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: ATI Technologies Inc Device [1002:0000]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fbdfb000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at fbdfac00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
    Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
    Flags: fast devsel

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [Realtek RTL8111E] [1043:8432]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    I/O ports at b800 [size=256]
    Memory at d3fff000 (64-bit, prefetchable) [size=4K]
    Memory at d3ff8000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
    Kernel driver in use: r8169
    Kernel modules: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Edimax Computer Co. Device [1432:7612]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at c800 [size=256]
    Memory at fbefc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 88-55-22-fe-ff-4c-e0-00
    Kernel driver in use: rtl819xSE
    Kernel modules: r8192se_pci

04:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:8413]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fbffa000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [50] Power Management version 3
    Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [90] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [a0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
    Capabilities: [150] #18
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd

05:00.0 IDE interface [0101]: JMicron Technology Corp. JMB368 IDE controller [197b:2368] (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device [1043:827e]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at dc00 [size=8]
    I/O ports at d880 [size=4]
    I/O ports at d800 [size=8]
    I/O ports at d480 [size=4]
    I/O ports at d400 [size=16]
    Capabilities: [68] Power Management version 2
    Capabilities: [50] Express Legacy Endpoint, MSI 01
    Kernel driver in use: pata_jmicron
    Kernel modules: pata_jmicron

06:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:1245] (rev a1) (prog-if 00 [VGA controller])
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fc000000 (32-bit, non-prefetchable) [size=32M]
    Memory at d8000000 (64-bit, prefetchable) [size=128M]
    Memory at d4000000 (64-bit, prefetchable) [size=64M]
    I/O ports at ec00 [size=128]
    [virtual] Expansion ROM at fe980000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

06:00.1 Audio device [0403]: nVidia Corporation Device [10de:0bee] (rev a1)
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fe97c000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```/var/log/Xorg.0.log is attached.

---

### Post by Mr_VeRiTy on 2011-06-22
The output of xrandr on my sisters laptop was: ```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
    1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)

```

She's using maverick right now, since we couldn't get natty to work.

---

### Post by Toz on 2011-06-22
Oh, I think I understand now. You're sister is running Maverick now, but wants to run Natty, but Natty won't boot with the proper resolution. Sorry for the confusion.(I thought your sister's computer had natty installed and couldn't display the proper resolution.)

From your sister's computer running Natty, can we get the output of:
```
lspci -vnn
``` and the contents of her current **/var/log/Xorg.0.log** file?

Lets see how things are set up now, the exact model of her video card and her current X configuration. Lets then have a look and see if there are any specific changes in Natty that would affect this setup.

---

### Post by Mr_VeRiTy on 2011-06-22
> **Toz said:**
> Oh, I think I understand now. You're sister is running Maverick now, but wants to run Natty, but Natty won't boot with the proper resolution. Sorry for the confusion.(I thought your sister's computer had natty installed and couldn't display the proper resolution.)

From your sister's computer running Natty, can we get the output of:
```
lspci -vnn
``` and the contents of her current **/var/log/Xorg.0.log** file?

Lets see how things are set up now, the exact model of her video card and her current X configuration. Lets then have a look and see if there are any specific changes in Natty that would affect this setup.
That would have to wait a while, my sister lives across town, and doesn't have a natty livecd with her.

---

### Post by Toz on 2011-06-22
Ugh. Not having a good day. I meant from your sister's computer now running _Maverick_, can you get the result of the lspci command and a copy of the log file.

---

### Post by Mr_VeRiTy on 2011-06-22
> **Toz said:**
> Ugh. Not having a good day. I meant from your sister's computer now running _Maverick_, can you get the result of the lspci command and a copy of the log file.

I probably wont be able to do that until tomorrow..

---

### Post by Mr_VeRiTy on 2011-06-23
The output was:```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 09)
	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
 	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
 	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp


00:02.0  VGA compatible controller [0300]: Intel Corporation Mobile 4 Series  Chipset Integrated Graphics Controller [8086:2a42] (rev 09) (prog-if 00  [VGA controller])
 	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
	Flags: bus master, fast devsel, latency 0, IRQ 45
 	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
 	I/O ports at 50f0 [size=8]
	Expansion ROM at <unassigned> [disabled]
 	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915
 

00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 09)
	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
 	Flags: bus master, fast devsel, latency 0
	Memory at d3400000 (64-bit, non-prefetchable) [size=1M]
 	Capabilities: <access denied>


00:1a.0  USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI  Controller #4 [8086:2937] (rev 03) (prog-if 00 [UHCI])
 	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
	Flags: bus master, medium devsel, latency 0, IRQ 20
 	I/O ports at 50c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
 

00:1a.7 USB Controller [0c03]: Intel Corporation  82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)  (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
 	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at d6704c00 (32-bit, non-prefetchable) [size=1K]
 	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd


 00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
 	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at d6700000 (64-bit, non-prefetchable) [size=16K]
 	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
 

00:1c.0 PCI bridge [0604]: Intel Corporation 82801I  (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03) (prog-if 00  [Normal decode])
	Flags: bus master, fast devsel, latency 0
 	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
 	Memory behind bridge: d5700000-d66fffff
	Prefetchable memory behind bridge: 00000000d0400000-00000000d13fffff
 	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp
 

00:1c.1 PCI bridge [0604]: Intel Corporation 82801I  (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03) (prog-if 00  [Normal decode])
	Flags: bus master, fast devsel, latency 0
 	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00003000-00003fff
 	Memory behind bridge: d4600000-d56fffff
	Prefetchable memory behind bridge: 00000000d1400000-00000000d23fffff
 	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp
 

00:1c.2 PCI bridge [0604]: Intel Corporation 82801I  (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03) (prog-if 00  [Normal decode])
	Flags: bus master, fast devsel, latency 0
 	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00001000-00002fff
 	Memory behind bridge: d3500000-d45fffff
	Prefetchable memory behind bridge: 00000000d2400000-00000000d33fffff
 	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp
 

00:1d.0 USB Controller [0c03]: Intel Corporation  82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)  (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
 	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 50a0 [size=32]
 	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd


 00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9  Family) USB UHCI Controller #2 [8086:2935] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
 	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 5080 [size=32]
 	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd


 00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9  Family) USB UHCI Controller #3 [8086:2936] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
 	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 5060 [size=32]
 	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd


 00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9  Family) USB UHCI Controller #6 [8086:2939] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
 	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 5040 [size=32]
 	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd


 00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9  Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
 	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d6704800 (32-bit, non-prefetchable) [size=1K]
 	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd


 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
 	Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
	Capabilities: <access denied>
 

00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
 	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
 	Kernel modules: iTCO_wdt


00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03) (prog-if 01 [AHCI 1.0])
 	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
 	I/O ports at 50e8 [size=8]
	I/O ports at 50fc [size=4]
	I/O ports at 50e0 [size=8]
 	I/O ports at 50f8 [size=4]
	I/O ports at 5020 [size=32]
	Memory at d6704000 (32-bit, non-prefetchable) [size=2K]
 	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci
 

00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
 	Flags: medium devsel, IRQ 11
	Memory at d6705000 (64-bit, non-prefetchable) [size=256]
 	I/O ports at 5000 [size=32]
	Kernel modules: i2c-i801


04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
 	Subsystem: AMBIT Microsystem Corp. AR5BXB63 802.11bg NIC [1468:0428]
	Flags: bus master, fast devsel, latency 0, IRQ 17
 	Memory at d4600000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
 	Kernel driver in use: ath5k
	Kernel modules: ath5k


05:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
 	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
	Flags: bus master, fast devsel, latency 0, IRQ 44
 	Memory at d3500000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 1000 [size=128]
 	Capabilities: <access denied>
	Kernel driver in use: atl1c
	Kernel modules: atl1c

```

---

### Post by Toz on 2011-06-23
Something doesn't make sense here. The results of the lspci command show an intel video card.....
> 00:02.0  VGA compatible controller [0300]: Intel Corporation Mobile 4 Series  Chipset Integrated Graphics Controller [8086:2a42] (rev 09) (prog-if 00  [VGA controller])
 	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
	Flags: bus master, fast devsel, latency 0, IRQ 45
 	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
 	I/O ports at 50f0 [size=8]
	Expansion ROM at <unassigned> [disabled]
 	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915
 

00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 09)
	Subsystem: Acer Incorporated [ALI] Device [1025:0212]
 	Flags: bus master, fast devsel, latency 0
	Memory at d3400000 (64-bit, non-prefetchable) [size=1M]
 	Capabilities: <access denied>
.....but the Xorg.0.log file is loading an nvidia driver???
> [    23.027] (II) LoadModule: "nvidia"
[    23.027] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    23.082] (II) Module nvidia: vendor="NVIDIA Corporation"

Are both of these outputs from the same computer? And what kind of computer is it?

---

### Post by Mr_VeRiTy on 2011-06-23
> **Toz said:**
> Something doesn't make sense here. The results of the lspci command show an intel video card.....

.....but the Xorg.0.log file is loading an nvidia driver???


Are both of these outputs from the same computer? And what kind of computer is it?

They should be from the same laptop, yes. Its an emachines laptop.

Edit: My bad, got the files mixed up, here's the correct file.. _[http://www.pasteall.org/22625](http://www.pasteall.org/22625)_[]("http://pastebin.com/qQi6sBDS")

---

### Post by Toz on 2011-06-23
> **Mr_VeRiTy said:**
> Its an emachines laptop.

What is the model of the laptop?

---

### Post by Mr_VeRiTy on 2011-06-23
> **Toz said:**
> What is the model of the laptop?

eMachines E525

---

### Post by Toz on 2011-06-23
Some interesting info for you.

1. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/759104]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/759104") - A known bug with that chipset. Read post #3 where they got it going by installing the xorg-edgers version of X (though with backlight problems).

2. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/792026]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/792026") - found this bug report as well. Interesting thing here is that this person has found that the screen is not blank, but rather the backlight is off. In this case, you might want to try booting the Natty Live CD without the nomodeset parameter, but with the **acpi_osi=Linux** kernel parameter. (see also: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438/comments/2]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438/comments/2"))

3. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773740]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773740") - about a new patched kernel that might solve the problem.

4. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438") - this one talks about the same thing, but of note is that when they plug an external monitor into the laptop, the screen displays properly on the external monitor and they can issue setpci commands to make the laptop brightness work again.

Hope this helps.

---

### Post by Mr_VeRiTy on 2011-06-23
> **Toz said:**
> Some interesting info for you.

1. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/759104](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/759104) - A known bug with that chipset. Read post #3 where they got it going by installing the xorg-edgers version of X (though with backlight problems).

2. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/792026](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/792026) - found this bug report as well. Interesting thing here is that this person has found that the screen is not blank, but rather the backlight is off. In this case, you might want to try booting the Natty Live CD without the nomodeset parameter, but with the **acpi_osi=Linux** kernel parameter. (see also: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438/comments/2](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438/comments/2))

3. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773740](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773740) - about a new patched kernel that might solve the problem.

4. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438) - this one talks about the same thing, but of note is that when they plug an external monitor into the laptop, the screen displays properly on the external monitor and they can issue setpci commands to make the laptop brightness work again.

Hope this helps.

Number 2 sounds very relevant, as when I was trying to get natty to work on the laptop I could see a VERY faint outline of where windows were, but I thought this was normal. Anyway I'll check these out, thanks.

---

