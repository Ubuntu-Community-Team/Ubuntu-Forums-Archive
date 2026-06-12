---
title: "Ubuntu does not recognize bluetooth, sound, microphone and touchscreen cards..."
date: 2018-02-18
forum: Installation &amp; Upgrades
---

### Post by marcos.1108 on 2018-02-18
First of all, this is the first time I'm posting anything to a forum, so sorry for anything. I recently bought the M11W multilaser notebook and installed the 16.04.3 LTS version of ubuntu on it, as it is the latest LTS version. As soon as I installed it, I realized that the wi-fi card, not many others had been recognized. I decided to install the newest version at 17.10.1 to see what it gave. When installing, I realized that cards had been recognized as the camera, the wi-fi and other more basic were all recognized, but the bluetooth boards, sound, microphone, touchscreen did not. I am basic level in ubuntu and I do not know how to solve this, I already researched in Google, but I did not find anything that helps a lot.


I've already circled the code in the terminal:


sudo lspci -k
and the result was:

```

[COLOR=#1D2129][FONT=Helvetica]00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 36)[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]Kernel driver in use: iosf_mbi_pci[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers (rev 36)[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]Subsystem: Intel Corporation Atom/Celeron/Pentiu[/FONT][/COLOR][COLOR=#1D2129][FONT=Helvetica]m Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers
Kernel driver in use: i915
Kernel modules: i915
00:03.0 Multimedia controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit (rev 36)
Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit
00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 36)
Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller
Kernel driver in use: proc_thermal
Kernel modules: processor_thermal_device
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 36)
Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller
Kernel driver in use: xhci_hcd
00:1a.0 Encryption controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine (rev 36)
Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine
Kernel driver in use: mei_txe
Kernel modules: mei_txe
00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 36)
Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU
Kernel driver in use: lpc_ich
Kernel modules: lpc_ich
[/FONT][/COLOR]
```


For information on the motherboard, I installed hardInfo and in the DMI part it looked like this:


-BIOS-
Date: 05/25/2017
Vendor: American Megatrends Inc. ([www.ami.com]("http://www.ami.com"))
Version: 8.17
-Board-
Name: M11W
Vendor: Multilaser
-Product-
Name: M11W
Family: EMI30P3S1M12L1B304T4C00W1H2G0G3A0C0P0C0D0C1104M0N1X1WOS
Version: Default string

I downloaded the official drivers, but they came in extensions .cat .inf .sys and .pnf. But I do not know how to install them

---

### Post by tinylagarto on 2018-02-18
Which version of Ubuntu are you running right now? 16.04 or 17.10?

Did you try to install the drivers via the drivers install or software properties?

---

### Post by marcos.1108 on 2018-02-18
I am using version 17.10 and do not know how to install these drivers, so I have not tried

---

### Post by tinylagarto on 2018-02-19
OK, there is an option to install proprietary drivers on Ubuntu.

I guess you use the default Gnome desktop on 17.10, then just hit the Super/Win key and type drivers. You should see 'Additional Drivers', something like this, open it and try to see if you can install them.

---

### Post by marcos.1108 on 2018-02-19
[IMG]https://scontent.fbel1-1.fna.fbcdn.net/v/t1.0-9/27973493_2048542041828780_3102337802673633989_n.jpg?_nc_eui2=v1%3AAeGAiRucF1aY14jspd4l_HBmdJBUwXNJg6vwri16OfloPVgJOa-Sh0NpN0xSrMv4P_feqDOpXgDZkgsftlMWoHubmUrEwUjIcZsUFurBI93q8g&oh=62c7fd97a0eb7d2a605644640d5e538f&oe=5B210103[/IMG]
only that appears here

---

### Post by tinylagarto on 2018-02-20
OK I see. I hoped it would offer more. I have no experience with that kind of device. I guess it is relatively new and probably and it seems many of the components are not being recognized.

I hope someone else can step in. 

Also try to edit your post and put the hardware specs into CODE tags. This way the output will be more readable.

---

### Post by marcos.1108 on 2018-02-20
Done, thank you anyway. Yes, this device is really new.

---

