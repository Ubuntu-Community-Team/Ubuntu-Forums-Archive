---
title: "Installing *buntu in Abit Abit Fatal1ty F-I90HD"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by pinoytechie on 2008-07-29
How can I ever install Ubuntu 8 in a PC with this motherboard?

I tried Ubuntu, Kubuntu, Xubuntu and event LinuxMint Elyssa LiveCDs but none would boot. All of them stopped loading with this last lines of log:

> io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)

I tried switching AHCI, IDE, Legacy in SATA config with no success.

System:
- Intel E2160
- 2GIG RAM
- SATA DVD Drive
- 160GB SATA HDD (WD)

This motherboard is using ATI® Radeon Xpress 1250

Motherboard [specs]("http://www.uabit.com/index.php?option=com_content&task=view&id=32&Itemid=48&page=1&model=339")

Note: System works flawlessly with Vista and XP. Even tried an old LinuxMint Cassandra and Ubuntu Edgy LiveCDs and they booted fine.

---

### Post by pinoytechie on 2008-07-29
up... help

---

### Post by pinoytechie on 2008-07-29
:confused:

---

### Post by pinoytechie on 2008-07-30
???

---

### Post by pinoytechie on 2008-07-30
????

---

### Post by pinoytechie on 2008-07-30
*ehem*

---

### Post by pinoytechie on 2008-07-31
helppppppppppppppp!

---

### Post by Dynamo_Joe on 2008-08-01
Hi pinoytechie, 

Not sure if the following suggestion are of use or not as there doesn't seen to be too much information provided with your original post. 

1. Boot from the liveCD and see if all your hardware is recognized. 

2. If you are having issues with installing onto the hard drive, you could: 
a) remove all SATA drives and install to one single (connected) IDE drive. 
b) remove all IDE drives and install to one single SATA drive. 

There is an issue (don't know whether it has been resolved yet) where Hardy hicups on computers with mixed combination of SATA and IDE drives. 

For your information, when I did my installation, I disconnected all my data drives and left one (IDE) drive connected for the installation. 

Once the installation completed, I then re-attach the drives and Hardy automatically recognized them. If you want the data drives to be recognized at boot time, you'll need to edit the fstab file. 

3. If you get a garbled screen when Hardy loads, reboot and press "F4" and select "Safe graphics mode". 

If none of the above works, then you maybe just unlucky and have a non-compatible MB. 

4. If you still want to persist with installing Hardy, then "Google" is you best friend. 

Take care now.

---

### Post by MTisza on 2008-12-27
I realize this might be too late for you, but in case anyone else searches for this...

When booting from the install CD and you get the menu to choose to boot to the live CD or install, Press F6 and add this kernel boot option:

clocksource=acpi_pm

This worked for me.

---

### Post by ppine on 2011-12-15
Maybe late for some, just in time for me. This got it working, thanks alot!

 * well, it does boot but its slooooooowww :(

---

