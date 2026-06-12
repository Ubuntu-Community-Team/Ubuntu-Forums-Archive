---
title: "64bit OS Does Not See All RAM"
date: 2015-06-07
forum: MINT
---

### Post by borgward on 2015-06-07
Installed LinuxMint 17 64bit ver2 on Dell Optiplex 210L.  64bit P4, Hyperthreading enabled = running in 64bit mode. New Crucial 4 GB RAM (2 - 2GB sticks), Onboard video - Video Memory Size Is set at 8 MB. I only have 3 GB RAM available. Setup sees 4 GB of RAM. Since I am running 64 bit OS all of the RAM should be available. Is there something about the 64 bit P4 that is causing this problem? What else could be using all that RAM?

---

### Post by oldfred on 2015-06-07
Moved to Mint.

Post the following. 
 cat /proc/cpuinfo
cat /proc/meminfo
egrep "model name|address" /proc/cpuinfo 

 uname -a
      cat /etc/*release

Not sure if all those work in Mint or not?

---

### Post by borgward on 2015-06-07
> **oldfred said:**
> Moved to Mint.

Post the following. 
 cat /proc/cpuinfo

$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping	: 9
microcode	: 0x3
cpu MHz		: 2992.563
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips	: 5985.12
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping	: 9
microcode	: 0x3
cpu MHz		: 2992.563
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips	: 5985.12
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:


> **oldfred said:**
> cat /proc/meminfo

$ cat /proc/meminfo
MemTotal:        3071852 kB
MemFree:         1781128 kB
Buffers:           50152 kB
Cached:           530220 kB
SwapCached:            0 kB
Active:           734852 kB
Inactive:         461068 kB
Active(anon):     616424 kB
Inactive(anon):    87672 kB
Active(file):     118428 kB
Inactive(file):   373396 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       4876284 kB
SwapFree:        4876284 kB
Dirty:               264 kB
Writeback:             0 kB
AnonPages:        615540 kB
Mapped:           113656 kB
Shmem:             88556 kB
Slab:              41624 kB
SReclaimable:      24600 kB
SUnreclaim:        17024 kB
KernelStack:        2816 kB
PageTables:        16592 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     6412208 kB
Committed_AS:    2160812 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      544412 kB
VmallocChunk:   34359186436 kB
HardwareCorrupted:     0 kB
AnonHugePages:     71680 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       41504 kB
DirectMap2M:     3094528 kB

> **oldfred said:**
> egrep "model name|address" /proc/cpuinfo 

$ egrep "model name|address" /proc/cpuinfo 
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
address sizes	: 36 bits physical, 48 bits virtual
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
address sizes	: 36 bits physical, 48 bits virtual

> **oldfred said:**
> uname -a

$ uname -a
Linux user-OptiPlex-210L 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

> **oldfred said:**
> cat /etc/*release

$ cat /etc/*release
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=17
DISTRIB_CODENAME=qiana
DISTRIB_DESCRIPTION="Linux Mint 17 Qiana"
NAME="Ubuntu"
VERSION="14.04, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
cat: /etc/upstream-release: Is a directory

> **oldfred said:**
> Not sure if all those work in Mint or not?

They did.

---

### Post by oldfred on 2015-06-07
It is only showing the 3GB of RAM.

There was some issues on early versions with PAE, but that was so the 32 bit version could partially use more than the 3GB.
Does BIOS show all 4GB? Some motherboard/BIOS may not support that much RAM.

This should show each bank.
 sudo lshw | grep -m 1 -A 25 "*-memory"

If one is 1GB not 2GB then either it is not working or your motherboard does not support the full 64GB.
The other test would be to try each DIMM and see that each shows 2GB, so you know each is ok.

---

### Post by borgward on 2015-06-07
> **oldfred said:**
> It is only showing the 3GB of RAM.

Yes. Both Sysinfo and System Monitor show only 3GB. 
$ free
             total       used       free     shared    buffers     cached
Mem:       3071852    1630948    1440904     129244      53328     762076
-/+ buffers/cache:     815544    2256308
Swap:      4876284          0    4876284

> **oldfred said:**
> There was some issues on early versions with PAE, but that was so the 32 bit version could partially use more than the 3GB.
Does BIOS show all 4GB? Some motherboard/BIOS may not support that much RAM.

Yes the BIOS does show 4GB

> **oldfred said:**
> This should show each bank.
 sudo lshw | grep -m 1 -A 25 "*-memory"

 sudo lshw | grep -m 1 -A 25 "*-memory"

$ sudo lshw | grep -m 1 -A 25 "*-memory"
[sudo] password for user: 
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: FFFFFFFFFFFFFFFF
             physical id: 0
             serial: FFFFFFFF
             slot: DIMM_1
             size: 2GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: CT25664AA667.M16FM
             vendor: 7F7F7F7F7F9B0000
             physical id: 1
             serial: 00000000
             slot: DIMM_2
             size: 2GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge

> **oldfred said:**
> If one is 1GB not 2GB then either it is not working or your motherboard does not support the full 64GB.
The other test would be to try each DIMM and see that each shows 2GB, so you know each is ok.

---

### Post by oldfred on 2015-06-07
That says you have 4GB and it sees it correctly as two 2GB banks.

Does this also show 3GB?
free
I know somethings Video uses some RAM, but not 1GB.
So not sure why different results from different tools. Hopefully someone else with your older Pentium knows.

---

### Post by borgward on 2015-06-07
$ free
             total       used       free     shared    buffers     cached
Mem:       3071852    1630948    1440904     129244      53328     762076
-/+ buffers/cache:     815544    2256308
Swap:      4876284          0    4876284

---

### Post by CharlesA on 2015-06-07
The BIOS is probably reserving 1GB for video even though it's only set at 8MB. I ran into similar issues with an older laptop - 2 GB was installed, but it only saw 1GB as usable. Kinda strange, but it seems to happen to both Windows and Linux.

---

### Post by MikeMecanic on 2015-06-08
Try all the terminal commands shown above and ain't have anything wrong.  What do you see under System Info?  Running this version of Cinnamon Rebecca Romeo
```
cinnamon --version
Cinnamon 2.6.7

```

If you get 4Gig of RAM in System Info, then go for a second installation: It takes 5 minutes.  Me it's in System Info (About This Computer under Ubuntu) that I  had problems in the pass and a second installation fix those problems usually.
Menu / Preferences / System Info
[http://media-opensource.blogspot.ca/2015/05/cinnamon-263-is-released-you-can.html](http://media-opensource.blogspot.ca/2015/05/cinnamon-263-is-released-you-can.html)


All the best,

---

### Post by borgward on 2015-06-09
> **MikeMecanic said:**
> Try all the terminal commands shown above and ain't have anything wrong.  What do you see under System Info?  Running this version of Cinnamon Rebecca Romeo
```
cinnamon --version
Cinnamon 2.6.7

```

If you get 4Gig of RAM in System Info, then go for a second installation: It takes 5 minutes.  Me it's in System Info (About This Computer under Ubuntu) that I  had problems in the pass and a second installation fix those problems usually.
Menu / Preferences / System Info
[http://media-opensource.blogspot.ca/2015/05/cinnamon-263-is-released-you-can.html](http://media-opensource.blogspot.ca/2015/05/cinnamon-263-is-released-you-can.html)


All the best,

$ cinnamon --version
Cinnamon 2.2.16

System Info shows 2999 MB

The problem is the chipset. It does not provide for memory remapping. The Chipset on the 210L is Intel 915GV. Data Bus Width is 64bit. Address Bus Width is 32 bit. Some of the Intel chipsets have option to allow the OS to see all of the RAM. Funny, this chipset has maximum memory size of 8 GB, but the OS can only use 3GB.

---

### Post by CharlesA on 2015-06-09
> **borgward said:**
> $ cinnamon --version
Cinnamon 2.2.16

System Info shows 2999 MB

The problem is the chipset. It does not provide for memory remapping. The Chipset on the 210L is Intel 915GV. Data Bus Width is 64bit. Address Bus Width is 32 bit. Some of the Intel chipsets have option to allow the OS to see all of the RAM. Funny, this chipset has maximum memory size of 8 GB, but the OS can only use 3GB.

Yeah, definitely the chipset. I ran into an issue like that when I went to build a small Atom-based box for an HTPC. Had 4GB installed, but it only saw 3. Reached out to support and they said it was a chipset limitation. BIOS showed 4GB too. Ugh!

---

### Post by MikeMecanic on 2015-06-09
> [COLOR=#000000]System Info shows 2999 MB[/COLOR]
_This is not a good news_.  What you see under System Info is a carbon copy of your Mother Board.  The only thing left is to get yourself a flash drive (usb stick) of Windows 8.1 and install on the Intel web site the** Intel Driver Update Utility**: Update your chip-set.  It work for me for the BIOS a couple of mouths ago and for my Intel Graphics under Win 10 two weeks ago (not the chip-set but an update was available for 8.1).  Never know?

[https://downloadcenter.intel.com]("https://downloadcenter.intel.com/")

I guess that CharlesA is not aside...
.
All the best,

---

