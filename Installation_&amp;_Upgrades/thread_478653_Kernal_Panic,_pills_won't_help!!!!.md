---
title: "Kernal Panic, pills won't help!!!!"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by Turboaaa2001 on 2007-06-19
Here's my issue. My only cd burner is dead and I orderd Fiesta but it won't get here for a while. I'm trying to install version 6.06 (I forget the name) for now on my high end machine as the primary partition and have Windows XP Por Mediacenter Edition as my second for high end games.

When I boot to the disk I get the normal options to either run the live cd and install or add boot options. When-ever I try to boot to the live cd I get a message saying something about the kernal panicking. (I understand thats not very clear so if you need more let me know)

At first it was referencing the APIC. I went into my BIOS and turned off an advanced feature so that my MPI would be used.  This solved that problem but now I'm getting another panic further on in the build. I have not been able to get to the live cd desktop.


My computer:

Core 2 Duo 6400 (Over CLocked to 2.71)
BFG-Tech nVidia 680i SLI Motherboard (Updated BIOS)
2GB DDR2 Dual Channel (512MB x 4)
EVGA GeForce 7600GT 256MB GDDR3 PCIex16 (x2 in SLI)
150GB SATA HD
CD-ROM
USB FLoppy

If you have any ideas please let me know. Like I said I want to dual boot with Ubuntu as my primary and Windows as secondary.

Thanks

---

### Post by floke on 2007-06-19
No idea if this will help or not - but for some distros to boot on my dual core I have to manually disable one of them in the BIOS lest it chucks a kernel wobbly too.

---

### Post by Turboaaa2001 on 2007-06-19
Were you able to enable the second core afterwards and have a stable run? Normally running both cores for everyday tasks like I mentioned is fine because it's not needed and it saves power.

But I (like alot of people) run BOINC ( [www.boinc.berkeley.edu](www.boinc.berkeley.edu) ) and work with several projects. Both cores are used whenever the machine is running.  In fact, at 1 time I had 10 computers running, but with always triping the fuses in the house I learned I have to keep it down to just a few. Well, until I get the wireing done for my server farm BWA HA HA HA. :twisted:

---

### Post by Turboaaa2001 on 2007-06-20
I tried disabling the second core with no luck.

Check this out!!! I tried running the 64bit install and got the same results. What was cool was when I ran 5.10 instead of 6.01 . I got the same error but a more precise message...

I cut it down to just the imprtant stuff:


.073000] CPU: L1 I cache: 32K, L1 D cache: 32K
.073000] CPU: L2 cache 2048K
.073000] CPU: Intel(R) Core(TM)2 CPU      6400 @ 2.13
.073000] Enabling fast FPU save and restore... done.
.073000] Enabling unmasked SIMD FPU exception support... done.
.077000] Checking for popad bug... OK.
.077000] checking if image is initramfs... it isn't (no cpio magic); looks like an initrd
.222000] Freeing initrd memory: 3963k freed
.228000] ACPI: Looking for DSDT in initrd... not found!
.248000]  not found!
.261000] ENABLING IO-APIC IRQs
.262000] ..TIMER: vector=0x31 pin1=0 pin2=-1
.263000] ..MP-BIOS bug 8254 timer not connected to IO-APIC
.263000] ...trying to set up timer (IRQ0) through the 8259A ... Failed!
.263000] ...trying to set up timer as Virtual Wire IRQ... Failed!
.263000] ...trying to set up timer as ExtINT IRQ... Failed :(.
.372000] Kernal panic - not syncing: IO-APIC + timer doesn't work!


PLEASE HELP ME!!!

---

### Post by confused57 on 2007-06-20
You might try some of the boot parameters mentioned in this thread:
[http://ubuntuforums.org/showthread.php?p=2798818](http://ubuntuforums.org/showthread.php?p=2798818)

---

### Post by Turboaaa2001 on 2007-06-23
I tried following the directions in that thread with no luck. If I had any Idea that this was going to take this long I would have kept Windows on it for a while longer...

Something else I tried was to disable the second core and any APIC and APCI controls within the BIOS, This had no effect, but It does take me to somewhat different results but basicaly the same.

I noticed several other people having problems witht the E6400 -6700 CPUs, could that be it? I'm a tech but I'm new to Linux.

I'm very thankfull for all your help, please help me get this up and running!!!

---

