---
title: "Change from 32 -&gt; 64 bit on 10.04"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by joakim.hove on 2010-05-08
Hello,

I have a server now running the 10.04 version of Ubuntu. It has a 32 bit kernel, however server hardware itself is 64 bit[*] - so I wanted to "upgrade" to a 64 operating system. Can that be easily done?

[*]: Actually I am not 100% certain about the hardware either, this is what I get from /proc/cpuinfo:


  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc 
  arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
  bogomips	: 4799.90
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual

Have read on the net that the 'lm' under flags indicates 64 bit hardware? [I do not have physical access to the server in question, not even details about make.]

Any tips?

Joakim

---

### Post by lemming465 on 2010-05-09
You have "lm" (long mode) in your cpuinfo flags, so yes, that CPU should be 64-bit capable.

Unfortunately, I'm not aware of any generally accepted method for converting an existing install to a different instruction set; the standard advice for going between 32-bits and 64-bits is to reinstall.  Depending on your disk layout, use of non-repository software, and comfort level with "dpkg --get-selections" this might not be particularly traumatic.

---

