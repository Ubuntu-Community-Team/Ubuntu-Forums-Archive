---
title: "Unable to set 1920 x 1080 over hdmi (EDID Error?)"
date: 2015-03-08
forum: Installation &amp; Upgrades
---

### Post by dave4444 on 2015-03-08
Hi,

I have just installed Lubuntu on an an ASUS Eee Box EB1036 and I am unable to set 1920 x 1080 over hdmi on a full HD Toshiba TV, if I choose 1920 x 1080  in monitor settings the screen goes blank.

The highest working resolution I can see is 1360 x 768 on both the hdmi and 1024 X 768 on the VGA port.

Also when I select 1920 x 1080 it affects the VGA resolution in some way as task bar disappears.

I have also tried this PC on a 1360 x 768 TV which worked perfectly on HDMI and VGA 

I installed the Intel graphics installer and ran the updates but this hasnt helped.

Could anyone advise how I can set 1920 x 1080 on this PC?

Please let me know if any more information is needed, many thanks in advance for any help.

Dave4444

---

### Post by grahammechanical on 2015-03-08
From my experience a VGA connection will not give us the full range of screen resolutions available. Whereas HDMI wil do that. Try running this command to see what resolutions are available.

```
xrandr
```

Can the graphic adapter present the optimum resolution of the monitor?

Regards.

---

### Post by dave4444 on 2015-03-08
Hi thanks for your help,

The EB1036 has onboard "Intel® HD Graphics" link to Asus website here - 
[http://www.asus.com/Commercial_Desktops/EB1036/specifications/](http://www.asus.com/Commercial_Desktops/EB1036/specifications/)   

The results from  "xrandr"

Screen 0: minimum 8 x 8, current 1360 x 768, maximum 32767 x 32767
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080      50.0 +   60.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1920x1080i     60.1     50.0     60.0  
   1280x1024      75.0     60.0  
   1360x768       60.0* 
   1280x768       59.9     60.0  
   1280x720       60.0     50.0     59.9  
   1440x576i      50.1  
   1024x768       75.1     70.1     60.0  
   1440x480i      60.1     60.1  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        75.0     72.8     60.0     59.9  
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

I guess this means that the on board graphics are capable of full HD? Do you know what I should do to enable it?

Another thing I should have mentioned is that whilst my desktop and taskbar resolution is 1360 x 768 I cant maximise the windows fully horizontally, it seems as if they will only go as wide as the VGA settings of 1024 x 768. (edited to say that if I turn off VGA and just have HDMI on the windows will stretch fully) 

Thanks,

Dave4444.

---

### Post by Mikael Hartzell on 2015-03-08
Hi dave4444 :)

I don't have a sure cure for your specific problem, but I have had similar problems when connecting a 1388x768 display laptop to a 1920x1080 TV.

The data you got from running xrandr suggests that you have both the HDMI and the VGA connected to a monitor at the same time. I suggest that you try the following:

- install lxranrd  ( apt-get install lxrandr )
- unplug the VGA cable and leave the HDMI connected to the monitor
- run lxrandr as root and set the HDMI to 1920x1080 60 Hz AND disable the VGA output (untick the option "Turn On" for VGA).

If you have both the HDMI and the VGA connected at the same time, the max resolution you get might be limited by the lowest maximum resolution supported by both of those connectors.

If the display goes black then connect the VGA back to the monitor.

You said that setting 1920x1080 on the HDMI makes the task bar disapper. This might be by design. If your display chip supports display mirroring, then it tries to set the HDMI and VGA always to the same resolution. The VGA might not be able to go beyond 1024x768 and then the operating system resizes the Linux desktop to 1920x1080 and lets you see a 1024x768 window into it. If you try to move your mouse over the edge of the display then the display might scroll to let you see other parts of the oversized desktop. This feature has been in Linux since the early 2000 and it was useful when our displays were still small by todays standards.

One more thing.

The EB1036 should have Intel HD graphics. These  chips normally work out of the box with Ubuntu, so there should be no  reason to install anything related to Intel graphics. It might be worth to start all over by installing Linux again. If you do this you could try to run the installer while VGA is disconnected and HDMI is connected.

By the way, I found this thread because I searched for information about installing Linux on Asus EB1036. I am thinking about buying one, so I would be very grateful if you could tell us how the hardware is working in Linux (ethernet, audio, display, wifi). Also did you have to change settings in the BIOS to be able to install Linux.

There is no other information about Linux on EB1036 on the net (I've searched for hours) so any info about successes and failures would be most welcome :) It would be very helpful if you could run as root the command:   lspci  -v    and post the output here :)

---

### Post by dave4444 on 2015-03-09
Hi Mikael,

I tried your suggestion and ran lxrandr as root,  Iunfortunately the display went black so I had to  connect the VGA back to the monitor.

Do you have any other suggestions so that I can force 1920 x 1080?

I think you may be right about the outputs mirroring each other, lxandr has very few options in the gui to change, is there a better one you can recomend? (or any command line "magic" I can use?)

According to the Asus website the unit has  "Intel® HD Graphics"  . . . !

I havent used this PC very much, so I cant really cant say how well it is working, of your questions I have only used the wireless so far which seems fine. 
I have however got an issue with BIOS which seems to have got corrupted in some way, the BIOS screen flashes up for a second when F2 is pressed then disappears and then boots into Lubuntu. I guess at some stage I will have to take it apart and find the bios battery to reset it?

Thanks for your help so far Dave4444 

As requested the output of lspci -v is below - 

 00:00.0 Host bridge: Intel Corporation ValleyView SSA-CUnit (rev 0e)
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, fast devsel, latency 0
    Kernel driver in use: iosf_mbi_pci

00:02.0 VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0e) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, fast devsel, latency 0, IRQ 107
    Memory at d0000000 (32-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f080 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:13.0 SATA controller: Intel Corporation ValleyView 6-Port SATA AHCI Controller (rev 0e) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 104
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=8]
    I/O ports at f040 [size=4]
    I/O ports at f020 [size=32]
    Memory at d0816000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:14.0 USB controller: Intel Corporation ValleyView USB xHCI Host Controller (rev 0e) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, medium devsel, latency 0, IRQ 103
    Memory at d0800000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:1a.0 Encryption controller: Intel Corporation ValleyView SEC (rev 0e)
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, fast devsel, latency 0, IRQ 106
    Memory at d0500000 (32-bit, non-prefetchable) [size=1M]
    Memory at d0400000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: mei_txe

00:1b.0 Audio device: Intel Corporation ValleyView High Definition Audio Controller (rev 0e)
    Subsystem: ASUSTeK Computer Inc. Device 84f5
    Flags: bus master, fast devsel, latency 0, IRQ 108
    Memory at d0810000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 80000000-801fffff
    Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: d0700000-d07fffff
    Prefetchable memory behind bridge: 0000000080400000-00000000805fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.2 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 80600000-807fffff
    Prefetchable memory behind bridge: 0000000080800000-00000000809fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.3 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d0600000-d06fffff
    Prefetchable memory behind bridge: 0000000080a00000-0000000080bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation ValleyView USB Enhanced Host Controller (rev 0e) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d0815000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation ValleyView Power Control Unit (rev 0e)
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich

00:1f.3 SMBus: Intel Corporation ValleyView SMBus Controller (rev 0e)
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: medium devsel, IRQ 14
    Memory at d0814000 (32-bit, non-prefetchable) [size=32]
    I/O ports at f000 [size=32]
    Capabilities: <access denied>

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device 84cd
    Flags: bus master, fast devsel, latency 0, IRQ 105
    I/O ports at e000 [size=256]
    Memory at d0704000 (64-bit, non-prefetchable) [size=4K]
    Memory at d0700000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169

04:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
    Subsystem: Lite-On Communications Inc Device 6627
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at d0600000 (64-bit, non-prefetchable) [size=512K]
    Expansion ROM at d0680000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k

---

### Post by Mikael Hartzell on 2015-03-09
Hi Dave4444 :)   
 
Sorry to hear it did not help.   

I guess you have tested the TV with another device and you known the 1920x1080 mode works with HDMI ?  

 Your graphics chip seems to be Intel Valley View Gen7. I spend some time googling and found no real solution. Intel is actively supporting Linux and writing drivers, so the problem might go away with some new kernel version.  

People complaining about a black screen with Valley View Gen 7 mostly got it right after booting, so it might not be related to your specific problem. Some found some solutions though. 

 This short thread shows that other people are strugling with the same / similar problem:  

[http://askubuntu.com/questions/461653/how-to-install-intel-corporation-valleyview-gen7-in-ubuntu-12-10](http://askubuntu.com/questions/461653/how-to-install-intel-corporation-valleyview-gen7-in-ubuntu-12-10)  

This guy got it working in Ubuntu 13.10, but newer ones give him black screen: 

 [http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/%5Bubuntu%5D-kernel-upgrade-fixes-rtl8821-drivers-and-breaks-intel-valleyview-gen7-rev-0c-4175502721-print/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/%5Bubuntu%5D-kernel-upgrade-fixes-rtl8821-drivers-and-breaks-intel-valleyview-gen7-rev-0c-4175502721-print/)  

This guy was helped by a BIOS upgrade:  

[http://forums.linuxmint.com/viewtopic.php?f=59&t=181867](http://forums.linuxmint.com/viewtopic.php?f=59&t=181867)  

This guy was helped by upgrading kernel to version 3.15 

 [http://forums.gentoo.org/viewtopic-t-994936.html](http://forums.gentoo.org/viewtopic-t-994936.html)  

 What version of Lubuntu are you running ? I run UbuntuStudio 14.10 and it has kernel version 3.16.  If a distro with a newer kernel won't help then I guess you just need to wait for the Intel graphics driver to be fixed. 

 Sorry I could be of no more help.

---

### Post by dave4444 on 2015-03-12
Hi Mikael,

I'm running Lubuntu 14.04 LTS, and the TV in question works fine at 1920 x 1080 over hdmi with other devices. 

I will have a look at the threads below when I am back at the TV (probably this weekend) and if all else fails will have to get on to ASUS about the BIOS problems I am having and then reinstall.

Other than ths issues mentioned the EB1306 works fine and is fast enough for general PC duties, web browsing etc.

Many thanks for your help! :D

---

### Post by Mikael Hartzell on 2015-03-12
Hi :)     
 
Please try the latest Lubuntu (14.10) it may work better. Work on kernel and drivers is done all the time, so a newer distro might make a big difference.      
 
Ubuntu 15.04 is scheduled to be released in about a moth, it will have even newer kernel and drives. Lets hope it brings full support for the display chip :)

---

### Post by Mikael Hartzell on 2015-03-15
Hi :)

I've spent some more time searching the internet and it seems that support for ValleyView Gen 7 chipset has been in intel graphics driver quite some time now (at leat a year). So the problem might not be the driver after all.

One source of display problems people are having is failed communication between the graphics chip and the display. The os gets information about resolutions and refresh rates the display supports by getting the EDID of the display through the HDMI. This is a binary blob with information about supported resolutions.  Sometimes the stored EDID information on the display might be permanetly corrupted or the os might get incorrect information. For example the EDID might announce refresh rates that the display hardware does not support. When these refresh rates are used, the display goes black or goes into sleep mode.

You could troubleshoot this by connecting the computer to another 1920x1080 display to see if the source of the trouble is the original display itself.

You could also try to read the X.org.log. This file is created by X when it starts. You could try to find some error messages that might be related to problem. You can read the logfile with this command:

less /var/log/Xorg.0.log

Search for keyswords: error,   failed,   does not exist,   disabled,   failure,   unable to....,   etc.

Hope this helps :)

---

### Post by ubfan1 on 2015-03-15
Under the Settings icon (gear with wrench) in the launcher, run the "Displays" and ensure that they are set up the way you want, ie. not mirrored, launcher display, left/right, resolutions, etc.  Try "Detect Displays" if necessary.

---

### Post by dave4444 on 2015-04-10
Hi Mikael and ubfan1,

Firstly apologies for taking so long in replying to all your suggestions, the PC has been back to ASUS for a new motherboard as it decided not to boot up one day . . .  

I have it back now put a fresh install of Ubuntu 14.10 on it as suggested and still have the same issue.

Unfortunately I don't have access to another 1920x1080 display but I have  used Ubuntu and Windows on it in the past at this resolution with no problems 

I have also checked that the displays are not  mirrored, launcher display, left/right, resolutions, etc. and tried "Detect  Displays" as suggested.                 

I think you may be right about the EDID information being wrong as it  lists my TV in Display Settings as a "Toshiba America Info Systems Inc  72" . This is incorrect as it is a 37" Toshiba model RV685D. 

I have checked  X.org.log as suggested and cant find any errors, I have pasted at the bottom of this post what I "think" is information relevant to the EDID.

How do I modify the EDID so that the OS gets the correct information?

Thanks again for all your help! 



[QUOTE 28.328] (II) intel(0): EDID vendor "TSB", prod id 264
[    28.328] (II) intel(0): Using EDID range info for horizontal sync
[    28.328] (II) intel(0): Using EDID range info for vertical refresh
[    28.328] (II) intel(0): Printing DDC gathered Modelines:
[    28.328] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz eP)
[    28.328] (II) intel(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[    28.328] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    28.328] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    28.328] (II) intel(0): Modeline "1280x768"x0.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz e)
[    28.328] (II) intel(0): Modeline "1280x768"x0.0   68.25  1280 1328 1360 1440  768 771 778 790 +hsync -vsync (47.4 kHz e)
[    28.328] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    28.328] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    28.328] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    28.328] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    28.328] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    28.328] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    28.328] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    28.328] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    28.328] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    28.328] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    28.328] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    28.328] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    28.329] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    28.329] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    28.329] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    28.329] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[    28.329] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    28.329] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    28.329] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    28.329] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[    28.329] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    28.329] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[    28.329] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[    28.329] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    28.329] (--) intel(0): HDMI max TMDS frequency 225000KHz
[    28.573] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.121] (II) intel(0): resizing framebuffer to 1360x768
[    30.124] (II) intel(0): switch to mode 1360x768@60.0 on HDMI1 using pipe 0, position (0, 0), rotation normal, reflection none
[    32.476] (--) intel(0): HDMI max TMDS frequency 225000KHz
[    32.790] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[    32.848] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[    32.910] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    32.980] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    32.985] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    32.990] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    32.996] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.002] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.007] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.013] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.019] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.025] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.030] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.036] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.042] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.047] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.053] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.059] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.064] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.070] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.075] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.080] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    33.086] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    51.712] (--) intel(0): HDMI max TMDS frequency 225000KHz
[    52.508] (--) intel(0): HDMI max TMDS frequency 225000KHz
[   313.085] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[   908.152] (--) intel(0): HDMI max TMDS frequency 225000KHz
[   909.592] (--) intel(0): HDMI max TMDS frequency 225000KHz
[   927.012] (--) intel(0): HDMI max TMDS frequency 225000KHz
[  4013.923] (--) intel(0): HDMI max TMDS frequency 225000KHz
(END)
][/QUOTE]

---

### Post by dave4444 on 2015-04-10
Some more information on the problem, however I am not sure if they are related . . . 

I installed xrandr and now can set 1920x1080, but only at 24hz, 25hz and 30hz (ideally I would like 60hz!) 

When the PC boots there is no image on HDMI unless I have the VGA cable connected as well (which is annoying as the TV is wall mounted and the connector is on the back)

Cheers,

dave4444

---

### Post by Mikael Hartzell on 2015-04-25
Hi :)  Unfortunately I don't know how to correct the EDID information. Somewhere I think I saw a method of overriding EDID using Xorg.conf.  As you got the computer working at 1920x1080, this is very promising and I just ordered the device myself :)  If I ever get the computer, I will post my findings. I have two HDTV's here both equipped with HDMI, so I can troubleshoot the possible display problem.

---

### Post by Mikael Hartzell on 2015-04-28
Hi :)  The computer store just told me that these computers are out of stock, and they can't send me one. I'm sorry, but now I can not help you to debug your problem.  If the problem was in the Intel display driver I think you could not get the display to work in the 1920 x 1080 resolution. So I think it boils down to the wrong EDID anyway.

---

