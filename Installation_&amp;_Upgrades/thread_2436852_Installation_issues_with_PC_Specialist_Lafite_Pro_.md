---
title: "Installation issues with PC Specialist Lafite Pro 14&quot; / Insyde H2O Bios Intel RST"
date: 2020-02-14
forum: Installation &amp; Upgrades
---

### Post by glambert2804 on 2020-02-14
Hi,


I'm  having great difficulty in getting Ubuntu installed on my Lafite Pro  14".  During the Ubuntu installation, when you get to the screen to  partition the disk and install, the NVMe disk isn't showing up as an  option.  When running things like fdisk from the live USB, it cannot see  the disk at all.  It appears to be because the Insyde H2O BIOS is too  restrictive and I cannot disable the Intel Rapid Storage Technology  (RST).


PC Specialist so far  are refusing to provide any support as I'm trying to use Linux, despite  it being very clear when I configured the laptop that my intention was  to have no OS shipped with it and to install Linux.


If anyone can review the spec below and advise on what I can do to get Ubuntu installed on my laptop I'd appreciate it!



Thanks


```
Chassis & Display
Lafité Pro Series: 14" Matte Full HD IPS LED (1920 x 1080)
Processor (CPU)
Intel® Core™ i7 Quad Core Processor i7-10510U (1.8GHz, 4.9GHz Turbo)
Memory (RAM)
24GB 2666MHz DDR4 (1 x 16GB Corsair SODIMM + 8GB SOLDERED)
Graphics Card
INTEL® HD GRAPHICS (CPU Dependant) - 1.7GB Max DDR4 Video RAM - DirectX® 12
1st M.2 SSD Drive
2TB SAMSUNG 970 EVO PLUS M.2, PCIe NVMe (up to 3500MB/R, 3300MB/W)
Memory Card Reader
Integrated Micro-SD Memory Card Reader
AC Adaptor
1 x 65W AC Adaptor
Power Cable
1 x 1 Metre Cloverleaf UK Power Cable
Battery
1 x Lafité Battery 73WH
Sound Card
Intel 2 Channel High Definition Audio + MIC/Headphone Jack
Bluetooth & Wireless
GIGABIT LAN & WIRELESS INTEL® Wi-Fi 6 AX200 (2.4 Gbps) + BT 5.0
USB/Thunderbolt Options
1 x USB 3.1 PORT (Type C) + 1 x USB 3.1 PORT + 1 x USB 3.0 PORT
Keyboard Language
LAFITÉ PRO SERIES SINGLE COLOUR BACKLIT UK KEYBOARD
Operating System
NO OPERATING SYSTEM REQUIRED
Operating System Language
United Kingdom - English Language
Windows Recovery Media
NO RECOVERY MEDIA REQUIRED
Office Software
FREE 30 Day Trial of Microsoft® Office® 365 (Operating System Required)
Anti-Virus
NO ANTI-VIRUS SOFTWARE
Browser
Microsoft® Edge (Windows 10 Only)
Notebook Mouse
INTEGRATED 2 BUTTON TOUCHPAD MOUSE
Webcam
INTEGRATED 1MP HD WEBCAM
Warranty
3 Year Gold Warranty (2 Year Collect & Return, 2 Year Parts, 3 Year Labour)
Delivery
STANDARD INSURED DELIVERY TO UK MAINLAND (MON-FRI)
Build Time
FAST TRACK 3 WORKING DAY DISPATCH
Welcome Book
PCSpecialist Welcome Book - United Kingdom & Republic of Ireland
```

---

### Post by mips on 2020-02-14
In the bios you can try changing SATA Operation and select AHCI.
Try [COLOR=#242729][FONT=Arial]boot from the USB in the UEFI mode
[/FONT][/COLOR]Modify the boot option to add "nvme_load=YES" and remove "quiet splash ---"[COLOR=#242729][FONT=Arial]
See if possible to flash with clevo bios[/FONT][/COLOR]

---

### Post by glambert2804 on 2020-02-14
> **mips said:**
> In the bios you can try changing SATA Operation and select AHCI.
Try [COLOR=#242729][FONT=Arial]boot from the USB in the UEFI mode
[/FONT][/COLOR]Modify the boot option to add "nvme_load=YES" and remove "quiet splash ---"[COLOR=#242729][FONT=Arial]
See if possible to flash with clevo bios[/FONT][/COLOR]

I don't have the option to change SATA to AHCI, I only have Intel RST as an option.

---

### Post by mips on 2020-02-14
> **glambert2804 said:**
> I don't have the option to change SATA to AHCI, I only have Intel RST as an option.

Try this [https://linustechtips.com/main/topic/911741-how-to-disable-intel-rapid-storage-technology/?tab=comments#comment-12336409](https://linustechtips.com/main/topic/911741-how-to-disable-intel-rapid-storage-technology/?tab=comments#comment-12336409)

---

