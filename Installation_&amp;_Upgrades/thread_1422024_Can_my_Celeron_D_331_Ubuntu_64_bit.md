---
title: "Can my Celeron D 331 Ubuntu 64 bit?"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by URGettingADull on 2010-03-04
After posting regarding my inability to boot into windoze, which is now solved, I am here to ask the question I wanted to ask hours ago.  

I have a Celeron D 331, the lscpu output for my computer included i686, which after searching the forums lead me to believe I could not install 64 bit on this processor.

However, having run the intel processor id utility, it return with Intel 64 technology included.  Does this mean I can run Ubuntu 64 bit? 

Thanks in advance, I really can't afford to brick this thing.

---

### Post by tgalati4 on 2010-03-04
cat /proc/cpuinfo

---

### Post by ram2500 on 2010-03-05
I think a Celeron D is 64-bit. I'm guessing if the processor or the PC as a whole was manufactured after 2005, chances are it's a 64-bit processor.

---

### Post by URGettingADull on 2010-03-05
kristian@Gigabyte:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Celeron(R) CPU 2.66GHz
stepping    : 1
cpu MHz        : 2666.910
cache size    : 256 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr
bogomips    : 5333.82
clflush size    : 64
power management:

---

### Post by ram2500 on 2010-03-05
I think dtes64 MIGHT be designating that it's a 64-bit chip, but usually 64-bit chips would be identified as ia64 (Intel) or amd64 (AMD).

---

### Post by tgalati4 on 2010-03-05
I've  got 64-bit running on my Pentium D machine.  Try the live 64-bit cd.  Worst that will happen:
Error:  wrong architecture

---

### Post by URGettingADull on 2010-03-05
excellent point, having been a windows user for so long I had forgotten about that beautiful little Ubuntu nugget, will be running that shortly :D:D:D

---

### Post by cascade9 on 2010-03-05
Celeron D 331 is 64bit. 

> All 9xx, 8xx, 6xx, 5x9, 5x6, 5x1, 3x6, and 3x1 series CPUs have Intel 64 enabled

[http://en.wikipedia.org/wiki/Intel_64#Intel_64](http://en.wikipedia.org/wiki/Intel_64#Intel_64)

> **ram2500 said:**
> I think dtes64 MIGHT be designating that it's a 64-bit chip, but usually 64-bit chips would be identified as ia64 (Intel) or amd64 (AMD).

ia64 is itanium, and is not x86 (or x86_64) compatible. Itanium wont run with ubuntu at all. 

[http://en.wikipedia.org/wiki/Itanium](http://en.wikipedia.org/wiki/Itanium)

---

### Post by URGettingADull on 2010-03-05
Posting this from the live CD, however, I am having a hard time getting the partition I want to install in to come up on the partition manager screen.  I want to install over my existing 32bit 9.10, is there any way to do this without just wiping the partition using gparted, or will does 64bit only use ext4, i know my existing is ext3

---

### Post by oldos2er on 2010-03-05
"flags : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx [COLOR="Red"]lm[/COLOR] constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr"

"lm" indicates a 64-bit capable processor.

---

### Post by URGettingADull on 2010-03-05
I am running it now, and I have to say it is noticeably faster on this machine than 32 Bit was.  

Thanks for the help everybody!

---

