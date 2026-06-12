---
title: "Spec for Gutsy (Feisty is OK) on VIA EPIA CL"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by owen_pg on 2007-10-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/152257](https://bugs.launchpad.net/ubuntu/+bug/152257) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

I wiped my (working) Feisty kubuntu partition to try and install the RC of kubuntu  (kubuntu-7.10-rc-desktop-i386.iso).

This is the CD boot loader we're talking about here not kubuntu itself loading. It didn't get very far, here's what happens:

I insert "Kubuntu 7.10 i38" CD into Via EPIA PC.

Power On PC:

. . . BIOS / Memory blah things . . .

PCI device listing . . .
. . . blah . . .

Verifying DMI Pool Data . . . . . . . . . . .
. . . blah . . .

Boot from CD :
ISOLINUX 3.36 Debian-2007-08-30 Copyright (C) 1994-2007 H. Peter Anvin
Loading . . . _



Now I can't find the minimum specs for the Gutsy install but I think it's a 686 processor.  My Via EPIA CL has a Via C3 processor and I found this snippet somewhere:

"The Via C3 is a 686. Unfortunately, the actual specs for 686 make CMOV an optional instruction, and you're supposed to test for the CMOV flag before using it.  Needless to say, C compilers generate CMOV when told to compile for 686."

Does anybody have a clue if this could be why the Live CD install never gets going?
Suggestions?
 :confused:

The bug report is here:
[https://bugs.launchpad.net/ubuntu/+bug/152257](https://bugs.launchpad.net/ubuntu/+bug/152257)

Thanks in anticipation.

Owen

---

### Post by lyalc on 2007-10-20
Maybe related
EPIA M10000 motherboard.
I get a Panic, CPU too old message on 7.10 serevr and desktop.
ok on 7.04 9 - ( I'm running it right now!)

cat /proc/cpuinfo 
processor       : 0
vendor_id       : CentaurHauls
cpu family      : 6
model           : 9
model name      : VIA Nehemiah
stepping        : 8
cpu MHz         : 1002.304
cache size      : 64 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr cx8 sep mtrr pge cmov pat mmx fxsr sse up rng rng_en ace ace_en
bogomips        : 2006.86
clflush size    : 32


Lyalc

---

### Post by nu2lnx on 2007-11-13
Any progress on this?  I currently have Fedora running on the Nehemiah and was thinking of switching it to Ubuntu so my laptop and desktop were in the same flavor category....  Just put the brakes on that after discovering this post...

From what I am understanding - Feisty is ok?  How does Feisty run, and what are the specs of the machine running the Nehemiah?

Thanks!

---

