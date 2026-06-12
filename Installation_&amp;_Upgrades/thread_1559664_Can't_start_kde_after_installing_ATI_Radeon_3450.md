---
title: "Can't start kde after installing ATI Radeon 3450"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by SillyKirby on 2010-08-23
I can't get kde to start. I boot through the blue ubuntu 10.04 splash screen normally, so my video card is putting out something, but then i drop into a tty terminal. I log on ok, but when i do startkde from the command line i get a 
message saying can't connect to xserver, when i do startx, i get these errors: (i can't stuff them here cuz i don't have a mouse or a cut and paste ability)

EE) NVIDIA: Failed to load the NVIDIA kernel module.
.
.
EE) No drivers available.

But here's the backstory: I have a ASUS M3N78 PRO MB with an on board Nvidia GeForce 8300 graphics capability. It was intermittently failing, so i disconnected it put in an ATI RADEON PowerColor HD 3450 graphics card, and then my problems started.

Seems to me I must have the Nvidia driver since i can boot to KDE fine using the Nvidia onboard analog output (at least 
some of the time). Supposedly Lucid Lynx has the ATI drivers for my card preinstalled, plus the new card does drive the 
splash screen. Is there some clash in some script between the Nvidia on the MB and my ATI Card? 

I upgraded to GRUB2, reconfigured xserver-xorg, tried to run jockey from the command line and failed, tried sudo 
nvidia-xconfig. Nothing changed anything. 

So i am really needing some tips, solutions, ideas, or directions. i am kind of stupid at this type of thing, so i 
apologize for bothering people. but i am stuck, what should i do?

---

### Post by xaliqen on 2010-08-23
I would start by uninstalling any proprietary nvidia drivers that may be present.  You can also try disabling the nvidia IGP via the BIOS if you think there's some kind of strange conflict going on.

If things still aren't working, then [work on your xorg.conf]("http://wiki.archlinux.org/index.php/Xorg") file and keep falling back into more rudimentary graphics modes until you can get into gnome or kde (also see these [troubleshooting tips]("http://hubpages.com/hub/How-to-configure-Xorg-in-Ubuntu")).

---

### Post by SillyKirby on 2010-08-24
Thanks xaliqen for the help. It got me started.
I found the most help in https/help.ubuntu.com/community/RadeonDriver

I checked lspci -nn | grep VGA and got:

silly@wrentit:~$ lspci -nn | grep VGA
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV620 LE [Radeon HD 3450] [1002:95c5]

So it was finding my new video card

Then i did an lspci and got:
silly@wrentit:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev 
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev 
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev 
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev 
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (r)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI modev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransponfiguration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Contro
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneontrol
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Contro
01:0a.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
02:00.0 VGA compatible controller: ATI Technologies Inc RV620 LE [Radeon HD 3450]
02:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]

So i had all kinds of nVidia stuff on my MB so i was afraid to start purging nvidia. 

First i tried to edit the /etc/X11/xorg.conf to include:
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
    BusID          "PCI:2:0.0"
EndSection

But it didn't work, ie startx still failed to find drivers. Then i noticed that ubuntu help said, "You can safely take away your xorg.conf and your computer will run fine." So i think, "really???" and move xorg.conf to xorg.conf.useless and then i tried startx, and low and behold, kde starts up. wow, how did that happen:)

Anyway, I call this problem solved. (well almost, i currently have a really dim and low contrast display, but that will be a problem for tomorrow:) thanks.

---

