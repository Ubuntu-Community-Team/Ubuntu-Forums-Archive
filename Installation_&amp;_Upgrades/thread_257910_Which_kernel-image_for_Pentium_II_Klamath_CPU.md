---
title: "Which kernel-image for Pentium II Klamath CPU?"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by SkyNet2029 on 2006-09-15
Ok, so what gives with Kubuntu 6.06 being a total dog on my recently built (by me) machine? 
The previous machine was an old Dell GXMT200 with a whopping 98Mb RAM. It ran faaaast on that machine. (Intel Pentium cpu @ 266Mhx.)

Now, I have acquired a machine from a friend I converted to the Linux way of life, for which he gave me a junked out machine. (parts candidate, mostly). 

On this machine it runs slower than molasses. The livecd on previous machine was tons quicker. 
Here is the output from 
$cat /proc/sysinfo on the newer machine

```
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 3
model name      : Pentium II (Klamath)
stepping        : 4
cpu MHz         : 266.692
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov mmx
bogomips        : 533.90

```

The output from 
$cat /proc/meminfo:

```
root@ubuntu:~# cat /proc/meminfo
MemTotal:       386336 kB
MemFree:          4288 kB
Buffers:         42724 kB
Cached:         216564 kB
SwapCached:          0 kB
Active:         152928 kB
Inactive:       193504 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       386336 kB
LowFree:          4288 kB
SwapTotal:      610460 kB
SwapFree:       610460 kB
Dirty:               0 kB
Writeback:           0 kB
Mapped:         132056 kB
Slab:            29500 kB
CommitLimit:    803628 kB
Committed_AS:   342380 kB
PageTables:       1596 kB
VmallocTotal:   638968 kB
VmallocUsed:      3692 kB
VmallocChunk:   634804 kB

```

So, I know I have enough memory available, the only noticeable difference is in the cpu architecture itself:

Old machine had a Pentium w/MMX @ 200Mhz, OC'd to 266Mhz. No problems at all and was reasonably quick.

New machine has an Pentium II @ 266Mhz, NO OC'ing. I did try to change to the 686 kernel, but the results were the same.

Is there a specific kernel I should use for a Pentium II (KLAMATH MODEL) to get things working the right way? Or am I just looking at the correct solution and applying the incorrect theorem???
As this was a 'gift' from a friend, I would love to get it working. BTW... Windows Server Enterprise flies on this machine, so I know its not the actual machine settings. (In windows at least, which is usually 4-5 times slower on execution than Kubuntu/Ubuntu. (Yes , I have tried both..although they both load up with a default 386 Kernel. In expert mode, there does not seem to be an option to install with 686 kernel on either (K/Ubuntu).
Maybe there is a guru in here who can steer me in the proper direction? As I abhor windows as it is just paying the man for what should (and is ) be readily available free...I want my Kubuntu back!
Any and all help is greatly appreciated.

---

