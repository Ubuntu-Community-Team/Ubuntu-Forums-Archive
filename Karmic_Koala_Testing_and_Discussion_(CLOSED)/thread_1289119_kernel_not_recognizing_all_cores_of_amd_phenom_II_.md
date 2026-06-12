---
title: "kernel not recognizing all cores of amd phenom II x4 965"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sgb on 2009-10-12
Recently changed motherboard and cpu to
gigabyte ga-ma790xt-ud4p and amd phenom II x4 965.

Sometimes (and I mean sometimes) ubuntu 9.04 does not recognize
all cpu cores, but 1 (sometimes :) even 2 or 3).
I have tried Karmic(9.10), and at first it recognized all cores, but now it
is back to normal (random not recognizing).

I have tried various Live distros: ubuntu 8.10, suse 11.1, suse 11.2alpha,
xubuntu, ...
Not rule, but older distros tend to be more accurate then newer in guessing CPU.
Found somewhere thread with suggestion to include pci=nommconf in grub kernel
boot line, and yes, it helps in a relative way (more good boots than before)
Tried different bios versions, without success.
some wierd things:
* dmi decode utility in 9.10 say it is 3.2GHz cpu, while it is 3.4GHz.
* windows xp missed number of cores before bios update to f6, and now
it never misses.
* if windows xp is booted and restarted to ubuntu, mb either locks up or
boots ubuntu 9.10 with all 4 cores
* every time on power-up there is a message: upadting DMI data - success
from bios.
* with one core up, it temperature rise quickly and fan spins up to 4500rpm soon, but with all four temp is well bellow 40 and fan is at 2200rpm (all on idle system)

here are dmesg excepts when it's good and bad:
GOOD:
[    0.004120] CPU: Physical Processor ID: 0
[    0.004121] CPU: Processor Core ID: 0
[    0.004122] using C1E aware idle routine
[    0.005127] ACPI: Core revision 20080926
[    0.007096] ACPI: Checking initramfs for custom DSDT
[    0.176040] Setting APIC routing to flat
[    0.180270] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.219961] CPU0: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.220001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6848.45 BogoMIPS (lpj=13696915)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.304596] CPU1: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.304601] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.308023] System has AMD C1E enabled
[    0.308027] Switch to broadcast mode on CPU1
[    0.308055] Booting processor 2 APIC 0x2 ip 0x6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 6848.45 BogoMIPS (lpj=13696906)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.396564] CPU2: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.396569] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.400026] Switch to broadcast mode on CPU2
[    0.400057] Booting processor 3 APIC 0x3 ip 0x6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 6848.46 BogoMIPS (lpj=13696926)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.488595] CPU3: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.488599] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.492033] Brought up 4 CPUs
[    0.492035] Total of 4 processors activated (27393.11 BogoMIPS).

BAD:
[    0.005750] CPU: Physical Processor ID: 0
[    0.005751] CPU: Processor Core ID: 0
[    0.005752] using C1E aware idle routine
[    0.005753] Performance Counters: AMD PMU driver.
[    0.005756] ... version:                 0
[    0.005757] ... bit width:               48
[    0.005758] ... generic counters:        4
[    0.005759] ... value mask:              0000ffffffffffff
[    0.005760] ... max period:              00007fffffffffff
[    0.005761] ... fixed-purpose counters:  0
[    0.005762] ... counter mask:            000000000000000f
[    0.006793] ACPI: Core revision 20090521
[    0.016051] Setting APIC routing to flat
[    0.016520] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.056446] CPU0: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.060001] Booting processor 1 APIC 0x1 ip 0x6000
[    5.199753] Not responding.
[    5.199904] Booting processor 2 APIC 0x2 ip 0x6000
[   10.342708] Not responding.
[   10.342818] Booting processor 3 APIC 0x3 ip 0x6000
[   15.485575] Not responding.
[   15.485632] Brought up 1 CPUs
[   15.485634] Total of 1 processors activated (6847.87 BogoMIPS).

Does anyone has this hw combination and similar problems?


m/b gigabyte ga-ma790xt-ud4p
cpu amd phenom II x4 965.

---

### Post by 3rdalbum on 2009-10-13
Google has some stuff to say about this problem, but not a lot to say :-(

Try the following Bash script when it's not working properly:

```

#!/bin/sh
for i in cpu1 cpu2 cpu3; do echo 0 >/sys/devices/system/cpu/$i/online; done
for i in cpu1 cpu2 cpu3; do echo 1 >/sys/devices/system/cpu/$i/online; done

```

Needs to be run as root.

See if that brings up your cores.

I have also read something about adding the "noapic" parameter to the kernel line in the GRUB boot menu, and removing the "splash" parameter.

---

### Post by tymek666 on 2009-10-13
So this could be energy-saving related issue?

---

### Post by sgb on 2009-10-14
First:
/sys/devices/system/cpu0
is only cpu0 interface visible when only one core is recognized, so I can't activate others. 
I did not know anything about this way of cpu control, but I'm reading now :).
If there is a way to reinitiate cpu booting, that would do the trick.
When all cores start working, one can turn all cores but core 0 on/off. I am not
sure if this is saving energy or anything alike, since remaining core heats up rapidly,
causing cpu fan to go wild.

There is a gigabyte power saving utility running on windoze, reducing frequency and
voltage to CPU, and (claiming at least) lowering CPU power to 10W. But I failed to
see any correlation with rebooting from windows to linux with this power saving
activated or deactivated.
Only relevant is notice is that ubuntu 9.04 manages to see all cores
almost every second boot, and 9.10 roughly once in five boots.

Anyway, too much random behavior for a digital machine.

---

### Post by lensman3 on 2009-10-15
What does "more /proc/cpu*"  from  a command line say".  This file lists the cores that the kernel sees.

---

### Post by sgb on 2009-10-16
Thanks everyone,
I have resolved the issue.
Unbelievable as it is: four port USB hub was responsible
for this random behavior. As soon as it is removed,
everything is working as it should.
I am amazed...
But it's working now. :)
If anyone has any theory how windows bypassed it,
and why linux *sometimes* did, and sometimes did not,
I would really like to hear... :confused:
Thanks again for Your effort.

---

### Post by sanderj on 2009-10-17
> **sgb said:**
> Thanks everyone,
I have resolved the issue.
Unbelievable as it is: four port USB hub was responsible
for this random behavior. As soon as it is removed,
everything is working as it should.
I am amazed...
But it's working now. :)
If anyone has any theory how windows bypassed it,
and why linux *sometimes* did, and sometimes did not,
I would really like to hear... :confused:
Thanks again for Your effort.

If you can reproduce it, please file a bug report on [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by TheJPK on 2009-10-17
sgb, thanks for your hint with the USB. I tried all hints I found in the net. And nothing helped. I got one of ten boots with all of my four cores. Sometimes it even hung.

But I did not need to remove a usb hub, I disabled "Highspeed usb" inside the BIOS and the system came up with no problems. Could you might test what happens when you attach the hub and only using usb 1.1?

Here some information about my system:

CPU: AMD Phenom(tm) 9650
Board is a Shuttle SN78SH7 with latest BIOS.
uname -a: Linux xxx 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

Before I tried Ubuntu 8.04.3 LTS, Ubuntu 9.04, Fedora 11, everywhere the same.

---

### Post by sgb on 2009-10-17
@sanderj: If that would help, I will. But this seems to be related to faulty USB hub..., it is reproducible, but only with same hub, not with other one I tried with.

@TheJPK: I am very glad that this was not a complete waste of time, and that it helped someone also.
About  usb 1.1, I am not sure how to do it in bios. I have two options related to usb:
OnChip USB controller [enable/disable] and
USB EHCI Controller [enable/disable]
plus (unrelated?) usb keyboard/mouse/legacy storage which should
help with MS-DOS using usb keyboard and usb-hdd as I recall.
If You can direct me to what to do, I am willing to try.
BTW, USB hub in question is external one with separate power supply, and if power is disconnected
from it, it is not even detected. (this is normal for this one, at least has been since I bought it).
It works ok on my laptop, and older amd dual core system.
Other hub I tried has an option of external supply, but works without it. That one does not cause any
trouble. Unfortunately I do not have PSU for that one, and can not try with it.

---

### Post by TheJPK on 2009-10-18
When I'm right, then disable USB EHCI Controller, should do the trick.

But strange that the problem only exist, when you attach the one hub. Are there differences between both? Like 1.1 and 2.0 USB?

I'm currently trying to get my box to boot with the faulty BIOS config.

---

### Post by soohrt on 2009-10-18
I'm having the same problem with a SN78SH7. Linux will only detect one of four cores if I attach a USB Bluetooth receiver even if I disable USB2.0 in the BIOS.

dmesg diffs between booting while the BT receiver is connected and connecting it after a successful boot
```
--- /nfsroot/a  2009-10-18 14:36:43.000000000 +0200
+++ /nfsroot/b  2009-10-18 14:37:48.000000000 +0200
@@ -163,16 +163,14 @@
 Checking if this processor honours the WP bit even in supervisor mode...Ok.
 NR_IRQS:2304 nr_irqs:440
 CPU 0 irqstacks, hard=c1936000 soft=c1937000
-Fast TSC calibration failed
-TSC: Unable to calibrate against PIT
-TSC: using PMTIMER reference calibration
-Detected 2999.951 MHz processor.
+Fast TSC calibration using PIT
+Detected 3000.319 MHz processor.
 spurious 8259A interrupt: IRQ7.
 Console: colour VGA+ 80x25
 console [tty0] enabled
 hpet clockevent registered
 HPET: 3 timers in total, 0 timers will be used for per-cpu timer
-Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.90 BogoMIPS (lpj=2999951)
+Calibrating delay loop (skipped), value calculated using timer frequency.. 6000.63 BogoMIPS (lpj=3000319)
 Mount-cache hash table entries: 512
 CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
 CPU: L2 Cache: 512K (64 bytes/line)
@@ -186,22 +184,46 @@
 CPU0: AMD Phenom(tm) II X4 940 Processor stepping 02
 CPU 1 irqstacks, hard=c1946000 soft=c1947000
 Booting processor 1 APIC 0x1 ip 0x6000
-Not responding.
-Unmapping cpu 1 from all nodes
+Initializing CPU#1
+Mapping cpu 1 to node 0
+Calibrating delay using timer specific routine.. 5999.97 BogoMIPS (lpj=2999986)
+CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
+CPU: L2 Cache: 512K (64 bytes/line)
+CPU: Physical Processor ID: 0
+CPU: Processor Core ID: 1
+x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
+CPU1: AMD Phenom(tm) II X4 940 Processor stepping 02
+checking TSC synchronization [CPU#0 -> CPU#1]: passed.
 CPU 2 irqstacks, hard=c1956000 soft=c1957000
 Booting processor 2 APIC 0x2 ip 0x6000
-Not responding.
-Unmapping cpu 2 from all nodes
+Initializing CPU#2
+Mapping cpu 2 to node 0
+Calibrating delay using timer specific routine.. 5999.97 BogoMIPS (lpj=2999988)
+CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
+CPU: L2 Cache: 512K (64 bytes/line)
+CPU: Physical Processor ID: 0
+CPU: Processor Core ID: 3
+x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106
+CPU2: AMD Phenom(tm) II X4 940 Processor stepping 02
+checking TSC synchronization [CPU#0 -> CPU#2]: passed.
 CPU 3 irqstacks, hard=c1966000 soft=c1967000
 Booting processor 3 APIC 0x3 ip 0x6000
-Not responding.
-Unmapping cpu 3 from all nodes
-Brought up 1 CPUs
-Total of 1 processors activated (5999.90 BogoMIPS).
+Initializing CPU#3
+Mapping cpu 3 to node 0
+Calibrating delay using timer specific routine.. 5999.97 BogoMIPS (lpj=2999987)
+CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
+CPU: L2 Cache: 512K (64 bytes/line)
+CPU: Physical Processor ID: 0
+CPU: Processor Core ID: 2
+x86 PAT enabled: cpu 3, old 0x7040600070406, new 0x7010600070106
+CPU3: AMD Phenom(tm) II X4 940 Processor stepping 02
+checking TSC synchronization [CPU#0 -> CPU#3]: passed.
+Brought up 4 CPUs
+Total of 4 processors activated (24000.56 BogoMIPS).
 Booting paravirtualized kernel on bare hardware
 xor: automatically using best checksumming function: pIII_sse
-   pIII_sse  : 12032.000 MB/sec
-xor: using function: pIII_sse (12032.000 MB/sec)
+   pIII_sse  : 12060.000 MB/sec
+xor: using function: pIII_sse (12060.000 MB/sec)
 NET: Registered protocol family 16
 ACPI: bus type pci registered
 PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
@@ -387,23 +409,26 @@
 usbcore: registered new interface driver usbfs
 usbcore: registered new interface driver hub
 usbcore: registered new device driver usb
-raid6: int32x1   1160 MB/s
-raid6: int32x2   1019 MB/s
-raid6: int32x4    656 MB/s
-raid6: int32x8    738 MB/s
-raid6: mmxx1     2148 MB/s
-raid6: mmxx2     4234 MB/s
-raid6: sse1x1    1300 MB/s
-raid6: sse1x2    2269 MB/s
-raid6: sse2x1    2285 MB/s
-raid6: sse2x2    3472 MB/s
-raid6: using algorithm sse2x2 (3472 MB/s)
+raid6: int32x1   1355 MB/s
+raid6: int32x2   1214 MB/s
+raid6: int32x4    781 MB/s
+raid6: int32x8    878 MB/s
+raid6: mmxx1     2457 MB/s
+raid6: mmxx2     4742 MB/s
+raid6: sse1x1    2109 MB/s
+raid6: sse1x2    3542 MB/s
+raid6: sse2x1    4031 MB/s
+raid6: sse2x2    6882 MB/s
+raid6: using algorithm sse2x2 (6882 MB/s)
 PCI: Using ACPI for IRQ routing
 hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
 hpet0: 3 comparators, 32-bit 25.000000 MHz counter
+Switched to high resolution mode on CPU 0
+Switched to high resolution mode on CPU 1
+Switched to high resolution mode on CPU 2
+Switched to high resolution mode on CPU 3
 pnp: PnP ACPI init
 ACPI: bus type pnp registered
-Switched to high resolution mode on CPU 0
 pnp: PnP ACPI: found 10 devices
 ACPI: ACPI bus type pnp unregistered
 system 00:01: ioport range 0x1000-0x107f has been reserved
@@ -518,6 +543,9 @@
 pcieport-driver 0000:00:12.0: irq 25 for MSI/MSI-X
 pcieport-driver 0000:00:12.0: setting latency timer to 64
 processor LNXCPU:00: registered as cooling_device0
+processor LNXCPU:01: registered as cooling_device1
+processor LNXCPU:02: registered as cooling_device2
+processor LNXCPU:03: registered as cooling_device3
 ACPI Warning: \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference 20090521 nspredef-946
 ACPI: Expecting a [Reference] package element, found type 0
 ACPI: Invalid passive threshold
@@ -606,11 +634,11 @@
   alloc kstat_irqs on node 0
 forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
 forcedeth 0000:00:0a.0: setting latency timer to 64
+ata1: SATA link down (SStatus 0 SControl 300)
+ata4: SATA link down (SStatus 0 SControl 300)
 ata6: SATA link down (SStatus 0 SControl 300)
-ata3: SATA link down (SStatus 0 SControl 300)
 ata5: SATA link down (SStatus 0 SControl 300)
-ata4: SATA link down (SStatus 0 SControl 300)
-ata1: SATA link down (SStatus 0 SControl 300)
+ata3: SATA link down (SStatus 0 SControl 300)
 ata2: SATA link down (SStatus 0 SControl 300)
 ata8: port disabled. ignoring.
 forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x5043 @ 19, addr 00:30:1b:47:c4:31
@@ -691,7 +719,6 @@
 ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver
 PNP: No PS/2 controller found. Probing ports directly.
 serio: i8042 KBD port at 0x60,0x64 irq 1
-serio: i8042 AUX port at 0x60,0x64 irq 12
 it87: Found IT8716F chip at 0x290, revision 3
 it87: in3 is VCC (+5V)
 it87: in7 is VCCH (+5V Stand-By)
@@ -747,7 +774,7 @@
 RPC: Registered tcp transport module.
 802.1Q VLAN Support v1.8 Ben Greear <greearb@candelatech.com>
 All bugs added by David S. Miller <davem@redhat.com>
-powernow-k8: Found 1 AMD Phenom(tm) II X4 940 Processor processors (1 cpu cores) (version 2.20.00)
+powernow-k8: Found 1 AMD Phenom(tm) II X4 940 Processor processors (4 cpu cores) (version 2.20.00)
 powernow-k8:    0 : pstate 0 (3000 MHz)
 powernow-k8:    1 : pstate 1 (2300 MHz)
 powernow-k8:    2 : pstate 2 (1800 MHz)
@@ -762,9 +789,9 @@
 md: autorun ...
 md: ... autorun DONE.
 RAMDISK: gzip image found at block 0
-usb 4-1: new full speed USB device using ohci_hcd and address 2
 VFS: Mounted root (ext2 filesystem) readonly on device 1:0.
 Freeing unused kernel memory: 452k freed
+usb 4-1: new full speed USB device using ohci_hcd and address 2
 usb 4-1: configuration #1 chosen from 1 choice
 hub 4-1:1.0: USB hub found
 hub 4-1:1.0: 3 ports detected

```

---

### Post by TheJPK on 2009-10-18
Hi soohrt, Try the following inside the BIOS:

enable "USB 2.0 Controller"  but set "USB Operation Mode" to "Full/Low Speed".

I think my issue is that I have a DVI-USB-KVM attached to the system.

[Update] 
When i have High Speed USB enabled and removing the KVM and have only a keyboard attached via USB, the system boots up, finding all cores.

Looks like the Fast TSC calibration is the problem

attached my dmesgs
[/Update]

---

### Post by soohrt on 2009-10-18
> **TheJPK said:**
> Hi soohrt, Try the following inside the BIOS:

enable "USB 2.0 Controller"  but set "USB Operation Mode" to "Full/Low Speed".

I think my issue is that I have a DVI-USB-KVM attached to the system.

I have tried all combinations and unfortunately none works.

---

### Post by TheJPK on 2009-10-18
> **soohrt said:**
> I have tried all combinations and unfortunately none works.

That's strange. Just to be sure that you using the latest BIOS? I will try to open a bug report.

---

### Post by rtalcott on 2009-10-18
I have this problem or something like it...Jaunty recognized the cores but not Karmic..
[https://bugs.launchpad.net/bugs/401374](https://bugs.launchpad.net/bugs/401374)
rt

---

### Post by soohrt on 2009-10-18
> **TheJPK said:**
> That's strange. Just to be sure that you using the latest BIOS? I will try to open a bug report.

Yes, I'm using BIOS version SN78S10Y.

The hardware is a stock SN78SH7 with a Phenom 2 X4 940, 2G ram and a Logitech diNovo Bluetooth USB stick.

I've tried all possible USB BIOS settings and all USB ports and I've even disconnected the front USB ports to no avail.
A regular USB mouse and a regular USB keyboard seem to work but as soon as the BT stick is connected, it won't boot with all 4 cores.

---

### Post by TheJPK on 2009-10-18
> **rtalcott said:**
> I have this problem or something like it...Jaunty recognized the cores but not Karmic..
[https://bugs.launchpad.net/bugs/401374](https://bugs.launchpad.net/bugs/401374)
rt

I'm not sure. Before I found out that setting the USB Speed to "Low/Full" helps I tried some other versions and Distris and all didn't like to boot correct.

amd64:
8.04.3 LTS
9.04
9.10
Fedora 11

i386:
9.10
9.04

---

### Post by rtalcott on 2009-10-18
I need to get back to this...I installed a single core Athlon in the machine...I need to go back to a multi-core chip and see if I can get it to work.  When I had the X2 in there I could boot the live Jaunty cd and see 2 cores..
rt

---

### Post by sgb on 2009-10-18
I have tried all BIOS USB options,
and there is no difference, if faulty (or not?) HUB is connected, cores are not recognized.
The only difference is when USB is turned OFF in BIOS.

Added new PCI USB card today, based on VIA chip (3+1 USB kind),
since I need extra usb ports, and works with no problem.

I tried OpenSuSE 11.2 milestone8 -- same

Again, for some reason windows xp always booted 4 cores.(!??)

---

### Post by TheJPK on 2009-10-19
> **sgb said:**
> I have tried all BIOS USB options,
and there is no difference, if faulty (or not?) HUB is connected, cores are not recognized.
The only difference is when USB is turned OFF in BIOS.

Added new PCI USB card today, based on VIA chip (3+1 USB kind),
since I need extra usb ports, and works with no problem.

I tried OpenSuSE 11.2 milestone8 -- same

Again, for some reason windows xp always booted 4 cores.(!??)

Yes, that's strange, I tested it with Windows 7 and had also no issues. One of my thought was that it is an issue with the Chip providing the USB-onboard-function. But when google is correct your board uses a chipset from AMD, and my board is using Nvidia.

---

### Post by lwhitmore on 2009-10-25
I've got the same problem with an Athlon II x4 620 .. I can intermittently boot with a bluetooth dongle plugged into the SN78SH7 - but most of the time I can't.

When it can't boot, it just hangs with "Not responding" < which is referring to the cores afaik.

If I boot without the bt dongle attached I can use the machine without problem.

---

