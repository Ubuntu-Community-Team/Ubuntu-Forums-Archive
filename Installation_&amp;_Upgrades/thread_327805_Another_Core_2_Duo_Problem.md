---
title: "Another Core 2 Duo Problem"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by capnqwest on 2006-12-29
No matter what I try, I cannot get Dapper to see both of my cores.

```
michael@mint:~$ uname -r
2.6.17-10-386

```

```
michael@mint:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz
stepping        : 6
cpu MHz         : 2666.909
cache size      : 4096 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 5339.20

```

Googling and other forum posts tell me to sudo apt-get install linux-image-2.6.17-10-generic, but I already have this kernel so I'm wondering what I'm doing wrong.  I could compile a vanilla one by hand I guess but want to know the Ubuntu way of accomplishing this.

---

### Post by bikeboy on 2006-12-29
Judging by your uname -r output you're not booted into an SMP enabled kernel. the 386 part indicates that. If you have the generic installed it says generic instead (but that is new with Edgy), and that one is SMP enabled.

Looking at the options for Dapper, try installing the "linux-686-smp" metapackage, and make sure you boot to the 686 kernel by selecting it in grub. It seems the 686 is SMP but the 386 is not.

---

### Post by capnqwest on 2006-12-29
Duh, I'm such an idiot.  I thought because I didn't see smp in the kernel name that it wouldn't support that.  Makes a huge difference though especially when running VMs in VMware6!  Thanks.

---

### Post by bikeboy on 2006-12-29
Hehe no worries. I just wish I had an smp capable processor instead of the PIII I mainly use :(

---

### Post by jfank on 2006-12-30
I'm having the same problem with mine as well.  I can't seem to find a way to get Ubuntu to see both cores.  I'm mostly using Kubuntu.  Where can I find the codec to use to get Ubuntu to recognize my process is a dual core processor.  I have the Intel Centrino Duel Core processor clocked at 1.83GHz

---

### Post by bikeboy on 2006-12-30
It's not a codec, but rather the kernel itself. What is your output of ```
uname -r
``` and also```
cat /proc/info
```

---

