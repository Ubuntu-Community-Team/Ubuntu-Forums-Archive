---
title: "CPU lacks cmov - so lubuntu 10.10 install CD won't boot"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by alpage2 on 2010-10-13
I have lubuntu 10.04 running nicely on an old laptop with an AMD-K6 400MHz CPU & 192Mb RAM.

When I boot it from a lubuntu 10.10 install CD, the initial boot menu appears, but when I click on the install option, it displays an error message informing me that the kernel is unable to boot because it requires a CPU that supports cmov.

I have not encountered this problem before - any help would be much appreciated.

Thanks in anticipation
Alan

---

### Post by 8oluf7 on 2010-10-20
I had the same problem with an IBM Thinkpad i1400. 

I wandered through the descriptions of Pentium processors in Wikipedia until I found a reference to CMOV. It stands for 'Conditional Move' and was added for the Pentium Pro (and later) variants. It is characterised somewhere in the pages I trawled through as one of the changes that make a processor a 'true 686'. 

The i1400 has a Pentium MMX, which doesn't include this instruction. I also have a Thinkpad 570 which has processor that's only slightly faster, but it's a Pentium II Mobile - which can cope with CMOV. 

I guess someone set/forgot to set a switch when compiling the kernel for the 10.10 CD and it's ended up as '686 only'.

If you want to check whether your processor supports CMOV in Lubuntu go to:

System Tools > System Profiler ...

Click on Processor (under Devices) in the left column and scroll down the right column to view the 'Capabilities'. CMOV will be there if it's supported (BTW, these 'Capabilities' are not listed in alphabetical order, so you need to check the whole list.)

Not a solution - but an explanation.

Mike G.

---

### Post by alpage2 on 2010-10-20
Hello Mike

Many thanks for the explanation - as you say, it's not a solution, but it does clear up the mystery. I followed your directions and obtained the following details of my CPU:

//
-Processor-
Name		: AMD-K6(tm) 3D processor
Family, model, stepping		: 5, 8, 12 (AMD K6-2)
Vendor		: AuthenticAMD
-Configuration-
Cache Size		: 64kb
Frequency		: 400.94MHz
BogoMIPS		: 801.87
Byte Order		: Little Endian
-Features-
FDIV Bug		: no
HLT Bug		: no
F00F Bug		: no
Coma Bug		: no
Has FPU		: yes
-Cache-
Cache information not available
-Capabilities-
fpu		: Floating Point Unit
vme		: Virtual 86 Mode Extension
de		: Debug Extensions - I/O breakpoints
pse		: Page Size Extensions (4MB pages)
tsc		: Time Stamp Counter and RDTSC instruction
msr		: Model Specific Registers
cx8		: CMPXCHG8 instruction
pge		: Page Global Enable
mmx		: MMX technology
syscall		: SYSCALL and SYSEXIT instructions
3dnow		: 3DNow! Technology
k6_mtrr		: AMD K6 nonstandard MTRRs
up		: smp kernel running on up
//

So it would seem that the CPU does not support cmov.

I am keeping my fingers crossed that the problem is cleared up in ver. 11.04  ;-)

Thanks again
Alan

---

### Post by brmiller on 2010-10-26
> **alpage2 said:**
> 
So it would seem that the CPU does not support cmov.

I am keeping my fingers crossed that the problem is cleared up in ver. 11.04  ;-)


Not likely.  See the [[COLOR="Blue"]Maverick Meerkat Release Notes[/COLOR]]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Linux%20kernel%202.6.35")

---

### Post by alpage2 on 2010-10-26
Thanks for the link - yes - the developers have dropped support for i586 and for i686 processors that lack cmov support.

Sad news indeed. I can continue to use 10.04 while it is supported, but after that ... puppy linux, perhaps :(

---

### Post by efflandt on 2010-10-26
I have an old K6-2/400 desktop I had not used for years, and had taken most of the PC100 RAM from it for a PIII 550 that I set up with Qimo for kids (based on Ubuntu) for my nieces kids.

But at our office we are supposed to use a squid proxy at our factory through a VPN and after our factory network was down for a day, I installed IPCop on the K6-2/400 w/128 MB RAM as a backup squid proxy, and it works fine for that (only using 30 watts headless).  So if you have a couple of PC Card (cardbus) nics, that old laptop could make someone a nice configurable firewall/router (web config interface).  IPCop uses a 2.4 kernel.

---

### Post by alpage2 on 2010-10-27
Thanks efflandt

Nice to know there are other options :)

Regards
Alan

---

### Post by alexei.colin on 2010-11-02
Just for information that somebody might stumble on. The dropped i586 support in Maverick can manifest in a failed update from 10.04 to 10.10. The point of failure is the first package that requires ldconfig after libc-bin_2.12.1-0ubuntu8_i386 gets installed: since ldconfig in that version of libc-bin has unsupported cmov instructions. E.g. in my case:
```
Preparing to replace libc6 2.11.1-0ubuntu7.5 (using .../libc6_2.12.1-0ubuntu8_i386.deb) ...
Checking for services that may need to be restarted...
Checking init scripts...
Illegal instruction
Unpacking replacement libc6 ...
dpkg: warning: old post-removal script killed by signal (Illegal instruction)
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/libc6_2.12.1-0ubuntu8_i386.deb (--unpack):
 subprocess new post-removal script killed by signal (Illegal instruction)

```

> Sad news indeed. I can continue to use 10.04 while it is supported, but after that ... puppy linux, perhaps 

Yeah, sadly, but probably will need to explore another distribution after LTS expires... =(

---

