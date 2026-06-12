---
title: "Install misery"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by edwardc01 on 2010-10-23
I have downloaded the dvd image "ubuntu-10.10-dvd-amd64.iso", the md5sum checks against the cdimages.ubuntu.com site and I have burned the image to a DVD+R disc successfully.  However when I attempt to boot the disc from an HPE-210f (Quad Core AMD64) system or from an HP a1268e system I'm unable to get it to come up.  On the HPE-210f (Dual Core AMD64 I finally get the following message:

   BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
   Enter 'help' for a list of built-in commands.

   (initramfs) Unable to find a medium containing a live file system
    _

On the HPa1268e the system just freezes after the initial screen that offers an option to run without installing (which I'm choosing, I think).

I had previously downloaded the Ubuntu 10,04.1 LTS cd image, and I get the exact same results.  

I know that the system is booting into a shell that I can talk to from the command line but I can't look at a lot of the file (such as dmesg) since the pipe to more or just more on a file doesn't work. (probably not identifying my monitor).

Appreciate any help!  Would love to remove the Windows XP from my wife's PC and I know it would run much faster.

---

### Post by kansasnoob on 2010-10-23
Do you even see the first purple screen with two small images at the bottom?

Do you have any older Linux Live CD's laying around?

I'm asking because I'd like to see some hardware info on the machine. Specifically:

```
lspci | grep VGA
```

```
cat /proc/cpuinfo
```

```
free
``` or "free -m"

I've been fairly impressed with the ability of Lucid Puppy to boot nearly everything I've thrown at it. Not that I'm recommending installing it, just that it's great for diagnostics.

[http://puppylinux.org/main/Download%20Latest%20Release.htm](http://puppylinux.org/main/Download%20Latest%20Release.htm)

W/O some more hardware info we can't help much :(

---

### Post by edwardc01 on 2010-10-23
Thanks for that suggestion.  I was able to boot a Fedora-i686-Live.iso and everything came up working except for networking.  I didn't try to troubleshoot that at this time but I was able to run the commands you suggested.

[B]lspci|grep VGA
[/B]01:00.0 VGA compatible controller: ATI Technologies Inc Device 68f9[B]

cpuinfo
[/B]processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 4
model name    : AMD Phenom(tm) II X4 945 Processor
stepping    : 3
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips    : 6000.20
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 4
model name    : AMD Phenom(tm) II X4 945 Processor
stepping    : 3
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips    : 6000.37
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 2
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 4
model name    : AMD Phenom(tm) II X4 945 Processor
stepping    : 3
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips    : 6000.37
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 3
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 4
model name    : AMD Phenom(tm) II X4 945 Processor
stepping    : 3
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips    : 6000.37
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

[B]free
[/B]             total       used       free     shared    buffers     cached
Mem:       3348376    1144016    2204360          0     150608     746680
-/+ buffers/cache:     246728    3101648
Swap:            0          0          0It seems 32 bit OS works fine.

---

### Post by ricepw on 2010-10-23
You just might want to try to burn the DVD or CD at a slower speed.

Just a suggestion.:guitar:

---

