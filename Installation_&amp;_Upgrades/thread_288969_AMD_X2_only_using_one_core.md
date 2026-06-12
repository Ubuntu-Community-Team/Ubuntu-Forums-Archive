---
title: "AMD X2 only using one core"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by nstuart on 2006-10-30
Hi all, installed Edgy yesterday and almost everything is going fine. System works great, except that its only using one core of my AMD X2 3800. I have installed the i386 version to avoid 64bit hassles right now. Dapper worked fine and saw both cores before, but edgy doesn't seem to.

Any pointers here? Pretty much everything is set to default at the moment so its a pretty basic system install. Only thing I've messed with is my X config to get twinview working.

---

### Post by funkyade on 2006-10-30
Have you installed a 32bit SMP kernel?

If not, then you need to!

e.g. ```
#> sudo aptitude install linux-686-smp
``` and then -
```
#>sudo nano /boot/grub/menu.lst
``` to make the smp kernel the default. Then reboot.

In theory the edgy generic kernel should work, but it doesn't seem to, had a similar experience with a friends machine, which was solved this way.

---

### Post by nstuart on 2006-10-30
Ok thanks. I saw the SMP kernel there, but saw it was supposed to be obsolete by generic so I thought I would check first before installing it.

---

### Post by mossholderm on 2006-10-30
Edgy should work fine with the generic kernel. An SMP kernel should not be required. Having said that, if, for some reason you are running an i386 kernel, that might explain why only one core is being seen...

   --Matt

```
root@mourneblade:~# uname -r
2.6.17-10-generic
root@mourneblade:~# more /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_o
pt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 2012.60

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2010.444
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_o
pt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 4020.92

```

---

### Post by nstuart on 2006-10-30
Actually mossholderm thats what was going on. For some reasont he install thought to use the i386 kernel instead of the generic. Is there any reason why the i386 was even installed?

Anyways, change the kernel and resinstalling my nvidia driver/restricted modules got everything in working order, and I show 2 cores in /proc/cpuinfo

Thanks all!

---

### Post by funkyade on 2006-11-01
> **nstuart said:**
> Actually mossholderm thats what was going on. For some reasont he install thought to use the i386 kernel instead of the generic. Is there any reason why the i386 was even installed?

Anyways, change the kernel and resinstalling my nvidia driver/restricted modules got everything in working order, and I show 2 cores in /proc/cpuinfo

Thanks all!

That's good!

---

### Post by Flecko on 2006-11-01
First of all, the i386 kernel is single core only. Second of all, if you've got an Athlon X2, you should be using the K7 kernel, its got SMP enabled in it, and should theoretically be better than the generic i686 kernel for your hardware.

Hope this helps you get it working.
-Flecko

---

### Post by borobudur on 2006-11-16
I have the same problem. I'm not sure what kernel I should use. The one I have at the moment is'n satisfiable:

```
samosir@sumatra:~$ uname -r
2.6.15-27-386
samosir@sumatra:~$ more /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-50
stepping        : 2
cpu MHz         : 1596.353
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy
bogomips        : 3318.52

```

---

### Post by guisar on 2006-12-04
Is there any advantage to using the SMP kernel? I just downloaded and installed it on my core 2 duo and notice no difference what so ever... Same with my AMD X2 machine. I was using the 686 kernel previously- just the generic one with the distribution not custom compliled.

---

### Post by TrendyDark on 2006-12-04
Should work if you use the SMP-686 kernel. 

If you're using Edgy, though, you should have both cores from the get-go.

I have an Intel Core 2 Duo E6600 and I had both cores before I installed the generic SMP kernel.

---

