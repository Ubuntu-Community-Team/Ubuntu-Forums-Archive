---
title: "Ubuntu 16.04 won't boot in amd A4 5300"
date: 2017-01-28
forum: Installation &amp; Upgrades
---

### Post by conormcgregor on 2017-01-28
Hi guys, I've been using a new pc with these specs:

motherboard: [FONT=arial]MSI[/FONT][FONT=arial] A78M-E45
cpu + gpu (apu) amd a4 5300 (gpu 7480D)

And the pc crashes (appears gnu grub) when installing ubuntu 16.04, both with bootable usb AND upgrading from 15.10.

The system worked fine with ubuntu 15.10 and ubuntu 14.04, but doesn't work with ubuntu 16.04, it appears gnu grub 2 after rebooting system.

I haven't tried to upload from 14.04 since I will get the same result.

Does anybody know what's going on?

Another issue I have is I can't get realistic temperature with psensors and lm-sensors (I get 1ºC), (but bios gives good temperatures). I read this was maybe 'cause ubuntu hadn't drivers to check temperature for my motherboard, but maybe somwbody knows an alternative.[/FONT]

---

### Post by MartiusElbus on 2017-03-20
Bit late maybe, but...

I have the same AMD APU A4-5300 on a MSI A88XM-E35 V2. I had the same problem with Ubuntu server after updating the kernel right after installing the system. Something goes wrong when the system loads the Radeon graphics driver. Since i run my servers headless i disabled the loading of the graphic driver in the bootloader (nomodeset). See this here for more on this; [https://ubuntuforums.org/showthread.php?t=1613132](https://ubuntuforums.org/showthread.php?t=1613132)

Temp sensors seem ok on my rig. Might be that there were some updates on the BIOS or kernel that fix that one in the meantime. 

My workstation uses the same motherboard but with an AMD X4 845 which requires a dedicated graphics card (I prefer Nvidia) so no issues with the board itself.

---

