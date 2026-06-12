---
title: "Building a kernel from kernel.org"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by jmarc on 2006-12-31
I've installed 6.06 on my new computer (Asus P5B Deluxe, Core 2 Duo, SATA HD and DVD).  Small problems with the stock kernels:
   - the first ethernet interface isn't initialized correctly at boot.  Issuing ifdown eth0, ifup eth0 (generally once, sometimes more times) solve the problem.
   - the second ethernet interface isn't recognized at all
   - only 2 out of 4 GB of memory is recognized.

From some web search, I deduced that I needed use a more recent kernel for the two first problems and use the 64 GB high memory option instead of the 4 GB.

I've downloaded 2.6.19 from kernel.org and was unable to compile a kernel which booted correctly.  Setting various combination of noapic, nolapic, acpi=off didn't help. The most common problem was at long pause after having displayed (I've removed splash and quiet options):
[17179582.112000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
the complaining that the root partition is not present and reverting to a root shell.

I've downloaded 2.6.15 from kernel.org and was also unable to compile a kernel which booted correctly, with the same symptom.  Even if I used the configuration from the stock kernel.

I've used apt-get to get the kernel source patched by Ubuntu and was finally able to compile a 2.6.15 kernel which booted.  Trying several configurations, I apparently need ACPI_SLEEP (if I remove this option, I get the same symptom as above), but that is not enough with the non patched kernels (BTW setting the 64 GB option allows to recognize all my memory).

I'm now running out of ideas and if the solution to my problem is available on the web, I must have overlooked it.  Does somebody has any ideas which could help me?

---

### Post by skale on 2006-12-31
Most likely, something else essential that the computer needed to boot was not compiled.  Did you use lspci? Could you post it?  Along with lsusb and `cat /proc/cpuinfo`.  
What exactly goes wrong now?  

I'm thinking just use the patched kernels.  Whatever.  I don't really know what is in the patches, so I can't really give you any good advice.

---

### Post by jmarc on 2006-12-31
> **skale said:**
> Most likely, something else essential that the computer needed to boot was not compiled.

What I though.  But what?  I've looked at all the configuration options one by one and find no hint.  And there is no differences in the configuration between patched and non patched kernels.

And the fact that ACPI_SLEEP seems to be required with the patched kernel makes no sense to me.

> Did you use lspci? Could you post it?

[QUOTE=lspci]0000:00:00.0 Host bridge: Intel Corporation: Unknown device 29a0 (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation: Unknown device 29a1 (rev 02)
0000:00:1a.0 USB Controller: Intel Corporation: Unknown device 2834 (rev 02)
0000:00:1a.1 USB Controller: Intel Corporation: Unknown device 2835 (rev 02)
0000:00:1a.7 USB Controller: Intel Corporation: Unknown device 283a (rev 02)
0000:00:1b.0 0403: Intel Corporation: Unknown device 284b (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation: Unknown device 283f (rev 02)
0000:00:1c.4 PCI bridge: Intel Corporation: Unknown device 2847 (rev 02)
0000:00:1c.5 PCI bridge: Intel Corporation: Unknown device 2849 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation: Unknown device 2830 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation: Unknown device 2831 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation: Unknown device 2832 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation: Unknown device 2836 (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
0000:00:1f.0 ISA bridge: Intel Corporation: Unknown device 2810 (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation: Unknown device 2820 (rev 02)
0000:00:1f.3 SMBus: Intel Corporation: Unknown device 283e (rev 02)
0000:00:1f.5 IDE interface: Intel Corporation: Unknown device 2825 (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0392 (rev a1)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4364 (rev 12)
0000:03:00.0 IDE interface: Unknown device 197b:2363 (rev 02)
0000:05:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
[/QUOTE]

[quote=skale]Along with lsusb[/quote]

[quote=lsusb]Bus 004 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 003 Device 004: ID 046d:c03d Logitech, Inc.
Bus 003 Device 005: ID 0430:0005 Sun Microsystems, Inc. Type 6 Keyboard
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
[/quote]

[quote=skale]and `cat /proc/cpuinfo`.[/quote]  
[quote=cpuinfo]
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 2400.486
cache size      : 4096 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ssht tm pbe nx lm pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4805.16

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 2400.486
cache size      : 4096 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ssht tm pbe nx lm pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4800.37
[/quote]

[quote=skale]What exactly goes wrong now?[/quote]  

With the patched kernel: one network interface recognized, and one not initialized correctly at boot.

With non patched kernels (and with patched kernel without ACPI_SLEEP: long wait after 
[17179582.112000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
then complain that the root partition does not exist and a root shell is launched (/proc/cpuinfo is correct, lspci and lsusb are not available).

> I'm thinking just use the patched kernels.  Whatever.

I could probably hack something for the first network interface; but I also had a use for the second one :-(

---

### Post by skale on 2007-01-01
If it is the wireless netowrk interface that does not work, use ndiswrapper and the windows driver check the wiki.  I have a TRENDNet wireless card which needs it.  So don't worry if it does not load.  

There is a USB HID something-or-the-other support which you need to compile in.  It's an easy one to miss, as it is buried in all the other USB devices which can be compiled.  

Be glad you remembered to compile ext3 support.   I spent two hours slapping myself afterward.  ](*,)

---

### Post by jmarc on 2007-01-02
> **skale said:**
> If it is the wireless netowrk interface that does not work, use ndiswrapper and the windows driver check the wiki.  I have a TRENDNet wireless card which needs it.  So don't worry if it does not load.

There is no wireless interface on the mother board.  It's the second ethernet one.  Note that I think I've seen a patch to activate it somewhere.

> There is a USB HID something-or-the-other support which you need to compile in.  It's an easy one to miss, as it is buried in all the other USB devices which can be compiled.

I'll double check when at home.  But I copied the configuration and checked manually afterwards when looking if option specific to the patch could explain the difference.

> Be glad you remembered to compile ext3 support.   I spent two hours slapping myself afterward.  ](*,)

Be there, done that.  But not this time :)

---

