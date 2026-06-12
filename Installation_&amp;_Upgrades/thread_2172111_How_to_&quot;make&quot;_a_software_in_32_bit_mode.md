---
title: "How to &quot;make&quot; a software in 32 bit mode"
date: 2013-09-03
forum: Installation &amp; Upgrades
---

### Post by malakar.subhendu on 2013-09-03
I have to work with a software which needs an x86 architecture to work upon. But my machine is x64 and ubuntu installed is amd64 one. How can i 'make' it in 32 bit mode.

---

### Post by leg on 2013-09-03
Create a 32 bit environment to work on in a virtual environment.

---

### Post by grahammechanical on 2013-09-03
Your CPU and both Windows 7 and Ubuntu 12.04, they are all x86 architecture. CPUs made by both Intel and AMD run the Intel x86 instruction codes and this is the same whether the CPU is 32 bit or 64 bit. The difference between 32 bit CPUs and 64 bit CPUs is that 32 bit CPUs cannot run 64 bit applications including 64 bit operating systems. Whereas, a 64 bit CPU can run a 32 bit application including a 32 bit OS.

When IBM made the first Personal Computer it used the Intel 8086 CPU. This was an 8 bit CPU. Over the years Intel expanded its x86 CPU instruction set, releasing CPUs that used the expanded instruction set - 80186, 80286, 80386, 80486 and then it switched to names such as the Pentium 5. Meanwhile other Chip makers produced CPUs that ran intel x86 compatible instruction code. AMD was one of these. These later CPUs run 32 bit code. So, the 32 bit Linux kernel is called i386, After the Intel 80386 CPU.

AMD was the first chip maker to produce a CPU that ran 64 bit instructions that was compatible with the Intel 64 bit instruction set. Intel was slow producing a CPU capable of running 64 bit code mainly because Microsoft was in no hurry to bring out a 64 bit version of Windows. So, the 64 bit Linux kernel is called AMD64, after AMD and its 64bit CPU.

AMD64 will run on both Intel and AMD CPUs whether 32 bit or 64bit. Whereas, i386 will run on Intel and AMD CPUs but only if they are 32bit.

I no nothing about compling software.

Regards.

---

### Post by malakar.subhendu on 2013-09-04
@leg: are you pointing to virtualbox? I want to install the software in the original one.
@grahammechanical: thanks for the info.

---

### Post by leg on 2013-09-04
> **malakar.subhendu said:**
> @leg: are you pointing to virtualbox? I want to install the software in the original one.
Not specifically no I was thinking of emulation in the same way as you emulate an environment for Android development. Android is a different environment to the desktop (usually). You want to develop for a different environment than the one you are on so you need to be able to compile for that environment. One way to do that is to be in the correct environment in the first place and this is where emulation can help. You may be able to just use a compiler switch to make a 32 bit executable.

---

### Post by markbl on 2013-09-05
Just add "-m32" to CFLAGS for gcc.

---

### Post by malakar.subhendu on 2013-09-09
> **markbl said:**
> Just add "-m32" to CFLAGS for gcc.
Not working

---

### Post by markbl on 2013-09-09
> **malakar.subhendu said:**
> Not working
Without detail you can't get any help.

---

