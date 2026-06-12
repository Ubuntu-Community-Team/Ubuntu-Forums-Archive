---
title: "System hang at installation language selection"
date: 2012-12-14
forum: Installation &amp; Upgrades
---

### Post by comraid on 2012-12-14
[LIST=1]
[*]Hello all:p
 
I am having trouble installing Ubuntu 12.04, the whole  computer hangs after I press 'Next' in the language screen or 'Install  Ubuntu' on the welcome screen. I have searched a whole bunch of threads  and forums but I can't seem to find a fix. This exact problem is also  present in Linux Mint 13 MATE/14 MATE and Cinnamon. Here is what I have  tried so far:
 
I have tried Mint 13 MATE, Mint 14 MATE/Cin and Ubuntu 12.04 LTS. All the same.
Putting in a graphics card in case it was a problem with the on-board.
Swapping the RAM in and out to make sure that isn't faulty.
With networking enabled and networking disabled.
Swapping out mouse and keyboard (apparently there is a problem with some logitech keyboards and mice)
Tried with nomodeset, noapic, nolapic and compatibility mode.
I have also tried removing the slide-show as is recommended by many users (recommended by Mint users).
I have removed all partitions except for one, so the whole drive is one partition.

If someone could please help me it would be much appreciated:(

Here is the  my hardware:

Machine:   Mobo: Intel model: DQ35JO version: AAD82085-701
           Bios: Intel version: JOQ3510J.86A.0693.2007.0919.2156 date: 09/19/2007
CPU:        Single core Intel Core2 CPU 4400 (-UP-) cache: 2048 KB flags: (lm  nx sse sse2 sse3 ssse3) bmips: 3989.82 clocked at 1200.00 MHz 
Graphics:  Card: Intel 82Q35 Express Integrated Graphics Controller bus-ID: 00:02.0 
           Audio:     Card: Intel 82801I (ICH9 Family) HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 Sound: ALSA ver: 1.0.24
Network:   Card: Intel 82566DM-2 Gigabit Network Connection driver: e1000e ver: 1.5.1-k port: 20e0 bus-ID: 00:19.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 80.0GB (-) 1: /dev/sda WDC_WD800AAJS 80.0GB 41C
[/LIST]

---

### Post by mastablasta on 2012-12-14
did you check the md5sum of the downloaded image file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
hardware doesn't seem problematic and is supported.
 
unless there is some hardware fault.

---

### Post by comraid on 2012-12-15
Hi mastablasta, I have checked the md5sums of all four disks I have tried, they all check out. 

Is there anything else I could try? The live CDs work perfectly, I was thinking a text-based installer but I am likely to run into problems once the system is up and running am I not? What kind of hardware fault could it be? Is there anyway to check? Thank you for helping me.

---

### Post by comraid on 2012-12-18
Hello again, this morning I tried installing crunchbang 10 and the graphical install worked perfectly through the language selection all the way up to 'Detect disks' screen where I experienced the exact same system hang as with Mint/Ubuntu. This must point towards the hard drive being faulty correct? Does Ubuntu run this disk detection after the language selection? I will be trying a different hard drive as soon as I can but I don't have any spares on-hand. Thanks for all the help so far.

---

