---
title: "Karmic Live CD fails to load after grub"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Trefenwyd on 2009-10-24
I have a Dell XPS 630i with an nvidia 280 GTX card with 4GB of RAM.

When I try and boot to the live CD(amd64), it fails to boot after the initial "Try Ubuntu without installing."

I get a blinking cursor and lose any keyboard interaction.  I have let it sit there for over an hour once thinking that it may just be going very slow.  I was able to at least get the 32 bit version of the beta CD to load all the way, but it took over 30 minutes from power on to desktop.

If you would like more information, please let me know.  I understand the final release is a very short time away, and I may have missed my chance.  I really enjoy running Ubuntu, and after booting the CD on another computer, I really REALLY want to begin using 9.10 as I love the setup of it.

Any input at all would be greatly appreciated.

--I have already tried all the options provided in the "F6" menu on the live CD.  Do you guys know of any others I could try?

---

### Post by motsteve on 2009-10-24
Could you get it to the menu item called "verify media"?  It sounds like you have something wrong way down at the ground level.  Check out your CD with this test.

---

### Post by Trefenwyd on 2009-10-24
I tried that.  It came back with no errors.  I also tried re burning several CDs.  I had the same problem on the beta.

I could get 32 bit to boot, albeit slowly, though I haven't tried the 32 bit RC yet.  I plan on trying that when I get home.

---

### Post by motsteve on 2009-10-24
I love Ubuntu, I really do, but I've had no luck with 9.10.  I'm using 9.04 and have absolutely little trouble with it, it is as smooth as silk. It worked great on my old clunky P4 and it works great on my kick *** i7.  When the kinks get worked out of Karmic, then you can upgrade, but I think you stand a good chance of success with 9.04 or even Linux Mint, which is Ubuntu in a different color. Take that from a guy who's been using Macs since 16 Feb 1984. :)

---

### Post by Trefenwyd on 2009-10-24
Haha, I'm in the IT business.  I've actually been using Ubuntu since 6.06 myself.  I have hopped around, but I've yet to find a distro that seemed as professional as Ubuntu.

It's a shame too, since I really liked the look and feel of the 32 bit version, but I refuse to run 32 bit on new computer.

And yes, 9.04 has been rock solid since april.

---

### Post by motsteve on 2009-10-24
My i7 is running the 64 bit with narry even a hiccup.  Glowing things are said of 9.10, but it has kicked my tail something awful; clean or upgraded in installation.

---

### Post by Trefenwyd on 2009-10-24
I love the new look of it, and I want to benefit from the kernel mode setting, but I can't even get the darned thing to boot.  I wonder if there's a line I can try after the kernel to get it to boot properly.

I'm at a complete loss.  I've tried to get rid of splash and quiet, but it's not even posting afterwards.  I'm not sure why it would just hang like it has.

Here's to hoping the final works :)  Otherwise, I'm going to try installing 9.04 fresh and doing a distribution upgrade from there.

---

### Post by Trefenwyd on 2009-10-24
root@kyle-compy:~# lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation GT200 [GTX280] (rev a1)
02:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

root@kyle-compy:~# lsusb
Bus 001 Device 009: ID 0424:2514 Standard Microsystems Corp.
Bus 001 Device 008: ID 05a9:2643 OmniVision Technologies, Inc.
Bus 001 Device 004: ID 0424:2512 Standard Microsystems Corp.
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 006: ID 413c:2006 Dell Computer Corp.
Bus 002 Device 005: ID 413c:1004 Dell Computer Corp.
Bus 002 Device 004: ID 045e:070f Microsoft Corp.
Bus 002 Device 003: ID 0461:4d22 Primax Electronics, Ltd
Bus 002 Device 002: ID 0955:000a NVidia Corp.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

root@kyle-compy:~# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz
stepping        : 10
cpu MHz         : 1998.000
cache size      : 6144 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 4
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips        : 5666.27
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz
stepping        : 10
cpu MHz         : 1998.000
cache size      : 6144 KB
physical id     : 0
siblings        : 4
core id         : 3
cpu cores       : 4
apicid          : 3
initial apicid  : 3
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips        : 5666.67
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz
stepping        : 10
cpu MHz         : 1998.000
cache size      : 6144 KB
physical id     : 0
siblings        : 4
core id         : 1
cpu cores       : 4
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips        : 5666.63
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz
stepping        : 10
cpu MHz         : 1998.000
cache size      : 6144 KB
physical id     : 0
siblings        : 4
core id         : 2
cpu cores       : 4
apicid          : 2
initial apicid  : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips        : 5666.63
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

This is what my lspci and lsusb output is, along with the cpuinfo.

---

### Post by motsteve on 2009-10-24
My clean install of the critter wouldn't boot either.  I went into my other working OS and found out the Karmic xorg.conf file is only about 5 lines long.  I tried also to fix the grub menu, but found out that it is probably grub2 because /boot/grub is full of Amiga sound files. Whoa!  Try replacing your xorg.conf in /etc/X11/ on your Karmic / partition.  I hate these "simple" upgrades that never are. :)

---

### Post by Trefenwyd on 2009-10-24
I was actually trying a fresh installation.  I hate upgrading myself.  It always seems to foul up.

---

### Post by Trefenwyd on 2009-10-24
As an update, the x86 version works just fine.  It appears that only the amd64 will not boot.

---

### Post by krausest on 2009-10-25
I have a similiar issue. My laptop (a HP hdx 9300) hangs on booting unless acpi is disabled, but only on x86_64 (x86_32 is fine). 9.04 worked fine for both x86_64 and x86.
See here for details:
[http://bugzilla.kernel.org/show_bug.cgi?id=14244&action=View](http://bugzilla.kernel.org/show_bug.cgi?id=14244&action=View)
[https://bugs.launchpad.net/ubuntu/+bug/410984](https://bugs.launchpad.net/ubuntu/+bug/410984)

---

