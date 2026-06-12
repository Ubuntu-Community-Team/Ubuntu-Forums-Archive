---
title: "Sapphire Radeon HD 6850 + Ubuntu 12.04 + computer freezes after installation"
date: 2013-06-28
forum: Installation &amp; Upgrades
---

### Post by mlu17 on 2013-06-28
Hey guys,

I already made a 1st post here on this forum because I have serious problems after the installation of Ubuntu 12.04.
User oldfred helped me to figure out that it might be a graphic driver problem. 
He suggested that I make a new thread with the graphic card model in the thread topic name.

So here is the situation:

I have a desktop computer with 3 built Harddisks.

- SSD (OCZ Agility 3): Windows 8
- HDD (Western Digital): Files
- SSD (OCZ Vector): Ubuntu 12.04

My motherboard is a Gigabyte MA-785GT-UD3H rev 1.0 with onboard Radeon HD 4200 graphics.
My Bios settings are set to AHCI mode and all disks get properly detected.
Windows 8 btw was only a online upgrade to Windows 7 which is running without problems for a cpl of years now.

I additionally have a PCI-E Sapphire Radeon HD 6850 attached to my board where my monitor is connected via HDMI cable.

I installed Ubuntu 12.04 on my new SSD (OCZ Vector) with a USB Stick (which I made with [this]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") tool).
I partitioned my SSD and installed everything without problems. The bootloader I installed on / partition.
Afterwards I booted into Windows 8 and started EasyBCD to add a Windows Bootloader entry and everything works fine.
After a restart I can choose between Windows 8 or Ubuntu and when I click Ubuntu I get to the common Grub bootloader where I can choose the normal Kernel or recovery mode or memtest mode or whatever.

The problem starts when Ubuntu is booted and I am on the Desktop. From now on, I have about 2-3 Minutes til my whole computer freezes and everything is stucked. No mouse movement or keyboard input possible. No tty or anything else.
And then I get a blackscreen with a kernel panic. I couldn't get everything on the photo, otherwise the part you see wouldn't be clear to read.
[ATTACH=CONFIG]244229[/ATTACH]

I also attached a Xorg logfile which I archived from within recovery mode.
[ATTACH]244230[/ATTACH]

What would the next step be to figure out what the problem exactly is or how to get this sorted out?
Please remember that I only have about 2 minutes when I booted into the Desktop til the computer freezes.

Thank you very much,

Regards,
Michael

---

### Post by Mark Phelps on 2013-06-28
I think the problem may be that AMD restricted drivers are not supported for Ubuntu versions 12.04.2 and newer for the AMD HD 2x/3x/4d series chipsets.  If you're running that version of Ubuntu, and have loaded the AMD drivers, they are probably causing the crash.  Even though the restricted drivers ARE compatible with the HD 6850, they are probably conflicting with the 4200.

Have you disabled the 4200 in the BIOS?

---

### Post by mlu17 on 2013-06-28
I have disabled the 4200 in BIOS. 
I only installed Ubuntu 12.04 no further software nor drivers or anything else which is due to the small laps of time I have til the computer freezes.

---

### Post by Mark Phelps on 2013-06-28
OK ... well restricted driver conflict was the only thing that came to mind that would quickly crash your PC.

I don't know how well the default Radeon drivers work with a 6850, but I have an onboard 4290 and they work fine in 12.10 and 13.04.

One thing you could try that got me around a Radeon driver problem in Mint15 is adding "xofrcevesa" to the kernel parameters in the GRUB boot file.

The general way to do that is to start pressing the Shift key when booting into Ubuntu, and when the GRUB menu comes up, press a Tab key to open an editor on the boot command line.  You'll see a line with parms like "quiet" and "splash" in it.  You edit that line to remove "quiet" and replace "splash" with "xforcevesa" -- and then press the Enter key.  That will continue the boot process.  Since you edited it this way, it does not save your changes, and any future boots will use the old parms.

---

### Post by mlu17 on 2013-06-29
xforcevesa didn't change anything. computer still freezes after 1-2 minutes.
another question: I just noticed that I totally disabled the onboard 4200 AFTER the installation of Ubuntu. So does this make any difference? Should I reinstall Ubuntu?

okay, this is some really weired behaviour. after Ubuntu booted to the desktop I immediatly switched to tty because I thought I might can do some stuff in the console but after the first command I got again a kernel panic or whatever. 
can you guys do anything with that provided information on the blackscreen?
[ATTACH=CONFIG]244254[/ATTACH][ATTACH=CONFIG]244255[/ATTACH]

Edit: 
Alright guys, I could sort it out and you won't believe what the problem was :)
Obviously the driver for my linksys ae-3000 wlan-stick was causing the kernel panics.
I switched to a dlink dwa-140 b3 stick and everything works fine now! 
Thank you all for your help!

---

