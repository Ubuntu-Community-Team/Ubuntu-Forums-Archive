---
title: "Help me please i dont know what to do"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by TheDevilMr666 on 2011-07-28
i installed an app called Nvidia from the software center and it messed upp my computer the desktop screen is now stuck in classic mode and i cant get nvidia to go away . can anyone tell me how to system reset ubuntu i have nothing worth keeping i just rather have a computer that runs on ubuntu . i tried burning the ubuntu download on a cd and trying to reinstall it but it just tells me my computer is up to date.

---

### Post by 23dornot23d on 2011-07-28
Its a Acer Aspire 7745 what [graphics card]("http://www.pcworld.com/product/648838/acer_aspire_77455632.html?p=specs") is in it please .... ( after looking at your other two threads )

ok it looks like its integrated intel ....

so just remove the Nvidia .... that you loaded in ... the same way you added it

Go to the Software Center 

except this time uninstall it .........

---

### Post by coffee412 on 2011-07-28
Go to system/admin/drivers and choose to turn off the nvidia driver and it should revert to the open driver.

also, to find out the video card that is in it open a term window and type this in:

> sudo lspci -v 

Look for your video card

---

### Post by TheDevilMr666 on 2011-07-28
ok i did that but i doesnt say anything about a video card it just gives me the specs of my comp acer aspire 7754-5632 , and stuff bout my wireless drivers

---

### Post by TheDevilMr666 on 2011-07-28
thats all it says is that its integrated oh and it also says i am 64 bit if that helps but is there away to just reset it kinda to factory default or do i have to find what did it and remove becus the Nvidia ad removies but when i go to system- admin it still shows up as nvidia X server settings

---

### Post by coffee412 on 2011-07-28
When you installed it did it say drivers where available and that it wanted to install them?

Also, Try this in a term window:

dmesg |grep nvidia

---

### Post by TheDevilMr666 on 2011-07-28
ok heres what happened when i installed the nvidia it in stalled a theme so when i when to uninstall it i didnt uninstall the theme pack so i clicked on the hidden files when i searched for nividia and i had 16 files installed ate the same time all linked to nvidia and deleated them all now my system is back to normal thank you guys very much .... now im looking for a 3d accelerator so i can pla games any hints??? im using 11.04 64 bit and i still dont know what kind of grafix driver i have it says intigrated?

---

### Post by 23dornot23d on 2011-07-28
According to the specs here ,,,,  [link to graphics card specifications for computer above ]("http://www.pcworld.com/product/648838/acer_aspire_77455632.html?p=specs")

Its intel ... according to that lnk .... but as said earlier

**sudo lspci -v **

will give all the info
just cut and paste it so we can see it ....

The way you un-install things on Linux needs to be done with the software center or synaptic

You cannot just go deleting files if they are related to things like video drivers ,,,, not sure it is drivers
if there was theme pack .... (and to delete nvidia drivers etc you would need root privileges) .... seems odd ...

But at least you are up and running again ....

If it booted ok you could check the log files and see what it is detecting too ... if its in UNITY now
then instead of classic ..... then is compiz running

**compiz --replace**

what happens if you do that ,,,,,,

---

### Post by TheDevilMr666 on 2011-07-28
dustin@dustin-Aspire-7745:~$ sudo lspci -v 
[sudo] password for dustin: 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
    Subsystem: Acer Incorporated [ALI] Device 0367
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 0368
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Acer Incorporated [ALI] Device 0367
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f0805800 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable- Count=1/1 Maskable- 64bit+

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 0367
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f0806000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: Acer Incorporated [ALI] Device 0367
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f0600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0400000-f04fffff
    Prefetchable memory behind bridge: 00000000a0000000-00000000a01fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0367
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0500000-f05fffff
    Prefetchable memory behind bridge: 00000000a0200000-00000000a03fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0367
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 0367
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f0806400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
    Capabilities: [50] Subsystem: Acer Incorporated [ALI] Device 0367

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
    Subsystem: Acer Incorporated [ALI] Device 0367
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=10 <?>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06) (prog-if 01 [AHCI 1.0])
    Subsystem: Acer Incorporated [ALI] Device 0367
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
    I/O ports at 1818 [size=8]
    I/O ports at 180c [size=4]
    I/O ports at 1810 [size=8]
    I/O ports at 1808 [size=4]
    I/O ports at 1820 [size=32]
    Memory at f0805000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
    Subsystem: Acer Incorporated [ALI] Device 0367
    Flags: medium devsel, IRQ 10
    Memory at f0806800 (64-bit, non-prefetchable) [size=256]
    I/O ports at 1840 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
    Subsystem: Acer Incorporated [ALI] Device 0367
    Flags: fast devsel, IRQ 18
    Memory at f0604000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: intel ips
    Kernel modules: intel_ips

02:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
    Subsystem: Acer Incorporated [ALI] Device 0367
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f0400000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 2000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [6c] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-65-5d-7a-c8-0a-a9-ff
    Kernel driver in use: atl1c
    Kernel modules: atl1c

09:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
    Subsystem: Foxconn International, Inc. Device e021
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-cb-ff-ff-7b-f0-7b
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: wl, brcm80211

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

dustin@dustin-Aspire-7745:~$

---

### Post by coffee412 on 2011-07-28
> Intel Corporation Core Processor Integrated Graphics Controller 

You have an intel graphics controller. I really dont know much about them. Im a Nvidia man myself. But I would use the default free driver for it or look up your specs on your laptop and see what others are doing. Google "Ubuntu <name of graphics card>" and see what you get.

For now, Boot your laptop and hold down the shift key while it boots. Select safe boot (or something like that) and it will use the free driver for the intel graphics.

---

### Post by 23dornot23d on 2011-07-28
00:02.0 VGA compatible controller: Intel Corporation Core Processor  Integrated Graphics Controller (rev 12) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 0368
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

its the intel i915 chipset .......
and appears to have picked up ok 

[_LINK_]("http://www.google.com/search?client=ubuntu&channel=fs&q=intel+i915&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&hs=cRI&channel=fs&source=hp&q=intel+i915+graphics+linux&pbx=1&oq=intel+i915+graphics+linux&aq=f&aqi=&aql=&gs_sm=e&gs_upl=8664l15811l0l15968l15l14l0l5l5l0l375l2159l0.1.4.3l8l0&bav=on.2,or.r_gc.r_pw.&fp=26e57aa7900464a7&biw=1077&bih=548") to more information on it ... so

what does

**xrandr -q**

display too ....

also did you try 

[B]compiz --replace

[COLOR=Red]did it give any errors .... or alter the display at all ....[/COLOR]
[/B]

---

