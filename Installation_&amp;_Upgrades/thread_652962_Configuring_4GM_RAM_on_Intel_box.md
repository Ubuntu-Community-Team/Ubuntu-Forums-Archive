---
title: "Configuring 4GM RAM on Intel box"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by brm on 2007-12-29
When I ordered my brand-new super-quiet Intel box with 4GB of RAM, I knew that there were issues with the 4GB limit of 32-bit OSes. Little did I expect that a couple of hours Googling and reading would leave me completely befuddled.

Before I spend more hours testing endlessly, I would appreciate input on the best compromise in the "real world". BTW, I am highly comfortable with Kubuntu Gutsy Gibbon; I will install it first. There is lots of space available to try other distros later.

Some sources say that the CONFIG_HIGHMEM4G configuration works for installations up to and including 4 GB RAM. Others say that one must use a PAE kernel (CONFIG_HIGHMEM64G) for installations of 4GB and up. My reading suggests that he latter group appears to be correct: If the first 32Kb of memory is reserved for PCI assignments, 4GB does not fit into (4G minus 32K).

dmesg recognizes all 4GB but recommends the PAE kernel:
```
[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a PAE enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.

```
cat /proc/meminfo tells a different story:
```
MemTotal:      3369808 kB
MemFree:       2816504 kB
Buffers:         81396 kB
Cached:         342620 kB
SwapCached:          0 kB
Active:         210868 kB
Inactive:       285996 kB
HighTotal:     2489856 kB
HighFree:      2068024 kB
LowTotal:       879952 kB
LowFree:        748480 kB
SwapTotal:           0 kB
SwapFree:            0 kB
```

P.S. Because this is a "just home from the store" system running off a LiveCD, the hard disks are not yet partitioned and there is no swap space. I will correct this during the OS install.

Q. Some sources state that enabling PAE in the kernel leaves a significant performance hit. All these sources are two years old or more. Is this problem inherent or has it been worked around? How significant is the hit? Since the default Ubuntu kernel on the LiveCD acknowledges ~3.3 GB of RAM, should I consider "leaving alone"?

Q. A posting by Falko Timme on howtoforge.com from mid-December 2007 states that there is a bug in the GRUB implementation on Debian Etch which prevents the system from recognizing more than ~3.3 GB RAM. (The exact figure on his 6GB system was a little higher than on my 4GB system.) He offers a patch and recommends recompiling GRUB. Does anyone know if the version of GRUB in Ku/Ubuntu 7.10 Gutsy Gibbon contains the same bug?

Thanks in advance for advice on these questions.

---

### Post by icheyne on 2007-12-29
I can't help you with your question, but why don't you go 64 bit?

---

### Post by brm on 2007-12-29
Does the Intel Core 2 Duo E2160 support 64bit operating systems?

---

### Post by PmDematagoda on 2007-12-29
Yes it most definitely does, if you do not use 64 bit, you may not be able to use all 4Gb of your RAM on 32 bit, unless you compile a kernel with support for 4Gb of RAM.

---

### Post by brm on 2007-12-29
> **PmDematagoda said:**
> Yes it most definitely does, if you do not use 64 bit, you may not be able to use all 4Gb of your RAM on 32 bit, unless you compile a kernel with support for 4Gb of RAM.

Forgive me for dotting Is and crossing Ts but just to be perfectly clear: although the Ku/Ubuntu 64bit version is labelled "amd64", it will work with my Intel chip ????

---

### Post by PmDematagoda on 2007-12-29
Yes it will, I use the AMD64 version on my Intel and it works:). The fact that the ISO is called AMD64, not AMD64 & EM64T is not only because it simply would be too long;), but they both (AMD64 and EM64T) mean pretty much the same thing, you can find quite a lot of information concerning this if you google it a bit:).

---

