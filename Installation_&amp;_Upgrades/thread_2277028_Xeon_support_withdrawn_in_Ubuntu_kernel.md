---
title: "Xeon support withdrawn in Ubuntu kernel?"
date: 2015-05-06
forum: Installation &amp; Upgrades
---

### Post by mark216 on 2015-05-06
I use a system with two twn-core Xeon processors. This still works fine under the 32 bit kernel 3.13.0-51, but will not start up with either the 3.16 or 3.19 kernels. Therefore, although I've updated to Ubuntu 15.04, I have had to keep the 3.13.0-51 kernel.

Has Xeon support been withdrawn from these later kernels, or is a "tweak" needed?

The processors are 32 bit, and the output from "[COLOR=#111111][FONT=Consolas]cat /proc/cpuinfo[/FONT][/COLOR]" is as follows:

```
==== start of output ====
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Xeon(TM) CPU 2.80GHz
stepping    : 9
microcode    : 0x15
cpu MHz        : 2790.845
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips    : 5581.69
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Xeon(TM) CPU 2.80GHz
stepping    : 9
microcode    : 0x15
cpu MHz        : 2790.845
cache size    : 512 KB
physical id    : 3
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 6
initial apicid    : 6
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips    : 5582.45
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Xeon(TM) CPU 2.80GHz
stepping    : 9
microcode    : 0x15
cpu MHz        : 2790.845
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips    : 5582.43
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Xeon(TM) CPU 2.80GHz
stepping    : 9
microcode    : 0x15
cpu MHz        : 2790.845
cache size    : 512 KB
physical id    : 3
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 7
initial apicid    : 7
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips    : 5582.46
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

==== end of output ====
```

I really hope that it's just a tweak, as upgrading the hardware isn't an option. :(

Mark

---

### Post by v3.xx on 2015-05-06
Hi Mark

One reason I run Xeon is because of linux compatibility. I can't see anyone pulling the plug on support.  Makes me wonder if this could be a 32bit bug.

I did a quick search and found this:
> Install / Upgrade to Kernel 3.16 in Ubuntu:
Be aware that proprietary drivers may or may not work correctly with this kernel version. You need to rebuilt (or install) your video driver after kernel update.
I take it that no error reports are being generated.

---

### Post by mark216 on 2015-05-06
I have no proprietary drivers installed. On booting with a 3.19 kernel, I get a kernel panic, with no logging written to /var/log. The text is so verbose that the probable cause whizzes off the screen. Sadly, I don't have an easy way to set up a serial terminal here, so it's hard to see exactly where things are going wrong. :(

Mark

---

### Post by sudodus on 2015-05-06
I have an HP workstation with Xeon processors, where I'm still running Precise. I'll test what happens when I try Lubuntu 32-bit and 64-bit live (it is easy because I have two such pendrives ready).

Edit: HP workstation xw8400 with 2x2 Xeon @ 3GHz

---

### Post by mark216 on 2015-05-06
Thank you. My PC is an HP xw6000, with 2GB RAM and "Gallium 0.4 on ATI R350" graphics. I'm actually running vivid, but with the kernel packages from trusty. It was the upgrade from trusty to utopic where it ceased to boot. My current solution of using a 3.13 kernel is working for now, but I'm worried about future upgrades.

---

### Post by sudodus on 2015-05-06
I have tested ***Lubuntu 15.04 live*** booted from the desktop iso files. Both the 64-bit version and the 32-bit version boot slowly but nicely into the Lubuntu desktop. There is no indication of kernel problems. Maybe the slow booting depends on searching for some suitable driver, but they find the drivers needed.

So I suggest that you do the same - try 15.04 (which comes with 3.19)

I think you might have some other issue because of upgrading. You should try ***14.04.2 LTS*** live too (which I think comes with 3.16)

By the way, which flavour of Ubuntu are you running?

I remember that there were problems with the Lubuntu alternate iso of 14.04.2 - maybe there are similar problems with Ubuntu Server. In that case you might be able to start from the ***Ubuntu mini.iso***, that you find at [this link]("http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730")

---

### Post by sudodus on 2015-05-06
There might also be problems due to the ATI graphics, that the drivers that come with the newer kernels do not work with your graphics chip. In that case you might stay with the 3.13 kernel (which has long time support) as long as 14.04 LTS (until April 2019), or get a graphics card that is compatible with newer versions of Ubuntu (and its linux kernel). I have an nvidia GeForce GT 430 card and it works with the free nouveau drivers and with the nvidia proprietary driver 304.125.

---

### Post by mark216 on 2015-05-08
That's a good point - it could be one of those cases where it might take a clean install, but not an upgrade. I'll try downloading the iso image and if that fails then I'll try a different graphic card.

Oh, and it's just the ordinary Ubuntu that I'm using, not one of its subclasses.

Mark

---

### Post by sudodus on 2015-05-08
I think kernel issues are independent of the Ubuntu flavour (only variations of the desktop environment). Graphics issues might be affected by the desktop environment. Standard Ubuntu is more demanding on the CPU horsepower and the graphics capability compared to Lubuntu, Xubuntu and Ubuntu Mate.

---

### Post by mark216 on 2015-05-11
I've solved this one! Booting from the Ubuntu 15.04 i386 installation disk give a short error trace (transcribed by hand, so any errors in transcription are my fault):
[    8.303374] ACPI PCC probe failed.
Starting version 219
[   40.841006] Kernel panic &#8211; not syncing: BRKADRINT
[   40.841146] CPU: 2 PID: 67 Comm: kworker/u8:3 Tainted: G      W    3.19.0-15-generic #15-Ubuntu
[   40.841394] Hardware name: Hewlett-Packard hp workstation xw6000/080Ch, BIOS 68604 v1.18 02/24/2004
[   40.841649] Workqueue: scsi_tmf_2 scmd_eh_abort_handler
[   40.841805] 00000000 00000000 f41ede2c c16e966d f870a310 f41ede44 c16e7bf8 f4fa0000
[   40.842109] f870a310 f4fa0000 f4fa0000 f41ede64 f86f7e22 f870ed03 f768f000 f870f429
[   40.842411] d0fffdf4 f4fa0000 0000009b f41ede78 f87007bf f4fa0000 000003e8 f4fa0000
[   40.842712] Call Trace:
[   40.842792]  [<c16e966d>] dump_stack+0x41/0x52
[   40.842931]  [<c16e7bf8>] panic+0x81/0x199
[   40.843063]  [<f86f7e22>] ahd_handle_hwerrint+0x42/0x70 [aic79xx]
[   40.843242]  [<f87007bf>] ahd_intr.part.49+0x13f/0x140 [aic79xx]
[   40.843423]  [<f8700947>] ahd_pause_and_flushwork+0x157/0x170 [aic79xx]
[   40.843615]  [<f8705491>] ahd_linux_abort+0x151/0x690 [aic79xx]
[   40.843787]  [<c13ab523>] ? get_color+0x23/0x110
[   40.843926]  [<c14bb0e0>] scmd_eh_abort_handler+0x60/0x480
[   40.844010]  [<c10761c0>] ? pwq_dec_nr_in_flight+0x40/0x90
[   40.844010]  [<c1077ae2>] process_one_work+0x122/0x3a0
[   40.844010]  [<c1078489>] worker_thread+0x39/0x4d0
[   40.844010]  [<c1078450>] ? rescuer_thread+0x320/0x320
[   40.844010]  [<c107c62b>] kthread+0x9b/0xb0
[   40.844010]  [<c16ef501>] ret_from_kernel_thread+0x21/0x30
[   40.844010]  [<c107c590>] ? kthread_create_on_node+0x150/0x150
[   40.844010] Kernel Offset: 0x0 from 0xc1000000 (relocation range: 0xc0000000-0xf83fdfff)
[   40.844010] drm_kms_helper: panic occurred, switching back to text console
[   40.844010] ---[ end Kernel panic &#8211; not syncing: BRKADRINT

There are two interesting things about this stack trace: the long delay between the second and third lines, and the appearance of aic79xx against several entries, implying that a SCSI driver was at fault.

I use an IDE drive, so [LEFT][COLOR=#000000][FONT=Calibri]within the BIOS, the two &#8220;Hewlett-Packard SCSI controller&#8221; entries were set to &#8220;Disable&#8221;.[/FONT][/COLOR][/LEFT] This was fine with kernels up to 3.13.

I enabled the SCSI controllers within the BIOS. Now, on boot, the SCSI bus is searched for devices (so a slight delay in booting) but the 3.19 kernel now starts successfully.

So the problem was the aic79xx SCSI controller - once the device is enabled in the BIOS, then the kernel boots fine.

sudodus and v3.xx, thank you for your help. You both prodded my thinking, which then led to the eventual solution.

---

### Post by sudodus on 2015-05-11
Congratulations :-) Now you can run your workstation with new kernels again.

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by mark216 on 2015-05-11
Done!
Thank you - I had looked for a way to mark the thread as solved, but looked in all the wrong places :(

Mark

---

### Post by dino99 on 2015-05-11
> **mark216 said:**
> Done!
Thank you - I had looked for a way to mark the thread as solved, but looked in all the wrong places :(

Mark

click on the 'Thread Tools' from your first post, on top right corner, and set it as SOLVED

---

