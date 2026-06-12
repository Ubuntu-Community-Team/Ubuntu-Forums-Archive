---
title: "Edgy: Starting up...blank screen and no activity or response"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by akijikan on 2006-11-01
So after I finially got Edgy installed with no errors, I reboot into my new OS.

It says "Starting up..." in the upper right corner, and then that goes away and I'm left with nothing, a blank screen.  No words, No command line, no nothing.  Well almost, did notice that there is harddrive activity for about the first 10 seconds but after that no more.

Any suggestions are appreciated!

---

### Post by akijikan on 2006-11-01
bump

---

### Post by bigroot on 2006-12-05
Got same problem : 

my notebook : 
Aopen, Centrino 1,5 Ghz
1Gb SRAM
ATI Radeon 9600 Pro (64Mb)



c'mon, can't be that hard....

---

### Post by wpshooter on 2006-12-05
Did you check the integrity of the CD before installing by running the verification test found on the initial Ubuntu boot screen menu ?

Are you installing from DESKTOP CD or from ALTERNATE CD ?

If from DESKTOP CD did you try installing with safe video mode ?

Consider installing from the ALTERNATE CD.

Are you installing just Ubuntu on the system or does it already have another O/S installed ?

---

### Post by ziomente on 2006-12-06
Same problem here, I dist-upgraded from Dapper and as system finishes loading and starts X, the screen goes black, hard-drive shows short and frequent activity, and even by hitting ctrl+alt+Fn I can't get a CLI to log-in (So I can't even look at xorg.conf or xorg logs)
Not to mention that boot takes so damn long, but this was the same with Dapper too.
Reinstalling from scratch will be of any help or that won't be working anyway?

--

config: Asus M6va
Intel Pentium M D750
2*512 MB DDR2
Ati X800 Mobility

---

### Post by Johnsie on 2006-12-06
I have the same problem. anyone fixed it yet?

---

### Post by eye208 on 2006-12-06
On certain laptops with ATI graphics, you need to add the line

**Option "MonitorLayout" "LVDS"**

to the "Device" section of /etc/X11/xorg.conf. Otherwise the panel's backlight will be turned off when X is started.

Boot into recovery mode, then use nano or vi to edit xorg.conf.

---

### Post by Sebastral on 2006-12-09
Same thing with matrox P750 videocard. After way too much time and pressing enter a few times I get the loginmanager and I can enter the system.
I noticed this in dmesg;
> [17179573.156000] Boot video device is 0000:02:00.0
[17179573.156000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.232000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179573.232000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179573.232000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[17179573.232000] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[17179573.232000] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.232000] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.236000] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.236000] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.236000] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.236000] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.236000] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.236000] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[17179573.236000] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.236000] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.236000] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.236000] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.240000] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.240000] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.240000] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[17179573.240000] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[17179573.240000] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[17179573.240000] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
[17179573.240000] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[17179573.240000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
[17179573.240000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
[17179573.240000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
[17179573.244000] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[17179573.244000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[17179573.244000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[17179573.244000] ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
[17179573.244000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
[17179573.244000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[17179573.244000] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[17179573.244000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[17179573.248000] Linux Plug and Play Support v0.97 (c) Adam Belay

Didn't have the problem with 6.06.

edit; the backlight isn't turned off btw, its just shines blackness.

---

### Post by viz_e on 2006-12-09
same here. it happened after last upgrade... The 
Option "MonitorLayout" "LVDS" trick does not work in my Thinkpad T42 (ati card).

---

### Post by viz_e on 2006-12-09
Kubuntu boots only with the vesa driver. Any idea why? ](*,) ](*,) I am missing a whole day where I should work... :evil: :evil:


Edit: for no apparent reasons now the ati driver works as well... My goal is to get radeon to work...

---

### Post by pombrbom on 2006-12-09
Have the same problem/blanc screen/when instaling 64-bit Edgy.Then I installed  32-bit sistem and everythig is OK.Could somebody tell me why I can not istall 64-bit sistem?/Cpu Pentium 805,Asus P5VD2-MX,NVIDIA GeForce 7300GS,512 Kingston DDR2 ram,Western Digital 200 gig hard disc/

---

### Post by Sebastral on 2006-12-12
Installed [SUM](http://ubuntuforums.org/showthread.php?t=295524&highlight=start+manager), defined correct screen resolution and it boots normally again.

---

