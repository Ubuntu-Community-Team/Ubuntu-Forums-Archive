---
title: "Ubuntu Regular, Ubuntu Alternate installer, Kubuntu, ThinkGOS - None of them worked"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by dministrator on 2010-05-22
Hello. 

I was given free an older computer, whose hard drive was wiped clean - no OS.

I tried to install every one of the above flavors and it's been a nightmare. After spending considerable amount of time with no successful result, I tried to install XP and it got installed, no problem in the first attempt. 

I need the community's help to get me through this. 

Here's my computer specs:

CD Drive: OEM CD-ROM F563E
Hard Drive: IC35L060AVV207-0
Processor: Intel Pentium 4 CPU
Memory: 256MB
Hard Drive capacity: 40MB

Ubuntu, Ubuntu alternate version of the installer, gave me the following messages:
> 
udevadm settle-timeout of 180 seconds reached, the event queue contains:
/sys/devices/pci0000:00/0000:00:11.1/host0/target0:0:0/0:0:0:0/block/sro (879)
/sys/devices/pci0000:00/0000:00:11.1/host0/target0:0:1/0:0:1:0/block/sda (890)
/sys/devices/pci0000:00/0000:00:11.1/host0/target0:0:1/0:0:1:0/block/sda/sda1 (891)
/sys/devices/pci0000:00/0000:00:11.1/host0/target0:0:0/0:0:0:0 (904)

[181.444268] Kernel Panic - not syncing: Attempted to kill init!


After a while, it goes to the install screen, with five flashing dots under "Ubuntu" and stays there forever.

I got similar experience with Kubuntu.

When I tried installing gOS, it went to (initramfs) prompt and stayed there forever. I've used the same gOS disc to install on a much much older computer, where it installed no problem.


All the above happened even when I tried the "Test Disc" option as well as "Try before installing" options in all of the above flavors.

All the CDs were burned at the slowest speed possible with my burner (12x).

Ubuntu community, please help me get through this. I want to have Ubuntu or Kubuntu as the only OS in this PC. I'm a newbie when it comes to Linux and party. 

Thank you very much.

---

### Post by BIGCJ on 2010-05-22
I'm just wondering what kind of P4 is it also the motherboard.
And what are the settings in the BIOS for you hard drive?

---

### Post by dministrator on 2010-05-22
BigCJ> Since it was given to me, I don't have much information on the PC other than the fact that it is a custom built system. 

I used scanner from Crucial.com and got the following information about the computer:

CPU Manufacturer:  GenuineIntel 
CPU Family:   Intel(R) Pentium(R) 4 CPU 1.60GHz Model 1, Stepping 2 
CPU Speed:  1599 MHz 
Dual Channel Support:   N.A. 
System Manufacturer:  VIAP4X
System Model: AWRDACPI
Motherboard Manufacturer: U COMPANY
Motherboard Model: U8668


In BIOS, I've set the boot order as

1) CDROM 
2) HDD
if that's what you are asking. If there is any other BIOS setting you want me to post here, please let me know. 

Thank you for taking time to help.

---

### Post by BIGCJ on 2010-05-22
No it should be under [FONT=Tahoma, Arial, Helvetica][SIZE=2]standard CMOS features.
Also have you tried installing Ubuntu in windows?

[/SIZE][/FONT]

---

### Post by dministrator on 2010-05-22
No, I haven't tried to install Ubuntu with Windows yet. 

I will restart my machine right now and will find out whatever I can from standard CMOS feature in BIOS settings. I will post my findings in the next few minutes. Thank you again.

---

### Post by dministrator on 2010-05-22
Here's the info from my BIOS Settings:

Standard CMOS
IDE Primary Master: OEM CD-ROM F563E
IDE Primary Slave: IC35L060AVV207-0
IDE Secondary Master: None
IDE Secondary Slave: None
Drive A: None
Drive B: None
Video: EGA/VGA
Halt On: All but Keyboard
-----
Advanced BIOS
Virus Warning: Disabled
CPU L1 & L2 Cache: Enabled
CPU L2 Cache ECC Checking: Enabled
Quick Power On Self Test: Enabled
First Boot Device: CD-ROM
Second Boot Device: HDD-0
Third Boot Device: HDD-0
Boot Other Device: Enabled
Swap Floppy Drive: Disabled
Boot-up Floppy Seek: Enabled
Boot-up NumLock Status: On
Typematic Rate Setting: Disabled
x Typematic Rate (Chars/sec): 6
x Typematic Delay (Msec): 250
Security Option: Setup
OS Select for DRAM > 64MB: Non-OS2
Video BIOS Shadow: Enabled

---

### Post by BIGCJ on 2010-05-22
Do you have the CD drive on the same cable as the hard drive?
Move the CD drive to the secondary IDE port. and leave the hard drive on the primary.
Make sure to move it to the first connector also move the jumper on the hard drive to the master position.

---

