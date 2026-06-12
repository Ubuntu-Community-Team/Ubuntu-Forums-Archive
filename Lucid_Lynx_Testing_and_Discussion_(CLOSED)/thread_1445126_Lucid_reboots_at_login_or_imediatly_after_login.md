---
title: "Lucid reboots at login or imediatly after login"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by simion314 on 2010-04-02
This problem always happend to me, i tried the ubuntu alpha3 and now the kubuntu version.
iI have a kubuntu alpha 3 cd, booted from it and at login the laptop rebooted. I tried again, Press F6 at grub menu and chose acpi=off noapic and nomodeset. After this i booted and installed kubuntu successfully. I started in safe mode and made all the updates, now after reboot i  get that reboot at login or if i try to login in fluxbox after a few seconds after fluxbox loads. I tried using acpi=off noapic and nomodeset, i tried xforcevesa and even creating a xorg.conf and set vesa insted of radeon. When using vesa X do not start, otherwise X starts and the laptop reboots at login. I can't figure out in what sbsystem is the bug and what it trigers it? if i stay and look ad KDM screen the bug does not happen only during login or after that. 
I upgraded a ubuntu 9.10 to 10.04 , same problem ,a few seconds after login the plaptop rebooted, i do not try to fix that because it was not a clean install and the devs were trying to backport some video stuff from latest kernel.
I found nothing similar using google, the launchpad can't be used now to submit bugs.The log files are clean.i am using a ATI card with radeon driver
Any idea? any sugestions?  

This is my hardware:
simi@simi-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
08:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
08:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
08:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 09)
08:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:00.0 Ethernet controller: ADMtek 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 11)

---

