---
title: "Monitor went dead after 16 install"
date: 2016-08-06
forum: Installation &amp; Upgrades
---

### Post by schmitta on 2016-08-06
I foolishly said yes to the question do I want to install 16 (04?). Everything went fine until the restart then the bongos sounded but the monitor was as if it was unplugged from vga. It is a VGA gateway ev910. I can't do anything without the monitor. Thanks for your help.

---

### Post by grahammechanical on 2016-08-06
Some more information about the hardware and set up would be useful. CPU? Amount of RAM? Video adapter? Dual booting or is Ubuntu the only OS? For example, if you are dual booting then you will be getting an boot menu (Grub) but if you are not dual booting the Grub boot menu will be hidden and you will need to press Shift while the motherboard is loading to bring up the Grub boot menu.

Either way, at the boot menu select Advanced options for Ubuntu. Select a Linux kernel with recovery mode and then at the recovery menu select Resume. If that gets you to a login screen and from there to a working desktop then go to System Settings>Software & Updates>Additional Drivers tab and change video drivers. You need to be connected to the internet and to allow time for Additional Drivers to find the drivers off of the internet.

Regards

---

### Post by schmitta on 2016-08-07
A quick reply to your reply - I will answer more data when I have a chance to look. Note that upon cold start boot the bios displays on the monitor properly with the monitor ON button turning GREEN indicating the computer has been recognized through the VGA connection. Then about 5 seconds later the BONGOS sound. Then the monitor ON button turns TAN indicating no computer connected on VGA and the monitor starts to display diagnostics as it would when the computer is shut off and nothing is live on the VGA connection. When I was running the previous LTS (14?) the monitor required no special driver as I guess your system is setup for standard VGA.

---

### Post by schmitta on 2016-08-12
CPU: AMD A4-3400 APU with Radeon HD Graphics 2.7 GHz Microcode Patch Level 3000027
Memory: 8GB 1333 MHz
MotherBoard: ASUS F1A55-M LX PLUS R2.0
BIOS: UEFI 0401 x64
On board VGA PCI Video
Monitor: Gateway EV910 VGA

When it comes up a cursor flashes; When enter is hit a page comes up asking if you want to run or install 16.04; Then at the bottom of the page 
symbols appear that look like a battery then equal sign then a little man in a circle. then nothing; then bongos sound.

---

### Post by schmitta on 2016-08-13
> [COLOR=#000000] if you are not dual booting the Grub boot menu will be hidden and you will need to press Shift while the motherboard is loading to bring up the Grub boot menu.[/COLOR]

[COLOR=#000000]Either way, at the boot menu select Advanced options for Ubuntu. Select a Linux kernel with recovery mode and then at the recovery menu select Resume. If that gets you to a login screen and from there to a working desktop then go to System Settings>Software & Updates>Additional Drivers tab and change video drivers. You need to be connected to the internet and to allow time for Additional Drivers to find the drivers off of the internet.[/COLOR]

I tried your above suggestions, grahammechanical, and got to the desktop. 

From System Settings I selected Software and Updates and the Additional Drivers tab found one driver. It said device (which I guess was the VGA) not working. It supplied two options 1) Using processor microcode firmware for AMD CPUs from AMD64-microcode (Proprietary) and 2) Do not use the device. I tried both from three different Linux recovery versions (44-42) with no luck with the monitor working from a cold start. 

For the Displays tab of System Settings it said it was using the Built In Display and Launcher Placement [Built In Display]. 

I used Detect Displays with no change.

Details stated:
Processor: AMD A4-3400 APU with Radeon (tm) HD Graphics x 2
Graphics: Gallium 0.4 on llvmpipe (LLVM 3.8 128 bits)
OS Type: 64 bits

Software on computer is up to date.

Single boot system using Ubuntu Linux 16.04

I guess for now I can use the system by using the recovery mode you stated above but would like to get it to the point where the display worked upon cold start.

---

### Post by schmitta on 2016-08-13
oops

---

