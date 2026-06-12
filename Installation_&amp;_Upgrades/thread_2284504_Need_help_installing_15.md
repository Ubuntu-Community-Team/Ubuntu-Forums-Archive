---
title: "Need help installing 15"
date: 2015-06-29
forum: Installation &amp; Upgrades
---

### Post by Donnie Love on 2015-06-29
Hello,
I'm trying to install 15, but I have no clue how. I downloaded it. I burned it to a disk, or attempted to. It never really stopped writing to the disk. After about a week I rebooted. When I try to boot from the disk, a version of Ubuntu comes up, but I'm not sure which. Whichever it is, it's so slow that it took 40 minutes to get the mouse over the settings button and then once I did, it wouldn't let me click on it. So where do I go from here??

---

### Post by grahammechanical on 2015-06-29
> All I want is an operating system whose main feature is _**NOT**_ planned obsolescence.

Then start again with Ubuntu 14.04. That has support until April 2019. Whereas, Ubuntu 15.04 only has 9 months support starting May 2015.

Ubuntu releases a Long Term Support (5 years) version every 2 years. The last was April 2014 (14.04). The next will be April 2016 (16.04). In between we get interim releases every six months that are supported for 9 months. The last was April 2015 (15.04). The next will be October 2015 (15.10).

As for your other problem we cannot even begin to help without further information about your computer hardware. Do include information about the graphic adapter and the amount of its own memory. Is there another operating system already installed? Does this machine have a BIOS or a UEFI boot system?

It is all useful information that can help us to guess what the problem could be. Right now I can only think that your hardware must be so old as to be obsolete even by Linux standards.

If you download Ubuntu 15.04 then it must be Ubuntu 15.04 that is running in the live session. There are usually logos that inform us of what version we are using.

Regards.

---

### Post by sammiev on 2015-06-29
> **grahammechanical said:**
> Then start again with Ubuntu 14.04. That has support until April 2019. Whereas, Ubuntu 15.04 only has 9 months support starting May 2015.

Ubuntu releases a Long Term Support (5 years) version every 2 years. The last was April 2014 (14.04). The next will be April 2016 (16.04). In between we get interim releases every six months that are supported for 9 months. The last was April 2015 (15.04). The next will be October 2015 (15.10).

As for your other problem we cannot even begin to help without further information about your computer hardware. Do include information about the graphic adapter and the amount of its own memory. Is there another operating system already installed? Does this machine have a BIOS or a UEFI boot system?

It is all useful information that can help us to guess what the problem could be. Right now I can only think that your hardware must be so old as to be obsolete even by Linux standards.

If you download Ubuntu 15.04 then it must be Ubuntu 15.04 that is running in the live session. There are usually logos that inform us of what version we are using.

Regards.

+1 to this post.

15.04 will be short lived and as above, 14.04 LTS is good for years to come. The next LTS version will be 16.04 and that is about 9 or 10 months away.

Computer specs are most helpful in answer what is correct for your computer.

---

### Post by Donnie Love on 2015-06-29
This computer's only a couple years old. It can't be that far out of date.
I tried installing 14, all it did was freeze up seconds after it opened. I did finally get 15 installed and it does the same thing.
I'll try to supply all the information I can, but I don't know where to find most of what you're asking for.
According to system info, under Graphics tab...
Driver: Gallium 0.4  on NV4C
Experience: Fallback
Does that mean anything to you? Doesn't say anything about memory.
14 was installed, but should have been wiped out by 15.
I don't know where to find information on boot system.

---

### Post by ajgreeny on 2015-06-30
For a start open a terminal with Ctrl+Alt+T then let's see the output in terminal of the command **lspci** followed by **free -m.**

Please use code-tags for the copied output; a how-to is in my signature below.

---

### Post by Skaperen on 2015-06-30
go with 14.04 or 14.04.2 and let us know what happens with that.

---

### Post by Donnie Love on 2015-06-30
[COLOR=#000080]My gibberish output code here

[/COLOR]```
Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file

```


> **Skaperen said:**
> go with 14.04 or 14.04.2 and let us know what happens with that.

14 freezes up about 10 seconds after it opens. Although, 15 did the same thing. That's where I'm at now.
I'm running 11 now. If only even numbered versions are the good ones, maybe I should try 12.

---

### Post by ajgreeny on 2015-06-30
Where did that "gibberish output code" come from; it can not have been from the command **lspci** which would show something like 
```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)

```Did you perhaps string the two commands together as one and type ```
lspci free -m
``` as a single command?
If so, run them separately, one by one; first run ```
lspci
``` then when that has finished run ```
free -m
```
Sorry if I confused you about that!

---

### Post by Donnie Love on 2015-07-01
Not your fault. I confuse easy. That's why I'm here.

```

donnie@donnie-amdnew:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 LPC Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control

```

```

donnie@donnie-amdnew:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3771       2206       1564          0        117        822
-/+ buffers/cache:       1266       2505
Swap:        11997         58      11939

```

Does any of that mean anything to you?

---

### Post by ajgreeny on 2015-07-01
```
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
```means that you have an nvidia video card for which I think you will need to either install the proprietary driver from Additional Drivers, or use the open source nouveau driver, though you will probably need to use the **nomodeset** boot option to do so.

There are lots of places where you can find out about using nomodeset but for a start have a look at [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132).

---

### Post by Donnie Love on 2015-08-09
I've been reading this over and over, at least the first 2 of 106 pages. It's way above my reading level and there's very little about it I understand. I'm aware of something called BIOS, but I don't really know how to get into it or monkey around inside. I'm unclear whether I'm supposed to go into the BIOS or enter code through a terminal. I guess I'll try one and then the other and see if one works.

---

### Post by Donnie Love on 2015-09-22
Still trying to figure this out. I think I downloaded the driver, or attempted to. It's hard to tell in a foreign environment. The screen doesn't scramble like it did before but it still freezes up. I'm completely lost. What do I do now?

---

### Post by oldfred on 2015-09-22
You said this was a newer system, but I find issues going back to 2007 when searching in Google.
[http://www.nvidia.com/object/nforce_nf4_winxp32_8.26_11.09.html](http://www.nvidia.com/object/nforce_nf4_winxp32_8.26_11.09.html)

If system is that old then Lubuntu or Xubuntu will work much better. 
Full Ubuntu is for systems with newer CPU and video cards/chips. The Unity gui needs better systems. But lightweight systems do not need such a new system and still are based on Ubuntu.

 Offical flavors:
[http://www.ubuntu.com/about/about-ubuntu/flavours](http://www.ubuntu.com/about/about-ubuntu/flavours)
[http://xubuntu.org/](http://xubuntu.org/)
[http://lubuntu.net/](http://lubuntu.net/)

---

