---
title: "i lost my kernel file =("
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by pdro7 on 2010-03-22
hi every one, after and upgrade process my system crashed, i tried to use the recovery option on the grub options, but i dont know what it did, because i LOST MY KERNEL FILES, after that i just had memtest options in that menu. I have trid to install a new kernel image, i used a live cd, i mounted my file system and use chroot, apt-get install newimage, everything seen ok , but when i restart the computer , even if i have a new option on grub menu, when i press enter,the systemn crash again. What do i miss? I put below some info about my system, or what other option i have to recovery it? 

root@ubuntu:/home/ubuntu#** fdisk -l**

Disco /dev/sda: 82.0 GB, 81964302336 bytes
255 cabezas, 63 sectores/pista, 9964 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x8c958c95

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        2569    20635461    7  HPFS/NTFS
/dev/sda2            2570        8435    47118645    7  HPFS/NTFS
/dev/sda3            8436        9964    12281692+   f  W95 Ext'd (LBA)
/dev/sda5            8436        8682     1983996    7  HPFS/NTFS
**/dev/sda6            8683        9903     9807651   83  Linux**
/dev/sda7            9904        9964      489951   82  Linux swap / Solaris


root@ubuntu:/home/ubuntu# **cat /proc/cpuinfo **
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping    : 1
cpu MHz        : 3006.890
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips    : 6013.78
clflush size    : 64
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping    : 1
cpu MHz        : 3006.890
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips    : 6014.49
clflush size    : 64
power management:

---

### Post by phillw on 2010-03-22
Hi and welcome to the forums,

with the help of others on the forum I put together a little "How To" for people who have been a little over-eager in tidying up their kernels ;)

You'll find it over here --> [http://forum.phillw.net/viewtopic.php?f=4&t=35](http://forum.phillw.net/viewtopic.php?f=4&t=35)

You'll be using sda6

Regards,

Phill.

---

