---
title: "uncompressing linux ... Ok, booting the kernel.   Then Hang...."
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by Fubie on 2006-07-14
Ok, Here's my little story.

I have an old Emachine with a celeron 600mhz that I decided to take my 1st real forray into Linux with.  I installed Dapper 6.06 and I loved it.  It was slow on that old machine but worked pretty well.

So I decided I wanted to put it on a faster machine to make it more usable.  So I bought an Emachine T6528.  Here are the specs.


CPU:  	AMD Athlon™ 64 3500+ processor with AMD 64 Technology
(2.2GHz, 2000MHz system bus, 512KB L2 cache)

Operating System: 	Genuine Microsoft® Windows® XP Home (SP2)

Chipset: 	NVIDIA® GeForce® 6100

Memory: 	512MB DDR (1 × 512MB), 400MHz (PC3200)
Expandable to 4GB

Hard Drive: 	160GB (7200rpm, 2MB cache)

Optical Drive: 	16x multiformat dual-layer DVD±RW
(Up to 8.5GB with dual-layer media)
Write max: 16x DVD±R, 6x DVD-RW, 8x DVD+RW, 4x DVD+R DL, 40x CD-R, 24x CD-RW
Read max: 16x DVD-ROM, 40x CD-ROM

Media Reader: 	9-in-1 media card reader (Memory Stick®, Memory Stick Pro®, MultiMediaCard™, Secure Digital™, CompactFlash®, MicroDrive, SmartMedia, xD, USB 2.0)

Video: 	NVIDIA® GeForce® 6100 GPU
Up to 128MB of shared video memory

PCI Express (PCIe x16) slot available

Sound: 	6-channel (5.1) high-definition audio

Network: 	10/100Mbps integrated Ethernet LAN (RJ-45 port)

Modem: 	56K ITU V.92-ready fax/modem (RJ-11 port)

Peripherals: 	Premium multimedia keyboard, 2-button wheel mouse, amplified stereo speakers

Ports/Other: 	5 USB 2.0 (1 in digital media manager, 4 in back), VGA external connector, parallel port, 2 PS/2 ports (keyboard and mouse), 5 audio ports (2 in front, 3 in back)



Now, Using the same disc I used to install onto my intel 600mhz I started up my new machine,  I received the initial screen asking me to select Run Live/ Install, Text mode, check cd, ect...

I chose to Run Live/Install.  I received the "uncompressing linux ... Ok, booting the kernel." and there it stayed.  No HD or CD activity at all.  I let it sit for 15min.

I then rebooted and ran the CD check.  The same thing happened.

I then re downloaded the 64bit iso, burned it to CD, same outcome.

I used another PC to burn it, Same outcome.

Tried a different brand of CD, Same Outcome.

Tried different software on 3 different PC's, Same outcome.

Tried the alternative iso's, Same outcome.

Tried Ubuntu 386 and 64bit Ubuntu and KUbuntu DVD ISO's, Same outcome.

Can anyone give me any clues?

By the way.  I left Windows on the HD along with a locked partition that it came with.  Could this be the issue?  Should I format the HD and try it?

Thanks for any help at all.

---

### Post by gerous on 2006-07-14
Got the same system (CPU) here.
Same error. Try the acpi=off option in the boot options

---

### Post by Fubie on 2006-07-14
> **gerous said:**
> Got the same system (CPU) here.
Same error. Try the acpi=off option in the boot options

Is that in the advanced options on the bottom right? F6 or something of the first screen I get with options?

---

### Post by gerous on 2006-07-15
exactly.. press f6 at the menu and later (after install) press ESC to enter grub settings and select the linux startup item press e select the line starting with kernel, press e again and enter acpi=off somwhere. press enter and then b to boot.. as root edit /boot/grub/menu.lst same way. than you are fine. 

hope that helps

---

### Post by Fubie on 2006-07-15
ok, I'm now getting another error immediatly after the booting kernel.

it's [4294670.844000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC

---

### Post by gerous on 2006-07-16
[http://www.ubuntuforums.org/showthread.php?p=1113623#3](http://www.ubuntuforums.org/showthread.php?p=1113623#3)

---

