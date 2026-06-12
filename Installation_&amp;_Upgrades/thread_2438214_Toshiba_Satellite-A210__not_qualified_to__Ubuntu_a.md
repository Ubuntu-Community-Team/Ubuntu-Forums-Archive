---
title: "Toshiba Satellite-A210  not qualified to  Ubuntu and should exit ?"
date: 2020-03-07
forum: Installation &amp; Upgrades
---

### Post by safaia on 2020-03-07
My Toshiba Satellite-A210  not qualified to latest  Ubuntu and should exit the Ubuntu world ?

Any recommendation for this low [FONT=arial]ca·pa·bil·i·ty ?[/FONT]
I checked the system requirement on Ubuntu website, 
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

[LIST]
[*=left]2 GHz dual core processor[FONT=inherit][/FONT]
[*=left]4 GiB RAM (system memory)
[/LIST]
[LEFT][FONT=inherit]
My laptop is 
 [FONT=georgia]memory      1884MiB System memory[/FONT][FONT=georgia]  processor   AMD Athlon(tm) 64 X2 Dual-Core Processo
------------------------------------------------------------------[/FONT]
[FONT=georgia]Satellite-A210:~$ lshw -short[/FONT]
[FONT=georgia]WARNING: you should run this program as super-user.[/FONT]
[FONT=georgia]H/W path         Device      Class       Description[/FONT]
[FONT=georgia]====================================================[/FONT]
[FONT=georgia]                             system      Computer[/FONT]
[FONT=georgia]/0                           bus         Motherboard[/FONT]
[FONT=georgia]/0/0                         memory      1884MiB System memory[/FONT]
[FONT=georgia]/0/1                         processor   AMD Athlon(tm) 64 X2 Dual-Core Processo[/FONT]
[FONT=georgia]/0/1/0                       memory      128KiB L1 cache[/FONT]
[FONT=georgia]/0/1/1                       memory      256KiB L2 cache[/FONT]
[FONT=georgia]/0/100                       bridge      RS690 Host Bridge[/FONT]
[FONT=georgia]/0/100/1                     bridge      RS690 PCI to PCI Bridge (Internal gfx)[/FONT]
[FONT=georgia]/0/100/1/5                   display     RS690M [Radeon Xpress 1200/1250/1270][/FONT]
[FONT=georgia]/0/100/4                     bridge      Advanced Micro Devices, Inc. [AMD/ATI][/FONT]
[FONT=georgia]/0/100/5                     bridge      RS690 PCI to PCI Bridge (PCI Express Po[/FONT]
[FONT=georgia]/0/100/5/0       eth0        network     RTL8101/2/6E PCI Express Fast/Gigabit E[/FONT]
[FONT=georgia]/0/100/6                     bridge      RS690 PCI to PCI Bridge (PCI Express Po[/FONT]
[FONT=georgia]/0/100/12                    storage     SB600 Non-Raid-5 SATA[/FONT]
[FONT=georgia]/0/100/13                    bus         SB600 USB (OHCI0)[/FONT]
[FONT=georgia]/0/100/13.1                  bus         SB600 USB (OHCI1)[/FONT]
[FONT=georgia]/0/100/13.2                  bus         SB600 USB (OHCI2)[/FONT]
[FONT=georgia]/0/100/13.3                  bus         SB600 USB (OHCI3)[/FONT]
[FONT=georgia]/0/100/13.4                  bus         SB600 USB (OHCI4)[/FONT]
[FONT=georgia]/0/100/13.5                  bus         SB600 USB Controller (EHCI)[/FONT]
[FONT=georgia]/0/100/14                    bus         SBx00 SMBus Controller[/FONT]
[FONT=georgia]/0/100/14.1                  storage     SB600 IDE[/FONT]
[FONT=georgia]/0/100/14.2                  multimedia  SBx00 Azalia (Intel HDA)[/FONT]
[FONT=georgia]/0/100/14.3                  bridge      SB600 PCI to LPC Bridge[/FONT]
[FONT=georgia]/0/100/14.4                  bridge      SBx00 PCI to PCI Bridge[/FONT]
[FONT=georgia]/0/100/14.4/6                bus         R5C832 IEEE 1394 Controller[/FONT]
[FONT=georgia]/0/100/14.4/6.1              generic     R5C822 SD/SDIO/MMC/MS/MSPro Host Adapte[/FONT]
[FONT=georgia]/0/100/14.4/6.2              generic     R5C592 Memory Stick Bus Host Adapter[/FONT]
[FONT=georgia]/0/100/14.4/6.3              generic     xD-Picture Card Controller[/FONT]
[FONT=georgia]/0/101                       bridge      K8 [Athlon64/Opteron] HyperTransport Te[/FONT]
[FONT=georgia]/0/102                       bridge      K8 [Athlon64/Opteron] Address Map[/FONT]
[FONT=georgia]/0/103                       bridge      K8 [Athlon64/Opteron] DRAM Controller[/FONT]
[FONT=georgia]/0/104                       bridge      K8 [Athlon64/Opteron] Miscellaneous Con[/FONT]
[FONT=georgia]/0/2             scsi4       storage     [/FONT]
[FONT=georgia]/0/2/0.0.0       /dev/cdrom  disk        CDDVDW TS-L632H[/FONT]
[FONT=georgia]/1               wlan0       network     Wireless interface[/FONT]
[/FONT][/LEFT]

---

### Post by oldfred on 2020-03-07
Those are the requirements for Ubuntu.
Below it mentions Lightweight flavors which is what you then should use.
Light weight flavors
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

My old laptop had 12.04 Ubuntu but using fallback/flashback which was not Unity but old gnome panel gui which also is lightweight. Even though I retired that laptop which was 64 bit with only 1.5GB of RAM, I installed 16.04 to see if it worked.
It actually just barely ran Ubuntu 16.04, where 12.04 could not, and with fallback was functional, just not speedy. 

I am now running gnome-panel in 20.04, just because I prefer it.
[https://wiki.gnome.org/Projects/GnomePanel](https://wiki.gnome.org/Projects/GnomePanel)

---

### Post by crip720 on 2020-03-07
Have a Toshiba A20 with P4 cpu and 1.2GBs ram.  Runs Lubuntu quite well if you don't try too many things at once.  Gnome desktop might be to heavy but the light weights that Oldfred mention should work well.

---

### Post by safaia on 2020-03-07
I will check [COLOR=#000000]Lubuntu, Thanks. :)[/COLOR]

---

