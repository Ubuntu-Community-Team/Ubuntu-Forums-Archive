---
title: "Hangs during 10.04 LTS bootup"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by cci[RR]us on 2010-05-08
I downloaded the x86 10.04 LTS ISO and burned to a disc. I booted it on my old Fujitsu laptop but it just hangs at:
```

Begin: Running /scripts/init-bottom ...
Done.
init: ureadahead-other main process (1019) terminated with status 4
init: ureadahead-other main process (1020) terminated with status 4
* Setting sensors limits                                           [ OK ]

```
I tried all the possibilities like noacpi but to no avail. Please help. :(

Thank you.

---

### Post by cci[RR]us on 2010-05-08
I verified the installation disc is working. No I/O errors.

How should I proceed next? Any way to get to the logs where I could troubleshoot the problem?

---

### Post by cci[RR]us on 2010-05-08
How should I troubleshoot this problem? Please help!

---

### Post by paydaydaddy on 2010-05-08
Have you tried recovery? Safe graphics mode? Earlier Kernel?

---

### Post by cci[RR]us on 2010-05-09
> **paydaydaddy said:**
> Have you tried recovery? Safe graphics mode? Earlier Kernel?
I don't see these options in the boot menu of 10.04 LTS. May I know how do I activate recovery, safe graphics or earlier kernel?

I'm using Windows 7 right now on that problematic laptop.

---

### Post by ronparent on 2010-05-09
Have you tried editing the grub boot line to eliminate **quiet splash**?

---

### Post by cci[RR]us on 2010-05-09
> **ronparent said:**
> Have you tried editing the grub boot line to eliminate **quiet splash**?
Yes, that is how I managed to get the error output as shown in the first post. Else, I'd be left with a hanged PC at the splash screen.

---

### Post by cci[RR]us on 2010-05-09
cat /dev/cpuinfo
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Pentium(R) M processor 1.70GHz
stepping	: 6
cpu MHz		: 212.500
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2
bogomips	: 3402.08
```

lspci
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
01:0a.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 20)
01:0a.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 20)
01:0c.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
01:0d.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)

```

Is my hardware supported? I gotten these output from Knoppix 5.1.1 LiveCD.

---

### Post by eye12b12 on 2010-05-09
There seems to be an issue with the intel 82852/855GM video device and the ver 32 kernel.  I am knee deep in similar problem and trying to find out how to change kernels and or revert back to karmic or jaunty. 
If you are interested:

[http://ubuntuforums.org/showthread.php?t=1470685](http://ubuntuforums.org/showthread.php?t=1470685)

hope it is useful to you

---

### Post by Catharsis on 2010-05-09
There is a known issue with Lucid and i855 cards. See:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by cci[RR]us on 2010-05-09
> **eye12b12 said:**
> There seems to be an issue with the intel 82852/855GM video device and the ver 32 kernel.  I am knee deep in similar problem and trying to find out how to change kernels and or revert back to karmic or jaunty. 
If you are interested:

[http://ubuntuforums.org/showthread.php?t=1470685](http://ubuntuforums.org/showthread.php?t=1470685)

hope it is useful to you

> **Catharsis said:**
> There is a known issue with Lucid and i855 cards. See:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
Oh!!! Thanks Catharsis and eye12b12!

I'll try the two links later. Really appreciate your help!

---

### Post by cci[RR]us on 2010-05-10
Great! After adding "i915.modeset=1", I could install as well as boot into Lucid! Thanks guys for your wonderful help!

---

### Post by axel_2078 on 2010-05-10
> **'cci[RR]us said:**
> Great! After adding "i915.modeset=1", I could install as well as boot into Lucid! Thanks guys for your wonderful help!

I'm glad this worked for you. I'm having the same problem, but I don't have an intel chipset. My video chipset is ATI Mobility 9000.

---

### Post by rykel on 2010-08-25
I just installed Karmic on a Dell 710m (non-NVIDIA card) and everything was working fine. Then I upgraded it to Lucid, and now the system hangs with a blank screen after bootup.

I searched around the forums and realised that this might be a "modeset" problem - a problem which an end user will not know how to solve!

With such problems, I believe Ubuntu is regressing and NOT ready for prime time anymore. What should work with previous PCs should not be meddled with. Maybe it is time for us to look at another distro... disappointed.

---

