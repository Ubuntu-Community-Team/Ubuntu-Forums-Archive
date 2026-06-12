---
title: "Dual processors?"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by J77 on 2006-02-28
Hello,

Have recently installed ubuntu on my new machine.

Does the installation account for dual processors automatically, or do I need to do something?

On an old machine (RedHat Enterprise), when I typed 'top' I could see what both cpus were doing - on ubunut, I only see one...

---

### Post by codejunkie on 2006-02-28
[QUOTE=J77]Hello,

Have recently installed ubuntu on my new machine.

Does the installation account for dual processors automatically, or do I need to do something?

On an old machine (RedHat Enterprise), when I typed 'top' I could see what both cpus were doing - on ubunut, I only see one...[/QUOTE]
you need to install a smp linux-image package, open synaptic and search for linux-image and install the one for your kernel, use linux-image-kernelversion-386-smp for older intel cpu's, linux-image-kernelversion-686-smp for newer intel cpu's, and linux-image-kernelversion-k7-smp for amd cpu's.

---

### Post by localzuk on 2006-02-28
I can't remember if the default kernel installed provides dual processor support (I think it does). However, if you look at installing one of the 'SMP' kernels from the repo's that should do the job.

---

### Post by J77 on 2006-02-28
Thanks,

Did that and restarted machine (processors are Xeons so I got the 686 one).

What's the command for finding which kernel is running?

(top only shows one cpu still...)

edit:

uname -a

gives

Linux me 2.6.12-9-686-smp #1 SMP Mon Oct 10 13:36:57 BST 2005 i686 GNU/Linux

is there a good way of making sure both processors are being optimised?

edit2: sorry for being lame and answering my own queries...

I did: cat /proc/cpuinfo

and got:

vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Xeon(TM) CPU 3.40GHz
stepping        : 3
cpu MHz         : 3401.595
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_c
pl est cid cx16 xtpr
bogomips        : 6733.82

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Xeon(TM) CPU 3.40GHz
stepping        : 3
cpu MHz         : 3401.595
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_c
pl est cid cx16 xtpr
bogomips        : 6782.97

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Xeon(TM) CPU 3.40GHz
stepping        : 3
cpu MHz         : 3401.595
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_c
pl est cid cx16 xtpr
bogomips        : 6799.36

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Xeon(TM) CPU 3.40GHz
stepping        : 3
cpu MHz         : 3401.595
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_c
pl est cid cx16 xtpr
bogomips        : 6782.97

**I'm very confused now... have I got 4 processers ?!?!?**

---

### Post by codejunkie on 2006-02-28
[QUOTE=J77]Thanks,

Did that and restarted machine (processors are Xeons so I got the 686 one).

What's the command for finding which kernel is running?

(top only shows one cpu still...)

edit:

uname -a

gives

Linux me 2.6.12-9-686-smp #1 SMP Mon Oct 10 13:36:57 BST 2005 i686 GNU/Linux

is there a good way of making sure both processors are being optimised?

edit2: sorry for being lame and answering my own queries...

I did: cat /proc/cpuinfo

and got:

vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Xeon(TM) CPU 3.40GHz
stepping        : 3
cpu MHz         : 3401.595
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_c
pl est cid cx16 xtpr
bogomips        : 6733.82

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Xeon(TM) CPU 3.40GHz
stepping        : 3
cpu MHz         : 3401.595
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_c
pl est cid cx16 xtpr
bogomips        : 6782.97

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Xeon(TM) CPU 3.40GHz
stepping        : 3
cpu MHz         : 3401.595
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_c
pl est cid cx16 xtpr
bogomips        : 6799.36

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Xeon(TM) CPU 3.40GHz
stepping        : 3
cpu MHz         : 3401.595
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_c
pl est cid cx16 xtpr
bogomips        : 6782.97

**I'm very confused now... have I got 4 processers ?!?!?**[/QUOTE]
im not 100% on this, but id say your seeing this, because those processors are dual core it's listing both cores of both cpu's.

---

### Post by RAOF on 2006-03-01
[QUOTE=J77]...
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat pse36 clflush dts acpi mmx fxsr sse sse2 ss **ht** tm pbe nx lm pni monitor ds_c
pl est cid cx16 xtpr
...[/QUOTE]

Actually, it looks like those Xeons are hyperthreaded (aka: SMT).  So each processor appears as 2 virtual processors, and you've got 2 processors, so...

---

### Post by J77 on 2006-03-15
Well, the new kernal seems to be working fine.

If I have 4, say, Matlabs running - I get 100% on each copy.

I'm still confused as to what the dual core/virtual(?) stuff does though...

---

### Post by therunnyman on 2006-03-15
Hi All,

Very useful post.  I'd assumed Ubuntu picked up the dual processor, as it did everything else, but it didn't.  I grabbed an smp kernel, and all is well.

A couple questions.  First, I encountered an "sm" kernel for the most recent iteration.  Is this the same thing as an "smp" kernel, or did I do right by nabbing an older one?  Second, is there a way to update to the smp kernels automatically (that is, synaptically), instead of the default kernel?  Third, gediting menu.lst is getting a little old; is there a way to automatically comment out or be rid of older kernels?

Thanks in advance.

therunnyman

---

### Post by RAOF on 2006-03-15
[QUOTE=J77]...
I'm still confused as to what the dual core/virtual(?) stuff does though...[/QUOTE]
The hyperthreading/SMT/virtual processor thing is a way of making better use of the hardware on the CPU - you have two threads (sorta) running on each processor at the same time, so that if one thread can't do anything (it's waiting for data from memory, or whatever) the processor can hopefully run an instruction from the other thread instead.

[QUOTE=therunnyman]...Second, is there a way to update to the smp kernels automatically (that is, synaptically), instead of the default kernel?  
[/QUOTE]
Yes.  Install the "linux-*yourprocessorarch*-smp" package.  So, by default for an intel system, this would be the "linux-smp" package (or linux-686-smp, or linux-k7-smp, etc).  It's a metapackage which does nothing but depend upon the latest smp kernel - any updates will then get automatically installed.
[QUOTE=therunnyman]...
Third, gediting menu.lst is getting a little old; is there a way to automatically comment out or be rid of older kernels?...[/QUOTE]
You can uninstall the old kernels using Synaptic; that will remove the entries from menu.lst.  It's probably not necessary to have more than 2 kernels lying around anyway (your current, most recent one, and the previous one in case the new one doesn't work right ;)).

---

