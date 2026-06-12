---
title: "Unable to change screen resolution after installation"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by VictorWarner on 2008-02-25
I have installed Ubuntu 7.10. On reboot the resolution is set at 1280 x 1024 at 60hz.

Although other resolutions are shown none of them work (I want a lower resolution). 

Running lspci in console produces: 

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
02:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
02:02.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Among the available drivers under System/Administration/Screen and Graphics/Graphics Card none of the ones for ATI work (the default is VESA). 

Is there a way to fix this? Help with this would be greatly appreciated.

Victor Warner.

---

### Post by VictorWarner on 2008-02-26
Bump

---

### Post by Partyboi2 on 2008-02-26
what happens if you add the resolution that you want to xorg.conf file. ```
gksudo /etc/X11/xorg.conf
``` Look for the screen section and add your desired resolution. eg.
> "Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation NV17 [GeForce4 MX 440]"
    Monitor        "FLATRON L151"
    Defaultdepth    24
    SubSection "Display"
        [COLOR=Red]Modes        "1280x1024"    "1024x768"    "832x624"    "800x600"    "720x400"    "640x480"[/COLOR]
    EndSubSection
EndSectionor you could try something like [envy]("http://albertomilone.com/nvidia_scripts1.html") to install the ati driver.

---

