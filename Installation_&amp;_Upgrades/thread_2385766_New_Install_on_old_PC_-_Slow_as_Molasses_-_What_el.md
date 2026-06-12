---
title: "New Install on old PC - Slow as Molasses - What else to check?"
date: 2018-02-24
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2018-02-24
New install of Xubuntu v16.04.03 on older system:

Mobo: PCchips GOAL3+ 
CPU: AMD Sempron 2.5 Ghz
Ram: 2 X 512MB 333Mhz DDR SDRAM
HDD: 80GB Seagate

During install it took 2 days. System runs slow as molasses! MemCheck shows OK, No HDD errors (using Falcon4 Ultimate Boot CD). Partitioned OK Ext4.
Replaced HDD cable with brand new one. Had to install a VPU in AGP slot as onboard video doesn't seem to work.

Anyone have any idea what to check next? Does Ubuntu have any diagnostics we can run??

Thanks!
:(

---

### Post by ubfan1 on 2018-02-24
Check your swap statistics with the "free" command.  Sounds like you need more memory.  Maybe try Lubuntu as a lower resource intensive distribution?  Any errors in /var/log/syslog?

---

### Post by QIII on 2018-02-24
Hello!

According to [this]("https://help.ubuntu.com/community/Installation/SystemRequirements"), the minimum *recommended* hardware requirements are:

> Ubuntu Desktop Edition

    2 GHz dual core processor
    2 GiB RAM (system memory)
    25 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach)
    VGA capable of 1024x768 screen resolution
    Either a CD/DVD drive or a USB port for the installer media

    Internet access is helpful 

So "slow as molasses" may be expected with your slow and limited RAM.  I don't think there is probably much to be done about that short of adding more RAM.  Maybe someone else has other ideas.

But if I were you I would try no more weighty a flavor than Lubuntu.

Perhaps something like [Bodhi Linux]("http://www.bodhilinux.com") might be more appropriate for that machine.  They give the minimum requirements as:

> Minimum:

    500mhz processor
    256MB of RAM
    4GB of drive space

Recommended:

    1.0ghz processor
    512MB of RAM
    10GB of drive space


Although I'm not very hopeful you can get Ubuntu running like a champ on that machine, someone may come along with a more optimistic prognosis.

---

### Post by ajgreeny on 2018-02-24
I also believe that the AMD Sempron CPUs may be lacking in their abilities for a modern OS like Xubuntu.
Show us the output of ```
cat /proc/cpuinfo | grep flags
``` which may give us more clues as to what's missing, eg sse flags.

---

### Post by Rick St. George on 2018-02-24
> **ubfan1 said:**
> Check your swap statistics with the "free" command.  Sounds like you need more memory.  Maybe try Lubuntu as a lower resource intensive distribution?  Any errors in /var/log/syslog?

"free" command shows:
              Total        Used    Free    Shared
Mem:    1022744    271100  227664   6776
Swap:   1046524            0  1046524


ERRORS: in syslog  (seems fine except)

gpu-manager[632]:  /etc/modprobe.d  is not a file

AGP aperature is 64M  (Note: AGP card is XFX One 1GB DDR3 HDMI VGA; BIOS only goes upto 512Mb for AGP aperature)

EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Either enable ECC checking or force module loading by setting 'ecc_enable_override'.

Buffer I/O error on dev sr0, logical block 357231, asyn page read
Adding 0146524k swap on /dev/sda5. 

Error: can't open /lib/modules/4.10.28-generic/updates/dkms

unsupported cpu model, user thermal-conf.xml file or run with --ignore-cpuid-check

----------------------

---

### Post by Rick St. George on 2018-02-24
> **ajgreeny said:**
> I also believe that the AMD Sempron CPUs may be lacking in their abilities for a modern OS like Xubuntu.
Show us the output of ```
cat /proc/cpuinfo | grep flags
``` which may give us more clues as to what's missing, eg sse flags.

flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt im 3dnowext 3dnow rep_good extd_apicid pni lanf_lm 3dnowprefetch vmmcall

What does that mean?

---

### Post by #&amp;thj^% on 2018-02-24
ajgreeny was pointing out or suggesting that your CPU is not quite up to the new Instruction Sets writen in the new code for those OS's
```
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp

```

---

### Post by Rick St. George on 2018-02-24
I believe its Hardware related ... just don't know what to try next. I will however see if I can find 2 x 1Gb instead of 2 x 512MB, and install Bohdi Linux follow "QIII" advice. Will report results. Thanks!

---

### Post by mörgæs on 2018-02-25
Your CPU flags are fine (and Buntu installs on even weaker CPU's) but the message

> **Rick St. George said:**
> 
Buffer I/O error on dev sr0, logical block 357231, async page read


indicates that the DVD drive or the DVD itself could have some trouble. 

Trying a new and even lighter install is a good idea. Bodhi or a minimal Buntu can also be installed from a CD.

---

### Post by bobnutfield on 2018-02-25
I try (as a hobby) to get old laptops back to a usable life by tinkering with them and installing some form of linux.  Just thought I would mention the following:

Pentium III (Coppermine) 256mb ram - Running Puppy linux capably (though you might have a hard time with wireless)
Pentium 4 (Dothan) 1GB ram - Bodhi running with the speed of new laptop, even plays YouTube videos smoothly
Celeron M , 2GB ram - Lubuntu, smooth and very fast, though you'd want to use Chromium as a browser as Firefox is too slow

So, I may not be adding anything of worth for you, I am just mentioning this because low end hardware will definitely work.  All of these laptops range from 2002 to 2005 and run like they were new.

For what it's worth

Regards

Bob

---

### Post by Rick St. George on 2018-02-25
> **mörgæs said:**
> Your CPU flags are fine (and Buntu installs on even weaker CPU's) but the message indicates that the DVD drive or the DVD itself could have some trouble. 


Thanks! That would explain slow installation, but ... that would not explain computer running slow after installation. I click the mouse, and wait a minute or 2 for that to reflect on the screen, such as a drop down menu or whatever.

I understand the System Requirements are not upto par, but I just installed, using the same disk, Xubuntu v16.04 on an old Dell Dimension 4600 (Pentium 4, 1GB Ram, 80 HDD). 

The computer I'm working on has an AMD Athlon which outperforms the Pentium 4. Same 1GB Ram & 80 HDD.

So ... something is wrong with the hardware ... just can't figure out what? CPU? Memory bus? Seems to run OK in BIOS mode (fast), but once boot to HDD or CD/DVD its slow as molasses.  At this point ... it just doesn't seem worth the time and effort. But willing to give it another try.

Thanks for all the help and ideas.

---

### Post by ajgreeny on 2018-02-25
It's probably worth running **memtest86+** from the grub menu; leave it to run through several instances and check there are no faults or errors reported after a few hours, even overnight if possible.

---

### Post by kurt18947 on 2018-02-25
I have a machine that came with Windows ME - P3-600 mhz 64 MB RAM. I bought used Ebay RAM & maxed it out at 512 MB.  It wouldn't run any version of Ubuntu well. I tried some light distros and settled on Q4OS. I use the machine as a torrent box and it serves quite well in that capacity.

---

### Post by bobnutfield on 2018-02-25
> **kurt18947 said:**
> I have a machine that came with Windows ME - P3-600 mhz 64 MB RAM. I bought used Ebay RAM & maxed it out at 512 MB.  It wouldn't run any version of Ubuntu well. I tried some light distros and settled on Q4OS. I use the machine as a torrent box and it serves quite well in that capacity.

Q4os is very interesting.  I tried it live on a USB stick.  It is designed to look just like Windows 98/XP, but in fact is the old KDE 3 desktop.  It's pretty nice.  Very fast on an old Toshiba laptop and recognizes all of the hardware nicely.  I became interested and inestigated as much as I could, but not much seems to be known about it.  It appears to be a commercial enterprise and I cannot find any forums.  I believe it is maintained by just a small group of developers.  I don't what know kind of future it has but I like it.  I'll keep this USB stick around for a while.  I have an old Pentium III with a 128mb of Ram.  I might just give that a go for fun.

---

### Post by missmoondog on 2018-03-02
> **Rick St. George said:**
> Thanks! That would explain slow installation, but ... that would not explain computer running slow after installation. I click the mouse, and wait a minute or 2 for that to reflect on the screen, such as a drop down menu or whatever.

I understand the System Requirements are not upto par, but I just installed, using the same disk, Xubuntu v16.04 on an old Dell Dimension 4600 (Pentium 4, 1GB Ram, 80 HDD). 

The computer I'm working on has an AMD Athlon which outperforms the Pentium 4. Same 1GB Ram & 80 HDD.

So ... something is wrong with the hardware ... just can't figure out what? CPU? Memory bus? Seems to run OK in BIOS mode (fast), but once boot to HDD or CD/DVD its slow as molasses.  At this point ... it just doesn't seem worth the time and effort. But willing to give it another try.

Thanks for all the help and ideas.

that amd athlon won't even be able to use a modern browser, unless it's a 64bit machine, which i doubt. you would have to use palemoon without the sse2 instruction set as your only choice. i have an old amd athlon +3000 that runs lubuntu 16.04 very well with just 2 gigs of memory and palemoon.

---

### Post by mörgæs on 2018-03-02
> **missmoondog said:**
> You would have to use palemoon without the sse2 instruction set as your only choice.

Please see post 6. SSE2 is present as are all the other important flags. 

Original poster, did you try installing Lubuntu or Bodhi?

---

### Post by droid2bsd88 on 2018-03-02
You might try upgrading you're hdd which I assume is a dinosaur of a PATA or worse yet a Scssi or wide/ultra scssi. while you're at it you should up you're swap partition to 1536mb or 1.5 time physical sdram. Maybe even consider a PC Sata 3rd gen add-on card and either a Sata ssd or conventional hdd.

---

