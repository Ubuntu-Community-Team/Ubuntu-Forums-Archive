---
title: "Trouble booting/installing live USB"
date: 2013-07-05
forum: Installation &amp; Upgrades
---

### Post by hamgooof on 2013-07-05
[SIZE=2][FONT=arial]Hi, I've had some problems for the past couple of weeks installing any variants of Linux, Debian/Ubuntu (and some others I cannot remember the name of).

My new (current) issue is that after getting all the way to trying out Ubuntu 64 bit (both 12.04.2 and 13.04) my mouse and keyboard won't work, this happened after the problem below. The specs of my PC is at the end of the post.

[SUB]Originally the problem was I could install the operating system, but my keyboard/mouse wouldn't work (wireless logitech).

Now the issue is I'm using a 4GB memory stick which I have tried both 13.04 and 12.04 LTS, as well as downloading them a couple of times each in case there was an error downloading. When booted into EFI mode (I have Win 8) the back light on my keyboard and lights on my mouse stop, so on the loading screen I can't press F6 to change any settings which has been advised for my issue is other reports.

I then see the loading screen for a minute or two before being shown '[COLOR=#333333](initramfs) Unable to find a medium containing a live file system.' I get this whether trying to live boot/install/check disk.[/COLOR]

[COLOR=#333333]My keyboard is still un-accessible in this state so it's hard to get any information from it.[/COLOR][/SUB]

[COLOR=#333333]Notes:[/COLOR]
[COLOR=#333333]I have tried with both fast boot enabled/disabled with no success in getting further.[/COLOR]
[COLOR=#333333]I have tried both EFI and legacy booting from USB.[/COLOR]
[COLOR=#333333]My SATA configuration is set to AHCI in the bios.[/COLOR]
[COLOR=#333333]I don't have a PS/2 keyboard or mouse.[/COLOR]
[COLOR=#333333]When using EFI I get an error 'USB 2-1 device descriptor read/64 error - 32[/COLOR]
[COLOR=#333333]I tried ticking 'acpi=off' and 'noapic' in legacy mode as I had control of my keyboard in the immediate state after selecting try ubuntu - after fully loading I was just presented with a black screen.
[/COLOR]Tried USB in both USB 2.0 and 3.0 ports.


[COLOR=#333333]Specs:[/COLOR]
[COLOR=#333333]AMD bulldozer 8350[/COLOR]
[COLOR=#333333]Gigabyte motherboard GA-990FXA-UD5 with latest firmware
[/COLOR]2 x 8 GB RAM modules

[COLOR=#333333]Keyboard:[/COLOR]
[COLOR=#333333]Razer Blackwidow Ultimate 2013[/COLOR]

[COLOR=#333333]Mouse:[/COLOR]
[COLOR=#333333]R.A.T 7[/COLOR]


[COLOR=#333333]Any tips/help would be very much appreciated! Thanks in advance.[/COLOR][/FONT][/SIZE]

---

### Post by C.S.Cameron on 2013-07-05
Are you using 64bit Ubuntu?

---

### Post by hamgooof on 2013-07-05
I've mainly been trying 64x variants, and that is what I am currently trying (as I read on the wiki that it is needed for EFI systems) but I have given 32bit a couple of tries, with no success.

One thing I did just find out - even with my USB thumbstick removed when I boot my computer it comes up with GRUB recovery in which I can use my keyboard, so for windows I just boot off my SSD (which I have partitioned ready for Ubuntu :()

---

### Post by hamgooof on 2013-07-05
Formatted a 70GB hard drive in my PC and wrote the ISO (tried both 12.04.2 & 13.04) to it. I then booted using EFI and it gets ALL the way through, but my mouse and keyboard don't work.

My mouse has the DPI light on but after disconnecting and reconnecting it loses it - and the keyboard never seems to get any power.

Any help would be much appreciated.

---

### Post by Krupski on 2013-07-05
> **hamgooof said:**
> Formatted a 70GB hard drive in my PC and wrote the ISO (tried both 12.04.2 & 13.04) to it. I then booted using EFI and it gets ALL the way through, but my mouse and keyboard don't work.

My mouse has the DPI light on but after disconnecting and reconnecting it loses it - and the keyboard never seems to get any power.

Any help would be much appreciated.

I'm not an expert on USB ports, but what I've found is that typically USB 3.0 ports don't "work" until after a driver is loaded (i.e. there is no built in pre-boot BIOS support). So try to use USB 2.0 ports, better if they are built into your motherboard.

Also in the BIOS, be sure "USB support" or "Legacy USB" or something similar is enabled in order to have the BIOS activate the ports early in the boot process.

Lastly look at your powersave modes in the BIOS (S1 or S3). Some motherboards "sleep" so soundly (S3 mode) that even the USB ports are turned off unless specifically forced to be enabled. Try switching from S3 to S1 powersave mode (if your bios has it).

That's all I can think of. Sorry I don't have more.

---

### Post by hamgooof on 2013-07-06
I've tried Legacy USB on enable/disable and auto, one thing that did occur is when using Ubuntu 12.04.02,  edited the boot/launch commands to include acpi_osi=  and that gave me access to my mouse (once) last night. 

Thank-you very much for your input

---

### Post by fantab on 2013-07-06
If you have Windows8 then have you turned OFF 'Fast Startup'? To Turn OFF 'Fast Startup': [URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html
[/URL]'Fast Startup' keeps your Windows in Hibernation. We have to Shut Down Windows properly before installing Ubuntu.

---

### Post by hamgooof on 2013-07-06
Fastboot is already disabled - I have control of my mouse and keyboard again, I enabled IOMMU in the BIOS and it seems to allow me to use both my keyboard and mouse. Now time to try installing :D

---

