---
title: "Can you edit and apply ATI power scheme BEFORE an install?"
date: 2013-11-29
forum: Installation &amp; Upgrades
---

### Post by anderssoncolin on 2013-11-29
[FONT=Calibri]I have a HP Dv6 laptop, and I can’t install Ubuntu on it. 

Actually, I can’t install Debian, Linux Mint or any modern Linux distro either. I suppose that I could try some command line version out there, but what would the point of that be? This laptop has a hybrid graphics system with ATI Radeon Mobile 5650 and ATI Radeon Mobile 4200. It also has 4Gb of RAM. I am trying to set up a dual boot system. The laptop already has Windows 7 on it.

[/FONT]```

Operating System: Windows 7 Home Premium 64-bit (6.1, Build 7601) Service Pack 1 (7601.win7sp1_gdr.130828-1532)
System Manufacturer: Hewlett-Packard
System Model: HP Pavilion dv6 Notebook PC
BIOS: Default System BIOS
Processor: AMD Athlon(tm) II P320 Dual-Core Processor (2 CPUs), ~2.1GHz
Memory: 4096MB RAM
Available OS Memory: 3834MB RAM

Card name: AMD M880G with ATI Mobility Radeon HD 4250  
Manufacturer: ATI Technologies Inc.
Chip type: ATI display adapter (0x9712)
DAC type: Internal DAC(400MHz)

Card name: ATI Mobility Radeon HD 5650
Manufacturer: ATI Technologies Inc.
Chip type: ATI display adapter (0x68C1)
DAC type: Internal DAC(400MHz)
Current Mode: 1366 x 768 (32 bit) (60Hz)

```[FONT=Calibri]
[/FONT]
[FONT=Calibri]The reason why I can’t install Ubuntu (or any of those other distros) is, from what I gather having googled to see what the problem could be, that the hybrid graphics of my laptop is a problem. It seems to be a problem across all the Linux distros, so Ubuntu is certainly not unique in that way. This is not supposed to be a whine. I hope you don’t take it that way. I just want to explain the background.[/FONT]

[FONT=Calibri]What I have done myself to try to cool the laptop down is:[/FONT]

[FONT=Calibri]* I have cleaned the fan as far as I can without actually opening the laptop and voiding my warranty. This means blowing compressed air through the vents and holes in my laptop.[/FONT]
[FONT=Calibri]* I have taken out all my ice packs from the freezer, and have put the laptop on it.[/FONT]
[FONT=Calibri]* I have scoured the net to find a solution, and I think I’ve found one. I should edit the power scheme of the AMD drivers. I should set it to low.[/FONT]

[FONT=Calibri]However, Ubuntu will still only get about halfway through an install before the temperature reach 90 or 100 C. The laptop protection in the BIOS shuts the computer down, and I have to fix my boot loader.[/FONT]

[FONT=Calibri]So, TL;DR: is there any way to edit the power saving scheme of the ATI graphics in Ubuntu [/FONT][FONT=Calibri]*before*[/FONT][FONT=Calibri] an install? I mean, edit the install script in a way that the power saving scheme is used by the system when it boots from my USB.

What I want to do is to set the ATI power scheme to low power. Hopefully then I'll be able to install Ubuntu. Thank you in advance.[/FONT]

---

### Post by heir4c on 2013-11-29
And what if you use the "nomodeset" or "xforcevesa" boot-parameter?

---

### Post by anderssoncolin on 2013-12-01
Unfortunately, I don't know how to do that. I'm a linux noob in most respects. My research led me to the solution outlined in my OP.

What does those commands do? How do I change boot parameters?

---

### Post by heir4c on 2013-12-01
When you boot with the live-cd/dvd or live-usb you get some purple background with 2 icons at the bottom. When you see this icons than you click quick on a key (any key you like).
Than you can choose your Language. After that you can click on F6. And there you see the nomodeset. Use the space-key to check the line.
See also here:
(Scroll a little bit down untill you see: "How to enable kernel options on the livecd (before install)") 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

