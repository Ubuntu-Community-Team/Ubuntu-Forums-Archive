---
title: "Swap/kswapd0/[migration] Giving problems after upgrade 12.04 to 14.04.1"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by clams0 on 2014-08-16
Hi, A few day ago I prompted by the update manager **upgrade from 12.04 LTS to 1404.1 LTS**  I decided to upgrade, the process and went without any problems (that I could notice) I reboot all good until I started Firefox after a couple of tabs and some flash based music playing I started to feel the system and playback sluggish, I have this habit of having the task manager open so I quickly check and this process called **[kswapd0] **was using **at least the 10% of the CPU** something I never seen before, I shutdown FF thinking it could be a flash problem after the upgrade, ran the update manager to check for new version or something and when it was in the process of creating the cache for an icon theme I get from a PPA  it hits the 700MB ram (don't know how normal is that) and the **swap just hit 100%**  and makes the entire system slow after minutes I just shutdown, also trying to download files using qbittorrent makes this process called **[migration] use ton of CPU **again something thats never happen before.
Sorry for the bad English, All help  is welcome. Thanks. 

**tl;dr **
After upgrading every time a proccess hit the 500MB ram mark Swap and kswapd0 goes 100% and takes ton of cpu respectively. downloading makes [migration] uses a lot of CPU.

Info: 
Kernel: i686 Linux 3.13.0-34-generic
XUbuntu: 14.04.1 LTS fully updated.
CPU: Pentium Dual-Core CPU T4200 @ 2GHz
RAM: 1GB
Using Xuubntu for nearly 1 year, first upgrade.
Linux/Ubuntu experience: average/newbie.

---

### Post by kansasnoob on 2014-08-16
Post the output of:

```
free -m
```

---

### Post by clams0 on 2014-08-16
```

             total       usado       libre     compart.    búffers     almac.
Mem:           963        899         63        136          8        292
-/+ buffers/cache:        598        365
Intercambio:        982         22        960

```

Hi, Thanks fo the reply, sorry is on Spanish  but am guessing still understandable.

---

### Post by kansasnoob on 2014-08-17
I probably would have made SWAP about 2GB with that low of an amount of RAM but lets look at some other basic hardware and software info:

```
uname -a
```

```
cat /proc/cpuinfo
```

```
lspci | grep VGA
```

```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
```

In case we do decide to increase the size of SWAP let's also see the current drive structure:

```
sudo parted -l
```

> sorry is on Spanish but am guessing still understandable

If we need help with translation we'll ask :D

---

### Post by clams0 on 2014-08-18
> **kansasnoob said:**
> I probably would have made SWAP about 2GB with that low of an amount of RAM but lets look at some other basic hardware and software info:

I don't recall deciding the size of the SWAP Ubuntu must've done that automaticaly, reading on it seems correct

**uname -a**:
```
Linux marcel-Lenovo-3000-N500 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:49:09 UTC 2014 i686 i686 i686 GNU/Linux
```

** cat /proc/cpuinfo**:
```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz
stepping    : 10
microcode    : 0xa07
cpu MHz        : 2000.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dtherm
bogomips    : 3989.83
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz
stepping    : 10
microcode    : 0xa07
cpu MHz        : 1200.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dtherm
bogomips    : 3989.83
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

**lspci | grep VGA**:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

```

**lspci -v -s `lspci | awk '/VGA/{print $1}'**:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 3a02
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f4000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 3
    Kernel driver in use: i915

```

**sudo parted -l**:
```
Modelo: ATA WDC WD1600BEVS-0 (scsi)
Disco /dev/sda: 160GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Numero  Inicio  Fin    Tamaño  Tipo      Sistema de archivos  Banderas
 1      1049kB  159GB  159GB   primary   ext4                 arranque
 2      159GB   160GB  1031MB  extended
 5      159GB   160GB  1031MB  logical


Modelo: Asignador de dispositivos de Linux (crypt) (dm)
Disco /dev/mapper/cryptswap1: 1031MB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. loop

Numero  Inicio  Fin     Tamaño  Sistema de archivos  Banderas
 1      0,00B   1031MB  1031MB  linux-swap(v1)

```

Hopefully everything is correct.


> If we need help with translation we'll ask :D

OK. Thanks for the help. =)

---

### Post by kansasnoob on 2014-08-18
Nothing jumps out at me as being really wrong there. We may want to increase the size of SWAP but please wait and see if others have a better answer.

---

### Post by clams0 on 2014-08-19
Thanks. that's reassuring, I'll hold  then. Thanks for the support.

---

### Post by kansasnoob on 2014-08-19
I wonder if someone else knows how to check for memory leaks?

A long time ago I had trouble with a memory leak ........... didn't even know I had it, or what it was. It's been a very long time ago but if I recall correctly it turned out to be kernel related so I simply reverted to the previous release - think maybe it was Karmic and I reverted to Jaunty.

But back then the interim/normal releases were good for 18 months. Now that they're only good for 9 months LTS is really the only way to go for most production machines.

---

