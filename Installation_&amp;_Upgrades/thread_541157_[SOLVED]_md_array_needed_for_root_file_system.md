---
title: "[SOLVED] md array needed for root file system"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by shortybookit on 2007-09-02
I'm currently in the process of upgrading from Edgy to Feisty.
A window has just come up asking for "MD arrays needed for the root filesystem", and "all" is already entered into the box, but I have no idea what this is or what I should do.
The mouseover info says something about entering the arrays needed to start the root filesystem when I start up my computer, but I don't have any idea what I'm supposed to answer.
Should I just leave the default "all" answer?
after reading through some other posts i guess it depends on  your computer so here is what my pc has

Operating System
Windows XP Home Edition Service Pack 2 (build 2600

Processor
2.80 gigahertz Intel Celeron
16 kilobyte primary memory cache
256 kilobyte secondary memory cache


Drives
80.02 Gigabytes Usable Hard Drive Capacity
63.33 Gigabytes Hard Drive Free Space

PIONEER DVD-RW DVR-109 [CD-ROM drive]

WDC WD800BB-22JHC0 [Hard drive] (80.03 GB) -- drive 0, s/n WD-WMAM98974491, rev 05.01C05, SMART Status: Healthy


Controllers
Standard floppy disk controller
Intel(R) 82801EB Ultra ATA Storage Controllers (2x)
Primary IDE Channel [Controller] (2x)
Secondary IDE Channel [Controller] (2x)

Bus Adapters
Intel(R) 82801EB USB Universal Host Controller - 24D2
Intel(R) 82801EB USB Universal Host Controller - 24D4
Intel(R) 82801EB USB Universal Host Controller - 24D7
Intel(R) 82801EB USB Universal Host Controller - 24DE
Intel(R) 82801EB USB2 Enhanced Host Controller - 24DD

Communications
SoftV92 Data Fax Modem with SmartCP
Intel(R) PRO/100 VE Network Connection

Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
Microsoft PS/2 Mouse
USB Root Hub (5x)
SoundMAX Integrated Digital Audio
Intel(R) 82865G Graphics Controller [Display adapter]
Gateway 15.7 [Monitor] (15.7"vis, s/n MRK5750001002, July 2006)


240 Megabytes Installed Memory

Slot 'J6G1' has 256 MB (serial number F308955B)

---

### Post by shortybookit on 2007-09-02
THIS IS THE EXACT MSG 

if your system has its root filesystem on an MD array (raid), it needs to be started early during the boot sequence. if your root filesystem is on a logical volume(lvm) which is on md all constituent arrays need to be started

if you know exactly which arrays are needed to bring up the root filesystem and you want to postpone starting all other arrays to a later poing in the boot sequence enter the to start here alternatively enter all to simply start all availible arrays 

if you do not need or want to start any arrays for the root filesystem, leave the answer blank or enter none this may be the case if you are using kernel autostart or do not need any arrays to boot

please enter a space separated list of devices all or none 
you may omit the leading /dev/ and just enter e.g. md0 ,md1 or md1/1 md/d0

---

### Post by shortybookit on 2007-09-02
any one?

---

### Post by yota on 2007-09-02
Hi,
I can understand you have only one hard drive, and this implies that you are not using any raid/md array (md stands for Multiple Devices virtual disk).

as the message says:
> 
if you do not need or want to start any arrays for the root filesystem, leave the answer blank or enter none this may be the case if you are using kernel autostart or do not need any arrays to boot


you can leave the default, but also "none" would work fine since this is a setting about something you're not using.

Hope this helps!

---

### Post by shortybookit on 2007-09-03
thank you

---

