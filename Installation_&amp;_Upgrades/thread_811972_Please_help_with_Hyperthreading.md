---
title: "Please help with Hyperthreading"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by linuxpenguin on 2008-05-29
I have 2 boxes - one with Ubuntu 8.04 Server, the other set up with Mythbuntu - which at least according to what I see *should* have hyperthreading capabilities.  I've tried to enable it for both, but to no avail.  Could someone please help?  I've tried adding the "acpi=ht" and "ht=on" options to the GRUB menu.lst and running "update-grub" but when I reboot I still get the same results.

The server, I've heard hyperthreading is sometimes not so good for server security so I'm not really going to bother much with it.  But the MythTV box, I think hyperthreading could really help with encoding and such so I'd like to have it if I can.  Here's the output of "dmesg | grep "CPU"" and "cat /proc/cpuinfo":

```
myth@myth-desktop:/var/log$ dmesg | grep "CPU"
[    0.000000] Initializing CPU#0
[   13.618727] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   13.698870] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000 00000000
[   13.698888] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   13.698892] CPU: L2 cache: 512K
[   13.698895] CPU: Hyper-Threading is disabled
[   13.698898] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00000400 00000000 00000000 00000000
[   14.166965] CPU0: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 07
[   14.313654] Brought up 1 CPUs
[   14.313685] CPU0 attaching sched-domain:
[   14.896621] Switched to high resolution mode on CPU 0
myth@myth-desktop:/var/log$ dmesg | grep "CPU"
[    0.000000] Initializing CPU#0
[   13.618727] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   13.698870] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000 00000000
[   13.698888] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   13.698892] CPU: L2 cache: 512K
[   13.698895] CPU: Hyper-Threading is disabled
[   13.698898] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00000400 00000000 00000000 00000000
[   14.166965] CPU0: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 07
[   14.313654] Brought up 1 CPUs
[   14.313685] CPU0 attaching sched-domain:
[   14.896621] Switched to high resolution mode on CPU 0
myth@myth-desktop:/var/log$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 2.00GHz
stepping	: 7
cpu MHz		: 1992.664
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts sync_rdtsc cid
bogomips	: 3989.48
clflush size	: 64

```

The "ht" flag means this can do hyperthreading, I thought.  There's no option to enable/disable hyperthreading in BIOS unfortunately so I can't try that.  Any ideas?  I don't see any reason why it couldn't do hyperthreading, but maybe there's just something I'm looking past (or not understanding).

The PC is a Dell Optiplex GX260 with an Intel chip, not sure if that helps.

---

### Post by prshah on 2008-05-29
> **linuxpenguin said:**
> 
The PC is a Dell Optiplex GX260 with an Intel chip, not sure if that helps.

Looks like you can't on this particular machine:
[http://www.hardforum.com/archive/index.php/t-1120255.html](http://www.hardforum.com/archive/index.php/t-1120255.html)
[http://lists.us.dell.com/pipermail/linux-poweredge/2003-September/009845.html](http://lists.us.dell.com/pipermail/linux-poweredge/2003-September/009845.html)

---

### Post by linuxpenguin on 2008-05-29
Crap.  Well I guess that answers the question anyway, thanks.

---

