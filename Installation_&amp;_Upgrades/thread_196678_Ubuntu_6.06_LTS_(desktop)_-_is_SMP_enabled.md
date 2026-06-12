---
title: "Ubuntu 6.06 LTS (desktop) - is SMP enabled?"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2006-06-14
I installed Ubuntu 6.06 LTS (desktop) on my Lenovo 3000 N100 laptop only yesterday and I must admit that I am very impressed with the result. Basically, there is not reason for me to ever return to Windows XP, despite the fact that I kept it in a dual-boot options (I already paid for it, why not keep it?).

However, some aspects in the system seem more sluggish than in Windows XP - and I was wondering - perhaps my Ubuntu installation has not recognized the fact that I actually have two (2) processors in my laptop, not one? (it is an Intel Core Duo)

If so, what do I need to do enable it on my system? I hope I don't need to re-install everything from scratch...

And is there a way that can tell me whether my Ubuntu is running in dual processor mode?

Thanks!
Alex

---

### Post by mips on 2006-06-14
SMP is not enabled by default. You need to install a SMP kernel via Synaptic/Apt-get/Adept.

---

### Post by 5-HT on 2006-06-14
SMP support is enabled in all of Dapper's kernels except the stock i386 kernel that is installed by default if you used an x86 install CD.

For an intel core-duo, you'll need to install the i686 kernel to take advantage of both cores.

To install the latest kernel with the restricted modules (wireless/proprietary video drivers/other):

```
 sudo apt-get install linux-686 
``` 
To see if both cores are being recognized, there should be mention of them in /proc/cpuinfo.

```
 cat /proc/cpuinfo 
``` 

Have fun with Ubuntu!

---

### Post by xp_newbie on 2006-06-14
Amazing guys, you are simply amazing in how quickly you respond. I know I arrived to the ultimate Linux distribution.  :)

Here is the output of my cat /proc/cpuinfo:
> 
[SIZE=1] processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1662.727
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor vmx est tm2 xtpr
bogomips        : 3328.56[/SIZE]
 
This means my Ubuntu installation recognizes only one CPU, right?

I am now proceeding to do the upgrade...

Thanks,
Alex

---

### Post by xp_newbie on 2006-06-14
OK - I just got into Synaptic, did a search on '686' and discovered quite a few packages matching this criterion. Among those there are two packages that seem to answer your description:

1. linux-686
2. linux-686-smp

Which one do I choose?

Or does it matter?

I know you suggested using the command line apt-get, but at the moment I am on training wheels so I am interested in understanding what I am doing.

Thanks!
Alex

---

### Post by 5-HT on 2006-06-14
[quote=xp_newbie]Amazing guys, you are simply amazing in how quickly you respond. I know I arrived to the ultimate Linux distribution.  :)

Here is the output of my cat /proc/cpuinfo:
 
This means my Ubuntu installation recognizes only one CPU, right?

I am now proceeding to do the upgrade...

Thanks,
Alex[/quote] 
Yup, only one of the cores is currently being recognized.
After you install linux-686, y[SIZE=2]ou should se[/SIZE]e two entries wit[SIZE=2]h "[/SIZE][SIZE=1][SIZE=2]T2300  @ 1.66GHz".

Glad to have helped, if you have any problems just reply back.

EDIT:
[/SIZE][/SIZE][quote=xp newbie]1. linux-686
2. linux-686-smp

Which one do I choose?

Or does it matter?[/quote][SIZE=1][SIZE=2]

It doesn't matter as linux-686-smp just points to linux-686.
In previous releases of Ubuntu you had to install the linux-686-smp package if you wanted  the 686 kernel with smp support. 
In Dapper, however, the linux-686 package has smp support enabled for the regular 686 kernel.
[/SIZE]
[/SIZE]

---

### Post by xp_newbie on 2006-06-14
Thank you so much! I just finished updating to the SMP kernel and boy I must tell you - I have never seen anything easy like this. Not even Windows XP, which requires  lots of reboots on updating even applications (like Adobe Acrobat Reader). This is the easiest OS to install/update/maintain I have ever seen.

using cat /proc/cpuinfo I can now see two CPUs. This is great. 

Ubuntu rocks!

Alex

---

### Post by robertfranz on 2006-07-20
Wow. I didn't realize it was this easy.

Like most folks, I installed the 386 Desktop distro.
Also like most folks doing new installs, it sucked *** until I got a 686 smp kernel.

Unfortunately, I didn't read this post first, or I would not have gone through the process of following a HowTo for compiling an smp kernel - especially since the first update caused the root fs to no longer mount...

Hours gone - well, a few minutes then waiting hours for the kernel to compile on this ancient beast - instead of a few minutes.

This really should be a sticky - and the folks putting together the releases should note that smp kernels are required more now than ever before and put an smp kernel in all versions.

---

